## ActivityPub

_“Future standards — including vocabularies for social applications, activity streams, embedded experiences and in-context actions, and protocols to federate social information such as status updates — will address use cases that range from social business applications, to cross-organization federation, to greater user control over personal data” — [Launch press release][1] of the W3C Social Web Working Group_

Between 2014 and 2018, the W3C Social Web Working Group coordinated work drafting several different potential web standards. It was a broad charter, covering both IndieWeb-friendly formats like Micropub and Webmention, as well as some of the formats that would form the foundation of Mastodon.

### WebFinger

WebFinger is used in Mastodon, though it’s not strictly part of ActivityPub itself. With users spread out across multiple Mastodon instances, there needed to be a way to look up a user on another instance. WebFinger was used in earlier federated networks like StatusNet and Diaspora, and it is also used in Mastodon.

Remember that Mastodon usernames look like email addresses. WebFinger was designed to accommodate email addresses. From the [WebFinger specification][2]:

> WebFinger discovers information for a URI that might not be usable as a locator otherwise, such as account or email URIs.

In many IndieWeb protocols, to query information you often first look for `link` tags in the HTML for a user's blog. For example, `rel="micropub"` would point to the Micropub API endpoint for posting, which could live on a different server. WebFinger is not like that. With WebFinger, there is a standard URL under the path `/.well-known` that is provided by every Mastodon instance.

To look up a user with WebFinger, you construct a `resource` parameter with an `acct:` URI that includes the Mastodon username. The `:` and `@` characters will need to be encoded.

	GET /.well-known/webfinger?resource=acct:manton@mastodon.social
	Host: mastodon.social

There is no centralized directory of Mastodon usernames. This request should be sent to the hostname used in the Mastodon username.

So for a username like `manton@mastodon.social`, you should make a WebFinger request to "mastodon.social". For `aaronpk@aaronparecki.com`, it would be a connection to "aaronparecki.com". (Most Mastodon users share an instance with other users, but some people run a single-user instance with their own domain name.)

The response is JSON, including data such as the URI for the account and links to the user's profile page and ActivityPub endpoint. A portion of the JSON looks like this:

	{
	  "links": [
	{
	  "href": "https://mastodon.social/@manton", 
	  "type": "text/html", 
	  "rel": "http://webfinger.net/rel/profile-page"
	}, 
	{
	  "href": "https://mastodon.social/users/manton", 
	  "type": "application/activity+json", 
	  "rel": "self"
	}
	  ], 
	  "subject": "acct:manton@mastodon.social"
	}

The most important field is the link where the value of `rel` is "self". This is the ActivityPub "actor" URL, a unique identifier for referring to this user account.

### HTTP signatures

In addition to WebFinger for username lookups, another underspecified aspect of ActivityPub that Mastodon filled in was signing HTTP requests. In fact, there is no mention of this at all in the ActivityPub spec. The authors of the spec knew more work would need to be done here, so they published [a separate W3C best practices report][3] with a loose proposal for how to take the next step:

> Server to server federation is authenticated using HTTP Signatures in conjunction with the signing key from the actor's publicKey field. The keyId should link to the actor so that the publicKey field can be retrieved. At minimum, the digest field should be included in the set of headers being signed.

HTTP signatures effectively add new required HTTP headers to verify if the request is arriving as it appears to be, not intercepted and modified in transit. It combines the date, request path, and other fields, cryptographically signing it so that it can be verified on the other side.

Mastodon requires HTTP signatures for any POSTs to the inbox. Additionally, Mastodon can optionally be configured to require HTTP signatures for all requests, even just looking up the user’s profile.

### The inbox

Most requests in Mastodon are sent to a user’s inbox. This is an endpoint that receives follow requests, new posts from other users you might be following, and even notifications when a post is removed, so that an instance can update its own copy of posts and user accounts.

To discover the inbox and other URLs for a user, we query the actor URL found from WebFinger:

	GET /users/manton
	Host: mastodon.social
	Accept: application/activity+json

Mastodon uses HTTP content negotiation. The “Accept” header needs to be sent to indicate what kind of response you want to receive. It is usually set to “application/activity+json” (ActivityPub and ActivityStreams) or “application/ld+json” (JSON LD).

Mastodon instances and other platforms that implement ActivityPub will need to store data about the user. Requests to the inbox are signed, and the public key fields can be used to verify requests.

The full profile response from Mastodon is quite long. Here’s a partial response of the key JSON fields:

	{
	  "preferredUsername": "manton", 
	  "inbox": "https://mastodon.social/users/manton/inbox", 
	  "id": "https://mastodon.social/users/manton", 
	  "followers": "https://mastodon.social/users/manton/followers", 
	  "type": "Person", 
	  "publicKey": {
		...
	  }, 
	  "outbox": "https://mastodon.social/users/manton/outbox", 
	  "icon": {
	    "url": "https://files.mastodon.social/accounts/avatars/000/019/818/original/85d071e6a7864589.jpg", 
	    "type": "Image", 
	    "mediaType": "image/jpeg"
	  }, 
	  "name": "Manton Reece", 
	  "url": "https://mastodon.social/@manton"
	}

To send a new blog post to a user’s inbox, send an HTTP POST:

	POST /users/manton/inbox
	Host: mastodon.social
	Content-Type: application/activity+json
	Accept: application/activity+json

The JSON body in the request will look something like this:

	{
	  "@context": "https://www.w3.org/ns/activitystreams", 
	  "object": {
	    "url": "https://www.manton.org/2018/10/15/not-just-for.html", 
	    "attributedTo": "https://manton.org/activitypub/manton", 
	    "content": "Not just for bloggers", 
	    "to": [
	      "https://www.w3.org/ns/activitystreams#Public", 
	      "https://mastodon.cloud/users/manton_test"
	    ], 
	    "published": "2018-10-18T14:02:14+00:00", 
	    "type": "Note", 
	    "id": "http://manton.micro.blog/2018/10/15/not-just-for.html", 
	    "cc": [
	      "https://micro.blog/activitypub/manton/followers"
	    ]
	  }, 
	  "type": "Create", 
	  "id": "https://micro.blog/4533FDCDF869351762C5", 
	  "actor": "https://manton.org/activitypub/manton"
	}

You will see the “@context” field across ActivityPub requests and responses. This is part of the JSON-LD standard, which ActivityStreams is based on. Most ActivityPub implementations just use a regular JSON parser, though, not one specific to handling JSON-LD, so no special processing is usually necessary.

The “type” value comes from ActivityStreams 2.0. In addition to creating a post, there are verbs for following users, liking a post, and other actions you’d expect in a social network like Mastodon.

To follow a user, a request of type “Follow” is sent. The “actor” is the user sending the follow request. The “object” is the actor URL for the account to follow.

	{
	  "@context": "https://www.w3.org/ns/activitystreams",
	  "type": "Follow",
	  "id": "...",
	  "actor": "manton@mastodon.social",
	  "object": "news@micro.blog"
	}

Accounts on Mastodon can be configured to either automatically accept new followers, or require the user to manually approve the follow request. In either case, an ActivityPub server will reply to the follow request to accept or deny it.

To accept a follow, a request with type “Accept” is sent, with a reference to the follow:

	{
	  "@context": "https://www.w3.org/ns/activitystreams",
	  "type": "Accept",
	  "id": "...",
	  "actor": "news@micro.blog",
	  "object": {
	    "type": "Follow",
	    "id": "...",
	    "actor": "manton@mastodon.social",
	    "object": "news@micro.blog"
	  }
	}

Note that the original follow request is included inside the acceptance. ActivityPub servers will usually need to keep some information about these activities so they can track them between requests.

### Attachments

Micro.blog posts are just blog posts. That means they use HTML for linking and inline photos. Mastodon posts are more like tweets: instead of inline `<img>` tags for photos, ActivityPub has a separate `attachment` field with any images included in the post.

	"attachment": [
		{
		  "type": "Document",
		  "mediaType": "image/jpeg",
		  "url": "https://micro.blog/photos/..."
		},
		{
		  "type": "Document",
		  "mediaType": "image/jpeg",
		  "url": "https://micro.blog/photos/..."
		}
	]

The ActivityStreams 2.0 spec outlines the fields for many of these types like attachments. There is some variance between implementations. For example, Mastodon uses type “Document” for images, while Threads uses type “Image”.

### Moving instances

While many of the fediverse developer community developed separately from the IndieWeb community, they both share some common principles around the open web, including account portability. If we have many thousands of Mastodon servers, users are going to want to be able to migrate between instances. This is a core selling point of Mastodon, as outlined on the [Mastodon servers page][4]:

> Find a different server you'd prefer? With Mastodon, you can easily move your profile to a different server at any time without losing any followers.

Mastodon’s account migration is built on two parts of ActivityPub:

* Including aliases in the actor profile JSON to specify a mapping between old and new accounts.
* Using the “Move” activity to notify followers to re-follow the new account.

The Mastodon documentation says that aliases should be set up on both sides of the migration, but this does not seem to be required. In my testing, an alias is only needed on the new instance.

Micro.blog has implemented account migration following Mastodon’s example.

Because I wanted to move to Micro.blog, I added an alias in Micro.blog that references one of my old accounts: @manton@mastodon.social. You can find this in Micro.blog under Account → View Mastodon Details → Aliases.

Aliases are added to the ActivityPub profile information in the field `alsoKnownAs`. Here's a snippet of my info:

	{
	  "preferredUsername": "manton",
	  "name": "Manton Reece",
	  "alsoKnownAs": [
	    "https://mastodon.social/users/manton"
	  ],
	  …
	}

The next step is to sign into the old Mastodon instance and tell it to move to Micro.blog. Mastodon will take a few actions when this starts:

* It will verify that there's an alias on Micro.blog, confirming that both accounts are yours.
* It will lock your Mastodon account, updating the profile to tell people about the new Mastodon instance. (In my case, actually powered by Micro.blog.)
* It will send a "Move" activity to all the instances for all your followers, telling them to update their references to point to your new username.

The "Move" activity is sent to each follower's inbox just like other activities such as "Create". It includes a field `target` for the new instance that the user is moving to:

	{
	  "actor": "https://mastodon.social/users/manton",
	  "target": "https://manton.org/activitypub/manton",
	  …
	}

Mastodon won't add `alsoKnownAs` to your ActivityPub profile on the old instance, but instead it will add a similar field named `movedTo` with the new actor URL:

	{
	  "preferredUsername": "manton",
	  "name": "Manton Reece",
	  "movedTo": "https://manton.org/activitypub/manton",
	  …
	}

Updating your followers can take quite a while — likely hours and possibly over a day, if you have hundreds or thousands of followers. It makes sense that this is a low priority background task. You can watch the progress as Mastodon essentially decrements your follower count on the old instance.

---- 

As 2023 was winding down, with a year of turmoil at Twitter, ActivityPub was well positioned to spread to more platforms. David Pierce captured this momentum [in an article at The Verge][5], making the case for the fediverse:

> Forget the hand-wavy protocol stuff for a second — one of the best things about embracing ActivityPub is that it sticks a crowbar into a single Voltron-ic product like Facebook or Twitter or Snapchat and pries it apart into its component pieces, each one ripe for innovation and new ideas.

Meta’s Threads started testing ActivityPub. Announced directly [from Mark Zuckerberg][6]:

> Starting a test where posts from Threads accounts will be available on Mastodon and other services that use the ActivityPub protocol. Making Threads interoperable will give people more choice over how they interact and it will help content reach more people. I'm pretty optimistic about this.

Adam Mosseri, the head of Instagram and Threads, also echoed this point in more detail on subsequent posts [and video updates][7]. The rollout was going to take a little while, but Threads had a clear path for adopting more and more of ActivityPub. Adam said:

> This work is taking longer than we thought given our safety work, given our compliance work, and given all the scrutiny on our company. But over 2024 we’re going to be adding the ability to post from Threads to these other servers. We’re going to eventually also support the ability to show replies in Threads natively, and eventually allow you to even follow accounts on those other servers from the Threads app itself.

Flipboard also embraced ActivityPub, starting by spinning up their own Mastodon instance and then working to build ActivityPub directly into the core Flipboard platform. Flipboard co-founder Mike McCue started a podcast called Dot Social about the fediverse, and [wrote on Medium][8] about the potential for Flipboard:

> This is the single largest expansion of the Flipboard ecosystem since we launched as a social magazine in 2010. I’m incredibly excited about how federation will benefit everyone on Flipboard and in the Fediverse. More importantly, I hope we can serve as inspiration for other apps and services contemplating the Fediverse.

ActivityPub was a new opportunity for Flipboard to expand. Twitter was stumbling through a series of ill-received changes (including shutting down the Twitter API, which hurt Flipboard directly) at the same time that ActivityPub was growing. Flipboard got new momentum by coming along with ActivityPub for the next path forward for the social web.

ActivityPub is another layer on top of the web. It will always require custom software, either Mastodon itself or something compatible with ActivityPub, like Micro.blog, Threads, and Flipboard. Basing your identity instead on blogs means you can use anything that can generate HTML, from WordPress to Micro.blog to a static site, hosted anywhere.

[1]:	https://www.w3.org/2014/06/social.html.en
[2]:	https://tools.ietf.org/html/rfc7033
[3]:	https://www.w3.org/wiki/SocialCG/ActivityPub/Authentication_Authorization
[4]:	https://joinmastodon.org/servers
[5]:	https://www.theverge.com/23990974/social-media-2023-fediverse-mastodon-threads-activitypub
[6]:	https://www.threads.net/@zuck/post/C0zXcQmxO77
[7]:	https://www.threads.net/@mosseri/post/C01zMgWp4V-
[8]:	https://medium.com/@mmccue/flipboard-begins-to-federate-4a80d6bdc209
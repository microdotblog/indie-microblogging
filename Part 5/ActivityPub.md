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

So for a username like `manton@mastodon.social`, you should make a WebFinger request to "mastodon.social". For `aaronpk@aaronparecki.com`, it would be a connection to "aaronparecki.com". (Most Mastodon users share an instance, but some people run a single-user instance with their own domain name.)

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

### The inbox

Most requests in Mastodon are sent to a user’s inbox. This is an endpoint that receives follow requests, new posts from other users you might be following, and even notifications when a post is removed, so that an instance can update its own copy of posts and user accounts.

To discover the inbox and other URLs for a user, we query the actor URL found from WebFinger:

	GET /users/manton
	Host: mastodon.social
	Accept: application/ld+json

Mastodon uses HTTP content negotiation. The “Accept” header needs to be sent to indicate what kind of response you want to receive.

Mastodon instances and other platforms that implement ActivityPub will need to store this data. Requests to the inbox are signed, and the public key fields can be used to verify requests.

The full response from Mastodon is quite long. Here’s a partial response of the key JSON fields:

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

The “type” value comes from ActivityStreams 2.0. In addition to creating a post, there are verbs for following users, liking a post, and other actions you’d expect in a social network like Mastodon.

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

### Moving instances

...

---- 

Mastodon is another layer on top of the web. It will always require custom software, either Mastodon itself or something compatible with ActivityPub. Basing your identity instead on blogs means you can use anything that can generate HTML, from WordPress to Micro.blog to a static site, hosted anywhere.

[1]:	https://www.w3.org/2014/06/social.html.en
[2]:	https://tools.ietf.org/html/rfc7033
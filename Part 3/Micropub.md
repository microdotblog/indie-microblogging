## Micropub

_“The technical folks in the blogging world have learned a lot of the past few years about RSS and the blogging APIs—about what works well and what doesn't. And, despite the efforts that have gone into certain directions, we feel it'd be unfortunate this early in the game to be married to a certain direction just because we started out that way when we didn't know as much.” — [Evan Williams][1], Blogger API post from 2003_

Micropub is one of several important IndieWeb building blocks, answering the question: what would a posting API look like if we started over, stripping away everything except the most basic requirement of sending post text to a server, and then build on top of that foundation when clients and servers in the real world need more?

Many protocols attempt to be so comprehensive that they start off complicated and difficult to implement unless all at once. They over-specify everything that might be needed, even if there is no real-world example in use for it yet. Micropub isn't like that.

### Learning from XML-RPC and AtomPub

To understand how Micropub came to be — first created in 2015 and then formalized as a W3C recommendation in 2017 — we should rewind back in 2001 with the Blogger API and XML-RPC.

For my interview with Brent Simmons in Part 2, Brent talks about how easy XML-RPC was. And with good tools that understood XML, like the Frontier scripting environment that Brent worked in, it _was_ easy. All the complexity of serializing data structures into XML was hidden from you.

But actually inspecting the data passed between client and servers revealed an admittedly ugly format that would stump most developers today as being needlessly verbose. Even worse, there was no way to build a script to process these requests on the server without bundling in an XML-RPC framework.

Common data types such as integers, strings, and structs are encoded with rules outlined in the XML-RPC specification. To create a new post with the words "Hello world", the XML-RPC request might look like this:

	<?xml version="1.0"?>
	<methodCall>
	  <methodName>blogger.newPost</methodName>
	  <params>
	    <param>
	      <value><int>app ID</int></value>
	    </param>
	    <param>
	      <value><int>blog ID</int></value>
	    </param>
	    <param>
	      <value><string>manton</string></value>
	    </param>
	    <param>
	      <value><string>mypassword</string></value>
	    </param>
	    <param>
	      <value><string>Hello world.</string></value>
	    </param>
	    <param>
	      <value><boolean>1</boolean></value>
	    </param>
	  </params>
	</methodCall>

Note that the username and password are passed in the clear. There was no separate mechanism at the time, such as OAuth or IndieAuth, for authenticating a user and using more secure tokens with each request.

Subsequent blogging platforms extended the Blogger API with their own features. Instead of `blogger.newPost`, Movable Type had their own `mt.newPost` with similar parameters, adding a title field. WordPress had `wordpress.newPost`, and still supports XML-RPC today.

To try to unify some of these improvements in a vendor-neutral standard, Dave Winer proposed the [MetaWeblog API][2]. MetaWeblog switched to passing content as structs, which could more easily be extended with additional fields, and added an image upload API, `metaWeblog.newMediaObject`. Dave patterned the field names after RSS:

> The MetaWeblog API uses an XML-RPC struct to represent a weblog post. Rather than invent a new vocabulary for the metadata of a weblog post, we use the vocabulary for an [item][3] in RSS 2.0. So you can refer to a post's title, link and description; or its author, comments, enclosure, guid, etc using the already-familiar names given to those elements in RSS 2.0.

Dave wasn't the only one who hoped to bring consistency between feed formats and a blogging API. A couple of years later, AtomPub was created based on Atom feeds.

Ben Trott of Six Apart, makers of Movable Type, [blogged at the time][4] about the benefits to basing an API on the Atom feed format, which back then was called Echo:

> Benefits to developers: using the same data model and serialization for syndication, archiving, and editing simplifies the development of tools to work with (produce and consume) these formats, for obvious reasons: code written to produce an item in an Echo feed, for example, can also be used for producing data sent in an API request or packaged up for archiving.

AtomPub was adopted in Blogger but is not supported in any other modern blogging platforms. In early 2020, MarsEdit developer Daniel Jalkut announced that he would also be phasing out support for posting to Blogger.

As XML-RPC was falling out of style, Roy Fielding coined the term "representational state transfer", or REST, to describe the design of an API that acted on multiple web resources, retrieved and updated with standard HTTP methods such as `GET`, `POST`, and `PUT`. REST stepped back from the complexity of how requests were encoded in XML-RPC.

Most of today's platforms follow a REST style, but there was no open blogging API proposed using REST. There was also a move away from XML, with most new APIs using JSON.

WordPress still supports the XML-RPC API but has its own, WordPress-specific JSON API. Silos like Twitter, Facebook, and Medium create their own platform-specific API, or no posting API at all. Enough years had passed that the IndieWeb community could now take a fresh look at blogging APIs, learning from past formats to create a new open API that wasn't tied to any platform.

### Intro to Micropub

Micropub is a W3C recommendation and Micro.blog's native posting API. In an effort to make basic posting as simple as possible, while still allowing more advanced functionality, there are 2 formats for Micropub:

* **Form-encoded.** The easiest way to get started and useful from any programming language or scripting tool.
* **JSON.** With field names and structure based on conventions from Microformats.

Unlike many REST-based APIs, Micropub uses a single URL endpoint with multiple parameters to specify actions such as editing or deleting an existing post. This makes it easier to drop an implementation of Micropub into an existing web site or web application. This main endpoint is discovered by looking for a link tag in the blog's home page HTML:

	<link rel="micropub" href="https://micro.blog/micropub">

Requests will need an authentication token. This is usually provided by IndieAuth, although Micro.blog also lets users generate new tokens for specific apps under their account. When you have a token, it's set in an `Authentication: Bearer` HTTP header.

Now that we have the endpoint and auth token, we can use form-encoded parameters to create a new post. The following Micropub request creates a new post with the text "Hello world."

	POST /micropub
	Authorization: Bearer 123456789
	Content-Type: application/x-www-form-urlencoded
	
	h=entry&content=Hello%20world.

This request requires so little that it can even be used directly from the `curl` command line:

	curl -d "h=entry" -d "content=Hello world" -H "Authorization: Bearer 123456789" "https://micro.blog/micropub"

This shows the value of embracing simple HTTP requests. Calling an XML-RPC API from `curl` would be much more difficult.

When creating a new post, Micropub also accepts a "name" parameter to give the post a title:

	POST /micropub
	Authorization: Bearer 123456789
	Content-Type: application/x-www-form-urlencoded
	
	h=entry&name=Hello&content=This%20post%20is%20longer.

The `h=entry` may look familiar from Microformats. Micropub follows Microformats naming conventions. This table compares the Microformats class names with the Micropub fields:

| Microformats 2 | Micropub API |
| -------------- | ------------ |
| h-entry        | h=entry      |
| p-name         | name=        |
| e-content      | content=     |
| dt-published   | published=   |

### Uploading photos

To upload a photo to a Micro.blog-hosted blog, first query Micropub by sending a configuration request with the `q` parameter, which will return the media endpoint:

	GET /micropub?q=config
	Authorization: Bearer 123456789

This will return a response like:

	{
	  "media-endpoint": "https://micro.blog/micropub/media"
	}

The media endpoint accepts a `multipart/form-data` upload with a file part containing the JPEG image data. Micro.blog will send back an HTTP 202 response while the image is being copied to the published site. It may take a few seconds for it to be available at the URL in the response:

	HTTP/1.1 202 Accepted
	Location: https://username.micro.blog/uploads/123.jpg

Now that you have the URL for the uploaded photo, you can add a photo parameter to a new post. To set alt text for the photo, also include an `mp-photo-alt` parameter.

	POST /micropub
	Authorization: Bearer 123456789
	Content-Type: application/x-www-form-urlencoded
	
	h=entry&content=Hello%20world.&photo=https://...&mp-photo-alt=Description%20here.

The alt text parameter is not part of the original Micropub spec, but was instead proposed later through an extension to Micropub. In fact, the spec itself outlines only the initial framework for request and posting basics. Many useful parts of Micropub come from conventions used in the IndieWeb community. Once there are a few client and server implementations of a proposal, it is considered stable.

### More complex posts

The JSON variation of Micropub is needed for sending more complex representations of a blog post. For example, sending HTML or location check-in information. It is also used for querying a list of posts.

Our simple form-encoded example from earlier would look like this when formatted with JSON:

	POST /micropub
	Authorization: Bearer 123456789
	Content-Type: application/json
	
	{
	  "type": [ "h-entry" ], 
	  "properties": {
	    "content": [ "Hello world." ]
	  }
	}

To create a new post using HTML, clients can be explicitly about the format by adding an `html` field to the content:

	 POST /micropub
	 Authorization: Bearer 123456789
	 Content-Type: application/json
	
	 {
	   "type": [ "h-entry" ], 
	   "properties": {
	     "content": [
	       {
	         "html": "<p>Hello world.</p>"
	       }
	     ]
	   }
	 }

Note that most values when using JSON with Micropub are actually arrays, surrounded by `[` and `]`, even if there can only be 1 item in the array. While this makes the simplest requests more verbose and harder to read than the form-encoded version of Micropub, it also allows for richer types of data.

When using the JSON version of the Micropub API, Micro.blog can store location data with a blog post, including venue name, URL, latitude, and longitude.

To just send coordinates, use the location property:

	POST /micropub
	Authorization: Bearer 123456789
	Content-Type: application/json
	
	{
	  "type": [ "h-entry" ], 
	  "properties": {
	    "content": [ "Texas Book Festival." ], 
	    "location": [
	      {
	        "type": [ "h-adr" ], 
	        "properties": {
	          "latitude": [ 30.273892650534542 ], 
	          "longitude": [ -97.74060666521329 ]
	        }
	      }
	    ], 
	    "published": [ "2019-10-27T14:51:32-05:00" ]
	  }
	}

If you are making a check-in post with venue information, use the checkin property:

	POST /micropub
	Authorization: Bearer 123456789
	Content-Type: application/json
	
	{
	  "type": [ "h-entry" ], 
	  "properties": {
	    "content": [ "Texas Book Festival." ], 
	    "checkin": [
	      {
	        "type": [ "h-card" ], 
	        "properties": {
	          "url": [ "https://foursquare.com/v/4d8a30f199c2a1cd53508bd7" ], 
	          "latitude": [ 30.273892650534542 ], 
	          "name": [ "Texas Capitol Grounds" ], 
	          "longitude": [ -97.74060666521329 ]
	        }
	      }
	    ], 
	    "published": [ "2019-10-27T14:51:32-05:00" ]
	  }
	}

Using JSON is helpful for other types of applications too. IndieBookClub is a service that lets people easily post about a book they are reading. It prompts for the book’s title and ISBN, and then formats that as a Micropub request to your server using the `read-of` property, which contains details about the book:

	POST /micropub
	Authorization: Bearer 123456789
	Content-Type: application/json
	
	{
	  "type": [ "h-entry" ],
	  "properties": {
	    "summary": [ "Currently reading: The Tombs of Atuan by Ursula K. Le Guin, ISBN: 9780689845369" ],
	    "read-status": [ "reading" ],
	    "read-of": [
	      {
	        "type": [" h-cite" ],
	        "properties": {
	          "name": [ "The Tombs of Atuan" ],
	          "author": [ "Ursula K. Le Guin" ],
	          "uid": [" isbn:9780689845369" ]
	        }
	      }
	    ]
	  }
	}

Micro.blog recognizes these “read of” posts and does some lightweight processing on the post text, such as linking the book title. Because IndieBookClub provides a `summary` field, not all Micropub servers need to understand these types of requests. Other servers can simply fall back on using the `summary` and ignore the `read-of` properties.

### Other actions

Micro.blog accounts can have multiple blogs defined for a single username. You might have your main blog, a photos blog, and a test blog to try out design changes, for example. You can use the Micropub extension `mp-destination` to specify which blog to post to when making a request.

A list of defined blogs will be returned from the `q=config` request we used to get the media endpoint for uploading photos:

	{
	  "media-endpoint": "https://micro.blog/micropub/media",
	  "destination": [
	    {
	      "uid": "https://manton.micro.blog/", 
	      "name": "manton.micro.blog"
	    }, 
	    {
	      "uid": "https://news.micro.blog/", 
	      "name": "news.micro.blog"
	    }
	  ]
	}

The `uid` field is the URL for a specific blog on the user's account. Pass that URL value when posting:

	POST /micropub
	Authorization: Bearer 123456789
	Content-Type: application/x-www-form-urlencoded
	
	h=entry&content=Hello%20world.&mp-destination=https://manton.micro.blog/

Micropub can also be used to delete posts, edit posts, and send other types of content such as replies and bookmarks. Because favorites on Micro.blog are more like bookmarks than public "likes", Micro.blog converts bookmarks via Micropub to favorites on Micro.blog.

To create a bookmark, pass the `bookmark-of` parameter with the URL for the resource you want to bookmark.

	POST /micropub
	Authorization: Bearer 123456789
	Content-Type: application/x-www-form-urlencoded
	
	h=entry&content=Enjoyed%20reading%20this.&bookmark-of=https://example.com/interesting-article/

Getting a list of posts is similar to getting the configuration information, but instead of passing `q=config`, use `q=source`:

	GET /micropub?q=source

Micro.blog returns the posts in reverse-chronological order, with the familiar Microformats-style formatting as creating a new post using JSON:

	{
	  "items": [
	    {
	      "type": "h-entry",
	      "properties": {
	        "uid": [ 12345 ],
	        "name":[ "Title here" ],
	        "content": [ "Hello world." ],    
	        "published": [ "2020-07-14T18:54:18+00:00" ],
	        "post-status":[ "published" ],
	        "url": [ "https://www.manton.org/2020/..." ]
	      }
	    }
	  ]
	}

You can also limit the number of posts, or page through the results using the `offset` parameter. For example, to get the most recent 100 posts:

	GET /micropub?q=source&limit=100

And then to get the _next_ 100 posts:

	GET /micropub?q=source&limit=100&offset=100

To edit a post, send `action=update` using the JSON version of Micropub. The request will look just like creating a new post, with the addition of a `url` field for which post to edit. Instead of a `properties` field, use a field called `replace` to list which post properties to update:

	POST /micropub
	Authorization: Bearer 123456789
	Content-Type: application/json
	
	{
	  "action": "update",
	  "url": "https://www.manton.org/2020/…",
	  "replace": {
	    "content": [ "Hello again. Updated text here." ]
	  }
	}

To delete a post, send `action=delete` with the `url` of the post to delete using the simple form-encoded format:

	POST /micropub
	Authorization: Bearer 123456789
	Content-Type: application/x-www-form-urlencoded
	
	action=delete&url=https://…

There are many IndieWeb-friendly apps for posting to your blog, and they all use Micropub. These apps are often good secondary apps for specific purposes. You can use the official Micro.blog app for your normal microblog posts, and a specialized tool for uploading photos, creating bookmarks, sharing a book you're reading, and more.

### Drafts and categories

Micro.blog supports creating drafts on the server, for posts that aren’t ready to be published. To create a draft, add the `post-status=draft` parameter to your requests:

	POST /micropub
	Authorization: Bearer 123456789
	Content-Type: application/x-www-form-urlencoded
	
	h=entry&content=Hello%20world&post-status=draft

To later publish the post, update it using `action=update` and set `post-status=published`.

You can also set categories for your posts. To add a “Photos” category to a new post, add a parameter like `category=Photo`. You can set multiple categories by using `category[]`:

	POST /micropub
	Authorization: Bearer 123456789
	Content-Type: application/x-www-form-urlencoded
	
	h=entry&content=Hello%20world&category[]=Photos&category[]=Testing

To get a list of categories already set for your blog, send a `q=category` query for the categories:

	GET /micropub?q=category

The response will look like:

	{
	  categories":  [ "Photos", "Testing", "Travel", "Writing" ]
	}

Some people use categories more like tags, so it’s possible that the results could contain hundreds of categories. A convention across the Micropub API is to use a `filter` parameter to return a subset of results, so we can use that here to search categories:

	GET /micropub?q=category&filter=pho
	
	{
	  categories":  [ "Photos" ]
	}

### Getting standalone pages and uploads

IndieWeb blogs often have several post types, loosely following the Microformats standard:

* note: a short microblog post
* article: a full-length blog post with a title
* photo: a post that includes one or more photos
* rsvp: a post that is RSVP-ing to an event
* reply: a post that is a reply to another post
* ...and others

This type can be inferred from the content on the page using the Post Type Discovery specification. For example, if the post includes an `img` tag with a Microformats class `u-photo`, it’s a photo post.

There’s one type of content that isn’t well-covered in this list: standalone pages on your blog. These aren’t date-based like a blog post, but instead are usually pages that exist outside the reverse-chronological home page, like “About”, “Photos”, or “Archive”. They can be included in your blog’s navigation or sidebar.

Micro.blog uses a special “channel” for these standalone pages. When querying the Micropub config with `q=config`, the available channels will be returned:

	{
	  "channels": [
	    {
	      "uid": "default",
	      "name": "Posts"
	    },
	    {
	      "uid": "pages",
	      "name": "Pages"
	    }
	  ]
	}

We can pass the `uid` for “pages” in a new `mp-channel` parameter to Micropub when creating a new post:

	POST /micropub
	Authorization: Bearer 123456789
	Content-Type: application/x-www-form-urlencoded
	
	h=entry&content=Hello&mp-channel=pages

When using the JSON version of Micropub, `mp-channel` is included along with other properties. It’s not a property itself; the `mp-` prefix is used for commands to Micropub:

	POST /micropub
	Authorization: Bearer 123456789
	Content-Type: application/json
	
	{
	  "type": "h-entry",
	  "properties" {
	    "content": "Hello",
	    "mp-channel": "pages"
	  }
	}

To query Micropub for just these standalone pages, use the `mp-channel` parameter:

	GET /micropub?q=source&mp-channel=pages

The response will look similar to getting a list of regular blog posts:

	{
	   "items": [
	     { 
	       "type": "h-entry",
	       "properties": {
	         "uid": [ 12345 ],
	         "name": [ "Title here" ],
	         "content": [ "Hello world." ],
	         "published": [ "2020-05-19T15:39:00+00:00" ],
	         "url":[ "https://www.manton.org/..." ]
	       }
	     }
	   ]
	 }

There’s also an extension to Micropub for getting a list of uploaded files such as JPEGs or MP3s. It's similar to getting a list of posts, but sent to the media endpoint:

	GET /micropub/media?q=source
	
	{
	  "items": [
	    {
	      "url": "https://www.manton.org/uploads/2020/058fa92305.png", 
	      "published": "2020-05-27T14:14:09+00:00"
	    }, 
	    {
	      "url": "https://www.manton.org/uploads/2020/7a57980ca2.jpg", 
	      "published": "2020-05-20T02:22:09+00:00"
	    }
	  ]
	}

The `q=source` query on the media endpoint also supports the same `limit` and `offset` parameters as querying for a list of regular blog posts.

Micropub continues to evolve through extensions, but already has everything you need for maintaining a blog. While not all Micropub servers support everything that Micro.blog does, all servers will support basic posting, making Micropub an ideal place to start when writing a new client or script, and a good place to build from with future extensions.

[1]:	https://web.archive.org/web/20030815183345/https://www.blogger.com/developers/2003_07_01_archive.pyra
[2]:	http://1998.xmlrpc.com/metaWeblogApi.html
[3]:	https://cyber.harvard.edu/rss/rss.html#hrelementsOfLtitemgt
[4]:	https://web.archive.org/web/20030707045207/http://www.sixapart.com/log/2003/06/why_we_need_ech.shtml
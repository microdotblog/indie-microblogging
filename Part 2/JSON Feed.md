## JSON Feed

_“I gave it a specification and a little web site. All the rest happened by itself.”_
_— [Douglas Crockford][1] on documenting JSON_

Twenty years after RSS was getting its start, [Brent Simmons blogged about][2] introducing a new format called JSON Feed. He started by pointing to Dave Winer's rules for new standards, that it's better to have fewer formats:

> I agree completely — but I also believe that developers (particularly Mac and iOS developers, the group I know best) are so loath to work with XML that they won’t even consider building software that needs an XML parser. Which says to me that JSON Feed is needed for the survival of syndication.

We believed that a new format would help the open web get a kick, bootstrapping new work. RSS is pervasive, but there are little quirks that still trip up developers, and XML has fallen out of favor. New APIs are being written in JSON.

JSON Feed is an alternative to RSS. JSON Feed is easy to generate and was designed with microblogs in mind. The title in each post is optional:

> Microblogs, which are often plain text and without titles. So much web writing today is Twitter-like, which is actually plain text.

Another advantage of JSON is that HTML can be used without the special escaping that is required in RSS. Because HTML tags and XML elements both use angle brackets, they must be escaped in RSS, often producing unreadable markup.

Here's an example JSON Feed with a single microblog post:

	{
	    "version": "https://jsonfeed.org/version/1",
	    "home_page_url": "http://www.manton.org",
	    "feed_url": "http://www.manton.org/feed/json",
	    "title": "Manton Reece",
	    "items": [
	        {
	            "id": "http://www.manton.org/2018/04/6721.html",
	            "url": "http://www.manton.org/2018/04/6721.html",
	            "content_html": "<p>No sweep. What a great game. Go Spurs.</p>",
	            "date_published": "2018-04-22T21:56:28+00:00",
	            "author": {
	                "name": "manton"
	            }
	        }
	    ]
	}

This clarity led to quick adoption. Within weeks of releasing the specification, many popular apps had added support for JSON Feed.

JSON Feed also helped achieve the goal of having more feed readers update to support title-less items. Feeds readers like Feedbin and Inoreader both have excellent support for short microblog posts.

This is what my microblog looks like in Feedbin. Notice that the list has variable heights to accommodate the full text of a short post, including inline photos:

![][image-1]

Micro.blog extends JSON Feed with a few extra fields that are appropriate for a microblogging service, such as account username and whether a post has been favorited by the current user.

JSON Feed uses a special field naming convention to add custom objects to a feed. Fields that start with an underscore character are custom objects provided by a service like Micro.blog. Micro.blog uses the field name `_microblog` for its custom objects.

	"author": {
	  "name": "Jonathan LaCour",
	  "url": "https://cleverdevil.io",
	  "avatar": "https://micro.blog/cleverdevil/avatar.jpg",
	  "_microblog": {
	    "username": "cleverdevil"
	  }
	}

Adding these custom fields to JSON Feed allows Micro.blog to use JSON Feed for its API, rather than inventing a new JSON format. The JSON APIs for Twitter, Facebook, Medium, and other social networks are all very different and not compatible with any other apps without custom support. Because Micro.blog uses JSON Feed for any API endpoint that returns a list of posts, Micro.blog's API can often be used directly by other feed readers.

The following API endpoints all return JSON Feed:

* `/posts/all`
* `/posts/mentions`
* `/posts/bookmarks`

Further, the public sections of Micro.blog's API (such as the Discover feeds) also use JSON Feed. They do not need authentication so can be used in any feed reader that supports JSON Feed:

* `/posts/discover`
* `/posts/photos`
* `/posts/discover/books`

And finally, hosted blogs on Micro.blog also use JSON Feed for recent posts, posts, and the archive:

* `yourdomain.com/feed.json`
* `yourdomain.com/photos/index.json`
* `yourdomain.com/archive/index.json`

In some of the photo feeds, Micro.blog again extends JSON Feed to provide more information, such as a thumbnail version of photos. The photo is included in the HTML, so that all feed readers have everything they need to show the post, as well as a separate `image` field for clients that support it, and a `thumbnail_url` with a smaller version created by Micro.blog:

	{
	  "id": "https://www.manton.org/2020/04/20/wildflowers.html",
	  "title": "",
	  "content_html": "<p>Wildflowers.</p><p><img src=\"https://www.manton.org/uploads/2020/f53a913d74.jpg\" /></p>",
	  "date_published": "2020-04-20T15:55:39-05:00",
	  "url": "https://www.manton.org/2020/04/20/wildflowers.html",
	  "image": "https://www.manton.org/uploads/2020/f53a913d74.jpg",
	  "_microblog": {
	    "thumbnail_url": "https://micro.blog/photos/400/https://www.manton.org/uploads/2020/f53a913d74.jpg"
	  }
	}

Adopting JSON Feed everywhere in Micro.blog allows the platform to be compatible with many feed readers, and brings consistency across most of the API.

[1]:	https://youtu.be/-C-JoyNuQJs
[2]:	http://inessential.com/2017/05/17/json_feed

[image-1]:	https://book.micro.blog/uploads/2020/4e6da441a3.png
## Indie readers

_“Modularity increases the chance that at least some of it can and will be re-used, improved, which you can then reincorporate.” — [IndieWeb principles][1]_

Mastodon brought several protocols together in a new, more user-friendly web application that was familiar to Twitter users. On the IndieWeb side, "indie readers" attempt to do the same thing with IndieWeb protocols, providing a consistent interface on top of IndieWeb building blocks.

The UI for an indie reader is like a blending of Micro.blog's timeline and a traditional RSS feed reader. Users can subscribe to any blog, and in some cases even reply or favorite posts directly in the reader interface.

At IndieWeb Summit 2017, Jonathan LaCour introduced a session called [“Putting it all together”][2]. The reason that Facebook is so successful, he argued, is that they put together the entire experience: content creation with short status updates and photos; content consumption with a feed; and content interaction with likes and sharing.

Jonathan went on to demo a plug-in he had built for his RSS reader that let him reply and like blog posts:

> My notion is that people should have this nice, integrated experience. And if they can, more people will use it, because it’s easy and interesting. It’s delightful.

To reach more people, we would need more tools and that meant an IndieWeb specification to provide a common interface for IndieWeb readers and servers.

Whereas most RSS readers sync with a centralized API like Feedbin, indie readers would distribute the syncing and caching of feeds to any number of servers. You could have your own indie reader server, or you could have an account on a shared server powered by software such as Aaron Parecki’s Monocle.

These server are based on a new API called Microsub. What Micro**pub** is for _publishing_ posts, Micro**sub** is for _subscribing_ to blogs. Indie readers use both Micropub and Microsub to provide a unified interface to reading and posting.

### Microsub

Micro.blog has always had a JSON-based API for following users and downloading posts in the timeline. It is based on JSON Feed, with some extensions just for Micro.blog.

What Microsub adds is a general framework for how to subscribe to blogs. It's a more open alternative to Micro.blog’s JSON API. If you want to build an app for reading the Micro.blog timeline and following users, you can build it against the Microsub API and your app will be compatible with more services, not just Micro.blog.

To sign in to an indie reader, you use your domain name. Unlike the Micro.blog API which is always hosted at `micro.blog`, the first step with using Microsub is to discover the user's endpoint by checking the HTML at their domain name.

Just like Micropub and Webmention, the Microsub endpoint is included in a `link` tag:

	<link rel="microsub" href="https://micro.blog/microsub" />

Authentication in Microsub uses IndieAuth. After you have a valid token to call the Microsub server, you can make several types of requests, including:

* following a blog
* getting a list of posts in the timeline

Many responses in Microsub use JF2, a simplified version of the JSON flavor of Microformats. It resembles JSON Feed but is not the same thing, using different field names. A post in JF2 might look like this:

	{
	  "author": {
		"url": "https://aaronparecki.com/", 
		"photo": "...", 
		"type": "card", 
		"name": "Aaron Parecki"
	  }, 
	  "url": "https://aaronparecki.com/2022/03/03/7/", 
	  "content": {
		"html": "<p>...</p>"
	  }, 
	  "published": "2022-03-03T15:57:29.000+00:00", 
	  "_id": "12546606", 
	  "type": "entry"
	}

Just like Micropub, Microsub uses a single main URL. Different types of requests use the `action` parameter.

One of the most important things a Microsub server can do is aggregate multiple posts from the blogs you're following and put them together in a timeline. Microsub clients can then request these posts:

	GET /microsub?action=timeline

The posts are in reverse-chronological order, just like Micro.blog. To page through additional posts, use the `after` parameter:

	GET /microsub?action=timeline&after=12546606

### Monocle and Aperture

In the spirit of IndieWeb’s principle of modularity, when Aaron Parecki began coding support for Microsub, he split that support into multiple projects. That way, each one can be swapped out for another tool if needed, or they can be used together:

* [Monocle][3] is the front-end UI for browsing channels and reading posts in the timeline.
* [Aperture][4] is the server implementation for managing feeds and channels.
* [Watchtower][5] is responsible for downloading web pages to see if they’ve changed.
* [Switchboard][6] is the WebSub hub we mentioned in the previous chapter.

Monocle provides a clean timeline UI and supports posting via Micropub. This is what it looks like when used with Micro.blog’s WebSub implementation:

![][image-1]

Other tools came out of that early IndieWeb Summit session and later work on Aperture. [Together][7] (for the web) and [Indigenous][8] (for iOS and Android) are two additional Microsub clients.

### Micro.blog and Microsub

Micro.blog does not have the concept of user-editable groups of subscriptions. Instead, Micro.blog makes available to Microsub the core sections of its interface: Timeline, Mentions, Favorites, and Discover. Each of these is a hard-coded "channel" in Microsub.

	GET /microsub?action=channels

The response from Micro.blog looks like this:

	{
	  "channels": [
	    {
	      "uid": "default", 
	      "name": "Timeline"
	    }, 
	    {
	      "uid": "notifications", 
	      "name": "Mentions"
	    }, 
	    {
	      "uid": "bookmarks", 
	      "name": "Bookmarks"
	    }, 
	    {
	      "uid": "discover", 
	      "name": "Discover"
	    }
	  ]
	}

Modern web platforms will need to be a blend of services: support for feeds with RSS and JSON, IndieWeb building blocks, and even some ActivityPub. Microsub and indie readers are an important part of this future. The default of closed silos like Twitter or Facebook — proprietary APIs, or increasingly no APIs at all — does not advance our goals for a more open, connected web.

[1]:	https://indieweb.org/principles
[2]:	https://indieweb.org/2017/together
[3]:	https://monocle.p3k.io
[4]:	https://aperture.p3k.io
[5]:	https://github.com/aaronpk/watchtower
[6]:	https://switchboard.p3k.io
[7]:	https://alltogethernow.io
[8]:	https://indieweb.org/Indigenous

[image-1]:	https://book.micro.blog/uploads/2022/52b71c0469.png
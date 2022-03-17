## WebSub

The notifications-based approach of Mastodon means that there doesn’t need to be regular polling. Instead of a client checking a page or feed every few minutes for new posts, ActivityPub in Mastodon sends posts to all followers as the post is published.

Contrast with traditional RSS feed readers. One of the most important things a feed reader or new service like Micro.blog has to do is download posts from other sites via RSS. Whether that’s a Microformats feed, RSS, or a JSON Feed.

To check for new posts, Micro.blog makes an HTTP request to your blog for the feed:

![][image-1]

That's pretty simple, except that there are a lot of blogs out there. It's inefficient when scaled to thousands of blogs. Micro.blog is constantly working in the background to download feeds over and over to see if anything is new.

![][image-2]

Polling feeds is slow. In addition to making the HTTP request, the feed will also need to be parsed to check for new posts. To speed things up, Micro.blog and most feed readers support sending an `If-Modified-Since` or `If-None-Match` header, which lets the server return whether the feed has actually changed since the last time it was accessed.

When first requesting the feed, a client like Micro.blog or a feed reader would make note of the `etag` header in the response:

	HTTP/2 200 
	content-type: application/json
	etag: "r84z24dug"
	last-modified: Wed, 02 Mar 2022 21:15:40 GMT
	content-length: 17944

Micro.blog will store this etag value in its database. On subsequent requests, the client will send the etag, asking for new content only if the tag has changed, denoting that the feed has new posts in it:

	GET /feed.json
	If-None-Match: r84z24dug

If the feed hasn’t changed, Micro.blog will receive a “304 Not Modified” response.

There’s an even better way. The blog can notify the RSS aggregator, in this case Micro.blog, whenever there’s a new post. “Ping! I wrote a new post.”

![][image-3]

Instead of Micro.blog asking for the feed hundreds of times each day, even if there are no new posts, the blog itself reaches out to Micro.blog when there are actually new posts.

Micro.blog accepts 2 versions of a ping like this:

* Simple HTTP post
* XML-RPC based ping

The simple HTTP post looks like this, passing the feed URL as a URL-encoded parameter:

	POST /ping
	Content-Type: application/x-www-form-urlencoded
	
	url=https://your-blog.com/feed.json

This is Micro.blog-specific and not a standard, but it is so simple that it's useful for scripts and other tools that work with Micro.blog.

The XML-RPC approach is a little more complicated. It uses the same XML protocol as the MetaWeblog API covered in the Micropub chapter. XML-RPC pings are still supported by WordPress.

XML-RPC is very verbose. As we've already covered leading up to JSON Feed, most developers do not want to work with an XML parser, let alone another layer of abstraction provided by XML-RPC.

---- 

This brings us to WebSub, [a W3C recommendation][1] from the IndieWeb community. It was formerly called PubSubHubbub.

> WebSub provides a common mechanism for communication between publishers of any kind of Web content and their subscribers, based on HTTP web hooks. Subscription requests are relayed through hubs, which validate and verify the request. Hubs then distribute new and updated content to subscribers when it becomes available.

WebSub adds a new service — a hub — in between the RSS aggregator like Micro.blog and all the blog feeds. In your feed, you link to a hub that you will notify about new posts. Micro.blog can then "subscribe" to your blog using the hub:

![][image-4]

Now all the blogs can tell the hub when there’s a new post. The hub handles a lot of scaling complexity. A particular blog only has to notify the hub, not potentially many aggregators, and then the hub notifies Micro.blog:

![][image-5]

The more blogs that can support WebSub, the closer we’ll get to real-time notifications when new blog posts are published, improving the user experience of IndieWeb-friendly social networks that are distributed across the web. Because there can be multiple hubs, the notification load does not need to be concentrated in one place that could be a bottleneck.

No one wants to wait 5 minutes for a post to show up. Fast posting also enables new types of blogs, such as liveblogs.

WordPress.com already supports this by default. There is also a WordPress plugin for self-hosted blogs, and JSON Feed includes a `hubs` field so that WebSub support can be described for a blog without needing an RSS or XML feed.

Most blogs can use an existing WebSub hub. For anyone who wants to control every part of the notification process, Aaron Parecki’s open source project [Switchboard][2] is a hub you can host yourself.

[1]:	https://www.w3.org/TR/websub/
[2]:	https://github.com/aaronpk/Switchboard

[image-1]:	https://book.micro.blog/uploads/2019/0f0d87937f.png
[image-2]:	https://book.micro.blog/uploads/2019/817a6bf817.png
[image-3]:	https://book.micro.blog/uploads/2019/f7c48639d9.png
[image-4]:	https://book.micro.blog/uploads/2019/587d4a3f84.png
[image-5]:	https://book.micro.blog/uploads/2019/1a0303be41.png
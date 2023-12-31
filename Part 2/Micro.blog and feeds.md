## Micro.blog and feeds

_“As software developers and designers, we have a responsibility to the world to think these things through carefully and design software that makes the world better, or, at least, no worse than it started out.” — [Joel Spolsky][1]_

No matter which blogging platform you use, the posts flow into Micro.blog from RSS and JSON feeds. Even microblogs hosted by Micro.blog itself generate their own feeds — just like WordPress or any blogging platform — which Micro.blog then reads from. Abstracting the connection with feeds makes for a consistent experience across a variety of blogs.

The central user interface in Micro.blog is the timeline. The timeline shows posts from your friends' microblogs.

![][image-1]

When someone you're following publishes a new post, Micro.blog displays it in the timeline. Micro.blog does some minor processing on the post HTML, striping out HTML tags or JavaScript that aren't appropriate for the timeline. Photos are displayed inline for short posts, and longer posts with titles are linked back to the author's web site.

**How feeds work**

A single account on Micro.blog can have one or more feeds. Unlike a traditional RSS reader where adding feeds controls which blogs you're reading, adding feeds to your account on Micro.blog controls where _your own posts_ come from. (There's a separate interface for following other blogs.)

When a new post appears in these feeds, the post is added to the timeline. Usually there is just one feed: the user’s microblog. If the user writes longer posts at a different blog, or they want to connect bookmarks or other extra posts into the timeline, they can add those feeds to their account too.

The following screenshot shows the Edit Feeds screen. When your blog is hosted on Micro.blog, the feed for your blog is added to this screen automatically:

![][image-2]

This screen also controls which feeds cross-post to other platforms like Twitter or Mastodon. When Micro.blog sees a new post in your feed, it adds it to the Micro.blog timeline and also cross-posts it those platforms that are enabled.

Inside the feed are your recent posts in JSON or XML. Here's an example of what the latest post might look like in JSON:

	{
	  "id": "http://manton.micro.blog/2020/01/11/starting-to-get.html",  
	  "content_html": "<p>Starting to get excited for IndieWebCamp Austin next month! If you&rsquo;re interested in an open alternative to the big silos, I hope you&rsquo;ll join us. <a href=\"https://2020.indieweb.org/austin\">You can register</a> for $10.</p>\n",
	  "date_published": "2020-01-11T13:56:56-06:00",
	  "url": "https://www.manton.org/2020/01/11/starting-to-get.html"
	}

Micro.blog checks your feed for new posts as soon as the post is published, or every few minutes for blogs hosted outside of Micro.blog. (Part 5 covers how we can speed up downloading new posts.) When Micro.blog finds the new post, it adds it to the timeline so everyone following you can see it:

![][image-3]

**Timeline display rules**

Micro.blog follows a few rules when processing your RSS or JSON Feed into microblog posts to show in the timeline:

* If the post has no title and is 300 characters or less, the text is shown directly in the Micro.blog timeline.
* If the post has no title and is _over_ 300 characters, the text is truncated with a link back to the full post on your site.
* If the post includes a block quote, the limit is raised to 600 characters.
* If there's a title and it looks like a date or number, Micro.blog ignores it, as if there were no title. It then tries to show the text in the timeline.
* If there's a title but the entire post text is actually just a photo, it uses the title but also shows the photo inline. If there is a title, text, and photo, only the title is shown and linked back to your site.

For any other kind of post with a title, the title is shown in the timeline with a link back to the full post on your web site. Micro.blog displays your domain name when it needs to append a link to your post.

Micro.blog counts characters for the text version of your post, excluding the extra characters used in any HTML tags.

Sometimes we hear the feedback that Micro.blog shouldn't be so picky about how it treats short microblog posts compared to longer posts with a title. Why not just show as much as possible in the timeline, and truncate as necessary? Why not allow a summary of a post to be used instead of the full post?

But the reason is that Micro.blog is optimized for microblog posts. One of the things that makes it different than a traditional RSS reader is that Micro.blog is designed to encourage short posts. It's designed to provide the best, Twitter-like experience for short posts so that more people embrace indie microblogging.

By having some rules about what a microblog post is, and making it easy to follow those rules in a Micro.blog-hosted blog, it will slowly start to change how people approach microblogging on their own site. If we didn't do anything special for microblog posts, nothing on the web would change, and microblogging would remain a feature of closed platforms only.

Part 4 includes more details about why indie microblogs use HTML for posts. Support for HTML tags is an important part of making Micro.blog feel like an extension of the open web instead of a replacement for it.

[1]:	https://www.joelonsoftware.com/2018/01/12/birdcage-liners/

[image-1]:	https://book.micro.blog/uploads/2020/5fc0025966.png
[image-2]:	https://book.micro.blog/uploads/2020/f7e6a1a29d.png
[image-3]:	https://book.micro.blog/uploads/2020/8264cb94dc.png
## Part of the web

_“Micro.blog is not an alternative silo: instead, it’s what you build when you believe that the web itself is the great social network.” — [Brent Simmons][1]_

I often look back at this quote from Brent to help guide me as I evaluate the direction of Micro.blog. It takes the message from the Indie Microblogging Kickstarter video and distills into something concise and memorable. And it's a reminder that we must think beyond a single, silo-like platform.

If Micro.blog only included posts from user accounts registered on Micro.blog — requiring every user to set up a feed for their blog — it would be useful but limited by how many people will ever sign up on Micro.blog. It would fall short of the goal of connecting more of the web in an open way.

To expand beyond registered accounts, Micro.blog also lets users follow blogs and Mastodon accounts, even if the author of those posts is not on Micro.blog. In this way, Micro.blog acts more like a traditional RSS reader, where you can add a blog feed to follow posts from the author of that blog.

But the UI for Micro.blog is inspired by Twitter, not traditional feed readers. Instead of adding feed URLs to follow, Micro.blog is designed around adding "usernames" to follow.

### Usernames on Micro.blog

Micro.blog has 3 distinct styles of usernames to make the platform more compatible with other services:

* Micro.blog usernames, e.g. **@you**. These are simple usernames for @-mentioning someone else in the Micro.blog community.
* Mastodon usernames, e.g. **@you@yourdomain.com**. When you search Micro.blog for these usernames, Micro.blog will look for the user in another federated Mastodon instance so that you can follow them.
* IndieWeb-friendly domain names, e.g. **@yourdomain.com**. This is where I always thought we'd go for more distributed "the web is the social network" interactions. Replying to one of these usernames will send a Webmention to that user's external web site.

I'm `@manton` on Micro.blog, my blog is `manton.org`, and because Micro.blog-hosted blogs support the ActivityPub API that Mastodon uses, you can follow me from Mastodon by using `@manton@manton.org`.

### Following domain names

These special domain name usernames is where I think we can bring more social network-like interactions to the full web.

Here's an example. In a post on Micro.blog, you can @-mention someone's blog by including @domain.com in the post, using their domain name. If that blogger's site supports Webmention, Micro.blog will send your mention to their blog, where it could be included as a comment.

You can also follow blogs in the Micro.blog timeline, even if the blogger hasn't yet registered on Micro.blog. On the web, click Discover, then click the search icon, and enter their domain name. Micro.blog will auto-discover their JSON or RSS feed, letting you follow their blog just as you would follow any Micro.blog user.

![][image-1]

This feature is designed for blogs with a custom domain name. It assumes one blog, one user, one domain name, so it doesn't work to follow specific feed URLs yet. You'll still want a traditional RSS reader for sites that have multiple feeds.

It's particularly well-suited to platforms like Tumblr where everyone gets a hostname in the format `username.tumblr.com` by default. You can follow any Tumblr user on Micro.blog by entering their `username.tumblr.com` hostname in Micro.blog's search field. Micro.blog finds their RSS feed and includes their posts, including photos, directly in the timeline.

[1]:	https://inessential.com/2018/02/01/why_micro_blog_is_not_another_app_net

[image-1]:	https://book.micro.blog/uploads/2019/903d5b56f9.png
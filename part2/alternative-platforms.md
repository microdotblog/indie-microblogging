## Alternative platforms

In addition to WordPress and Micro.blog itself, here are some other options for microblog hosting.

### Tumblr

Tumblr and Micro.blog share many principles. Everyone gets a hostname, which can be upgraded with your own custom domain name, and there are many built-in designs for your blog.

Tumble RSS feeds include a post title even for post formats such as Quote or Photo that don’t actually have a title. Instead of leaving the title blank, Tumblr uses the first words of the blog post as the title in the RSS feed, truncated and then followed with an ellipsis. Micro.blog has special support for recognizing these synthetic titles and ignoring them.

To participate in the Micro.blog community, Tumblr users can create an account and add their Tumblr RSS feed to Micro.blog under Account → Edit Feeds & Cross-posting. Tumblr RSS feeds have the form:

	yourusername.tumblr.com/rss

But Micro.blog users can also follow Tumblr blogs directly, even if the Tumblr users haven't yet registered on Micro.blog, by searching for their Tumblr hostname. Tumblr photo blogs look great in the Micro.blog timeline:

![](https://book.micro.blog/uploads/2020/8570bf0d3a.png)

### Ghost

Like WordPress, Ghost is an open source project that you can either self-host yourself or pay [Ghost.org](https://ghost.org) to host for you. By default Ghost uses the placeholder text "(untitled)" for blank title fields, so it's not well-suited for microblogging. You can add custom CSS to hide these titles in your blog's design.

[Mike Haynes has documented](https://mikehayn.es/displaying-posts-without-titles-in-ghost-rss-feeds/) some additional work-arounds to Ghost’s default “(untitled)” behavior:

> Using the custom RSS routing was tough for me to wrap my head around but I finally cracked it and, if you've struggled with the same, I want to share how I split out the post types into their own feeds and got them to display correctly

Unfortunately Ghost chose to build a custom API instead of adopting a standard blog posting API. You can post to Ghost from some native apps such as Ulysses, but not from Micro.blog.

### Blot

Blot is a service that takes text files on Dropbox and converts them into a web site. It's a convenient way to create photo albums and other sites that you might want to manage from files you have on your computer. Blot creates an RSS feed that works in Micro.blog.

### Mastodon

Mastodon is a federated social network that we cover in much greater depth in Part 5. You can add the RSS feed for your Mastodon account to Micro.blog for those posts to show up in the timeline. You can also follow Mastodon users directly in Micro.blog.

### Jekyll

Jekyll is a static-site generator that is well-supported by GitHub. You write new blog post as text files with Markdown. After checking the text files in to a repository for your blog, GitHub Pages automatically generates the HTML and serves your blog for free. It also includes support for custom domain names.

If you want to get started with a blank single-page web site, the IndieWeb also has the [blank-gh-site](https://github.com/indieweb/blank-gh-site) repository that you can clone.

### The challenge with static sites

Before WordPress took off, Movable Type was one of the most popular blogging platforms. It provided a web interface for managing posts but then generated static HTML pages that were served directly without needing a server-side scripting language. Serving static HTML pages is fast and portable to many different platforms with few dependencies.

Today's static-site generators take out the web interface and focus purely on building a series of HTML pages based on source files, usually written in Markdown. They have the performance advantages of being served directly by Apache or Nginx, but require running a script on your own computer instead of posting with other apps via an API. This makes posting from multiple computers or mobile devices more difficult.

Micropub is an IndieWeb posting API that we cover in part 3. There are [open source projects](https://indieweb.org/static_site) that attempt to work around the limitation of static-site generators by providing a Micropub API proxy. This makes API endpoints available for apps such as Micro.blog to call to, and then turns those requests into files that are checked in to GitHub.

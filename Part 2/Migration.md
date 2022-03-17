## Migration

_“The magician takes the ordinary something and makes it into something extraordinary. But you wouldn’t clap yet, because making something disappear isn’t enough. You have to bring it back.” — The Prestige_

Micro.blog can import from WordPress, Medium, Tumblr, and Ghost. To upload a file from one of those platforms, go to Micro.blog on the web and click Posts → “…” → Import.

When importing, Micro.blog will create new blog posts from the posts in the import file. If there are any `img` references in the HTML for those posts, Micro.blog will also attempt to download those images and store them on Micro.blog. It will then update the HTML to use the new URL for the image on Micro.blog.

If the URLs for your previous blog posts are different than the URLs on Micro.blog, Micro.blog will keep a record of the old URLs and automatically set up redirects for them, so that no links will break. These redirects will become active once you've moved your domain name to point to Micro.blog.

If you're moving from a blog system not supported by Micro.blog, you may be able to automate moving the posts over. [Kahlil Lechelt has created a script][1] that will work with static-site generators such as Jekyll or Hugo by importing from a folder of Markdown files.

### Mirroring back to WordPress

Some people prefer to use Micro.blog because it's easier to post to, but still want those microblog posts to go back to their main WordPress blog. The [Feed Importer plugin][2] for WordPress by Michael Lichwa will load your microblog's RSS feed, looking for new posts and copying them over to your WordPress blog.

RSS feeds on Micro.blog contain the most recent 25 posts, not all posts. Feed Importer is best suited for ongoing mirroring of posts to WordPress rather than importing all previous posts.

---- 

If you are starting a new microblog hosted on Micro.blog in addition to maintaining a full blog outside of Micro.blog, you might want to integrate the microblog posts into your main blog.

You can include your Micro.blog-hosted microblog posts in the sidebar of your main web site with our JavaScript include called Sidebar.js. In your main site's HTML template, add this JavaScript wherever you want to include the microblog posts:

	<script type="text/javascript" src="https://micro.blog/sidebar.js?username=your_username"></script>

If you use WordPress, add this JavaScript in a "Text" widget available from the WordPress admin dashboard. Remember to replace `your_username` with your Micro.blog username.

The HTML for your microblog posts can be styled with CSS. The CSS class names include: `microblog_timeline` (for wrapping all the posts), `microblog_post` (around a single post), `microblog_text` (for the post HTML), and `microblog_time` (for when the post was created).

Sidebar.js defaults to including the most recent 10 posts. To show more, you can add `&count=25` at the end of the URL.

---- 

Micro.blog has very little lock-in by design. Basing everything on blogs makes it easy to move away if you need to. It also means you can effectively ignore most of Micro.blog and still get value out of blogging regularly and participating in the larger IndieWeb community of connected blogs with cross-site replies.

You can export your posts from Micro.blog in WordPress format or Blog Archive Format, which is covered more in Part 3.

[1]:	https://ka.micro.blog/2019/01/01/microblog-import-script.html
[2]:	https://wordpress.org/plugins/feed-importer-micro-blog/
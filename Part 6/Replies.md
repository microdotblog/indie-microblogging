## Replies

_“As you may know, @replies were not originally part of Twitter. They were embraced by the community first, and then we built them into the system.” — [Evan Williams][1], 2008 post about Twitter formalizing replies_

In 2016 around the 10-year anniversary of Twitter's launch, [Faruk Ateş wrote a post][2] that gives a sense of the major changes Twitter had gone through, most of which were difficult to fully understand at the time. On the change with @-replies:

> The second thing is that when they started hiding @-replies to people you don’t follow, they stripped the user experience of a vital ingredient for civility: peer transparency. The tone of discourse changed much for the worse over time, following that new behavior of the timeline. Before the rollout, all your friends would see if you behaved like a jerk to someone; after the rollout that was no longer the case. It removed the natural consequences of bad behavior, thereby encouraging people to reap the benefits of such bad behavior much more frequently.

Replies on Micro.blog go back to that earlier Twitter design. By default, when you reply to someone's post, all your followers see the reply even if they aren't following the person you are replying to. If you are following people who reply _a lot_, you can disable that behavior with a setting:

![][image-1]

Showing all replies by default helps your followers discover new people. Along with the Discover section, it's one of the best places to find new people. Seeing bits of other conversations also sets expectations for what the community is like.

Replies can come in several forms. At its simplest, you click "Reply" in Micro.blog and write something short:

![][image-2]

The reply is stored on Micro.blog and added to the timeline, threaded into the conversation. Micro.blog includes the reply in the timeline and Mentions section for any user referenced in the post.

Because Micro.blog is based on blogs, replying and mentioning other users does not work the same way as other social networks you may be used to. We've tried to build a system that is flexible enough to work with Micro.blog-hosted sites and external blogs.

There are several rules for processing replies and mentions:

* When replying to a post that is on an external blog, Micro.blog will attempt to send a Webmention to that blog post.
* If you post to your Micro.blog-hosted blog and include `@username` somewhere in the post, Micro.blog automatically converts that into a Markdown link to the Micro.blog user. Micro.blog also includes that mention in the user's timeline and Mentions section.
* For blogs hosted externally to Micro.blog, such as with WordPress, you are responsible for linking usernames for Micro.blog users you want to mention. Just including @username without a link will have no effect. It should be something like `<a href="https://micro.blog/username">@username</a>` to indicate to Micro.blog that a specific user should be notified. Micro.blog does not automatically link any text in external blog posts. (By adding links yourself, posts will show up correctly not just on Micro.blog but also on your web site and in feed readers.)
* For an external blog post that is a reply to a specific Micro.blog post, the external blog can send a Webmention to Micro.blog. If the sending blog is associated with a Micro.blog user, that post will be copied to Micro.blog as a reply and threaded into the conversation.

Remember that microblog posts use HTML. Micro.blog doesn't attempt to auto-linking usernames _after_ a blog post is published. We don't want to build a new platform that avoids HTML. Instead, it's about making the web itself better. A microblog post on the web should be readable in a web browser.

---- 

When I was first developing Micro.blog, I made a choice that quick replies in the timeline should be stored separately from regular blog posts. I thought that most people wouldn't want replies mixed in with their blog posts at their own domain name. I also liked that replies were simple, usually short and without images, because it makes the timeline much more readable.

But this design poked a hole in one of the most important goals of Micro.blog: owning your own content by having it at your own domain name. If someone wanted more control over their replies, they would need to use an external blog like WordPress, even though Micro.blog had great support for Webmention and cross-site replies.

In early 2020 we finally fixed this limitation. Storing replies outside of your Micro.blog-hosted blog, even if you could export them or move to another IndieWeb-friendly platform, was too silo-like for the mission of Micro.blog.

Now you can have your replies on your own blog, with reply permalink URLs at your own domain name. You can enable this on the Account screen. The popup menu will include any blog that's hosted on Micro.blog, so you could even create a separate microblog just for replies:

![][image-3]

Replies get a new `reply` post type in Hugo, which is used under-the-hood for your microblog. This means they won't show up in your default feeds or home page, although you can create a custom theme to change that.

Micro.blog adds a few Hugo parameters that can be used for reply HTML templates:

* `.Params.reply_to_url`: The URL for the post you are replying to.
* `.Params.reply_to_hostname`: Just the hostname part of the reply-to URL.
* `.Params.reply_to_username`: The username for the Micro.blog user you're replying to.
* `.Params.reply_to_avatar`: The URL for the Micro.blog user's profile photo.

Replies on your blog also get a special HTML template that includes the blog or Micro.blog username for the person you're replying to:

![][image-4]

This is common practice in the IndieWeb community.

---- 

You may want to link from your blog post to the conversation around that post on Micro.blog. When Micro.blog reads your feed, it creates a record for your post in the timeline. If you’re hosting on Micro.blog, you can install Sven Dahlstrand’s plug-in [Conversation on Micro.blog][3] to add a link automatically to your blog posts.

If you’re hosting elsewhere or want more control, Conversation.js also includes the URL for your post on Micro.blog in JSON Feed’s `home_page_url` field.

```json
GET https://micro.blog/conversation.js?url=https://example.com/your-blog-post.html&format=jsonfeed
```

Response:

```json
{
  "version": "https://jsonfeed.org/version/1",
  "title": "Conversation",
  "home_page_url": "https://micro.blog/manton/13029114",
  ...
}
```

You can use JavaScript or a server-side script to retrieve this JSON Feed and then use the URL in `home_page_url` for linking from your blog to the conversation on Micro.blog.

[1]:	https://blog.twitter.com/en_us/a/2008/how-replies-work-on-twitter-and-how-they-might
[2]:	https://productmatters.design/the-ghosts-of-twitter-past-present-and-future-a02827120927
[3]:	https://github.com/svendahlstrand/plugin-conversation-on-mb

[image-1]:	https://book.micro.blog/uploads/2020/85ccbd2d96.png
[image-2]:	https://book.micro.blog/uploads/2020/d819d19e4a.png
[image-3]:	https://book.micro.blog/uploads/2020/0ea6744e98.png
[image-4]:	https://book.micro.blog/uploads/2020/fd4796c73d.png
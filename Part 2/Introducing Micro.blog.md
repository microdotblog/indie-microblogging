## Introducing Micro.blog

Micro.blog is built on this foundation of JSON and RSS feeds, the importance of content ownership through domain names, and a new UI inspired by social networks.

Because of the technical hurdles of self-hosting your own blog, if we want to encourage more people to blog, it has to be much easier. Centralized platforms allow for that ease of use — nothing to install or maintain, with all the right defaults that use open standards.

I’ve always thought of Micro.blog as glue. It’s a thin layer on top of blogs that provides a Twitter-like timeline experience, adding conversations and user discovery. It’s a social network from the idea that more people should be blogging and sites should talk to each other.

Early on in the development of Micro.blog, I realized that building a social network on top of RSS feeds wasn't enough. Micro.blog had to be both a social network _and_ a blog hosting platform. I became committed to making Micro.blog the best place to write a blog.

Micro.blog publishing is based on Hugo under the hood. On top of that foundation, it adds posting from the web or from iOS, default themes, and other customizations for microblogging. Micro.blog is one of the easiest ways to get started with a blog.

![][image-1]

When you publish a new post, Micro.blog takes the following steps:

1. The new post is saved to a database in Micro.blog for your account.
2. Your posts are written to files that Hugo can process. Micro.blog first runs the latest posts through Hugo so that the new post shows up as quickly as possible, then processes the rest of your posts.
3. Your site is published to either `username.micro.blog` or your own custom domain name. This includes updating the feeds.
4. Micro.blog reads the feed and notices the new post, adding it to the Micro.blog timeline for anyone who follows you.

The goal is for this to feel like a single step, just as if you were posting a tweet, but in reality Micro.blog separates out the blog publishing from the work of building the timeline. It is essentially 2 systems, working together, which means external blogs can also be plugged in to the timeline.

![][image-2]

---- 

Because Micro.blog is a transitional platform, a bridge between centralized services and more distributed platforms, it needed many parts of a traditional API. Micro.blog’s JSON API allows for signing in, retrieving posts in the timeline, replying to posts, bookmarking posts, and more.

The official Micro.blog apps and third-party apps use the Micro.blog JSON API. Most present a timeline interface, with separate sections for mentions, managing posts, and other features.

![][image-3] ![][image-4]

Some of the popular third-party apps written specifically for Micro.blog include Gluon, Icro, and Dialog. Those apps and more are covered in the blogging workflow chapter.

Alternatively, third-party apps can instead use IndieWeb APIs such as Micropub. This will make these apps compatible with Micro.blog, but also potentially compatible with other platforms.

When Micro.blog was first launched, the IndieWeb APIs could not yet handle everything that Micro.blog needed. Over the years, as APIs such as Micropub have expanded, more and more functionality can be built on those standards.

Eventually, all new apps should be built with IndieWeb standards and not use the original Micro.blog JSON API. For that reason, most proprietary parts of the Micro.blog API won’t be covered in detail in this book, although they are still documented on the [Micro.blog help site][1]. Micropub is covered in detail in part 3.

---- 

Micro.blog is not the only choice for microblogging. A core principle of Micro.blog is that you can bring an existing blog hosted somewhere else, such as using WordPress, and that the Micro.blog platform works nicely with the rest of the web.

[1]:	https://help.micro.blog/

[image-1]:	https://book.micro.blog/uploads/2020/64d82327cd.png
[image-2]:	https://book.micro.blog/uploads/2020/5e218ee372.png
[image-3]:	https://book.micro.blog/uploads/2020/ed9043efb2.png
[image-4]:	https://book.micro.blog/uploads/2020/87ba0b1e20.png
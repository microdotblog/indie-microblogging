## Blogging workflow

_“kottke.org isn’t so much a thing I’m making but a process I’m going through. A journey. A journey towards knowledge, discovery, empathy, connection, and a better way of seeing the world. Along the way, I’ve found myself and all of you.” — [Jason Kottke][1]_

There’s no perfect blogging workflow that will work for everyone, all the time. There’s no single process, or even one goal, because everyone gets something different out of blogging. The strength of open standards is being able to pick the best tool for the job, rather than be locked into only one interface.

I personally use a variety of different apps depending on what I'm trying to do:

* If I'm posting a quick microblog post and know what I want to say, I type it into the Micro.blog app for Mac.
* If I'm posting a single photo, I use Micro.blog on my iPhone.
* If I'm posting a bunch of photos [like this post from Toronto][2], I use [Sunlit][3] to write a little something for each day.
* If I'm writing a longer post and have it all in my head, so I know I will post it very soon, I type it directly into MarsEdit and publish it to Micro.blog from there.
* If I'm writing a post and I'm not totally sure where it's going, or when I'm going to post it, I type it into Ulysses. This is the majority of my posts. Then I copy and paste it into Micro.blog.

And this only scratches the surface. There's Wavelength for podcasts, Epilogue for books, and some people prefer apps like Gluon, Quill, or Lillihub. This is why we link third-party apps from the posting screen in Micro.blog.

---- 

Platforms that only allow a single, official app for browsing and posting — like Twitter and Instagram, and increasingly Reddit too — usually have that restriction because their business is showing ads. By controlling the timeline experience, they can have precise stats on active users and they can insert ads directly into the timeline, which would be more difficult to enforce with third-party apps.

Blogs have no such restriction. Blogs are focused around your identity and your posts, freeing you to use whatever apps for posting fit your needs the best.

---- 

Third-party apps for Micro.blog bring their own UI that might be better suited for certain workflows. They also can expand Micro.blog to more platforms, such as the early Android app Dialog designed by [Mike Haynes][4], available before Micro.blog had an official app for Android.

**Icro for iOS.** Icro from developer [Martin Hartl][5] is well-designed, fast, and takes a different approach to some features compared to the official Micro.blog app. In a few ways, it’s _better_ than the app I built. This is exactly what I hoped for. We wanted an official app so that there’s a default to get started, but there should be other great options for Micro.blog users to choose from.

![][image-1]

**Gluon for iOS and Android.** Gluon was the first cross-platform mobile app for Micro.blog. It supports multiple Micro.blog accounts and features like local drafts, muting, and themes. Developer [Vincent Ritter][6] has documented the development process [on his blog][7] through several iterations of the app.

![][image-2]

**Mimi Uploader for iOS.** [Sam Grover][8] built a new iOS app that is all about batch uploading photos to your blog. I love it because it takes a specific need and provides a really polished workflow just for that. After the upload finishes, you can copy Markdown or HTML to reference all the photos for easy pasting into another app or Micro.blog on the web.

![][image-3]

**MarsEdit for macOS.** Long-time Mac developer [Daniel Jalkut][9] has continued to improve his app MarsEdit through the years to support multiple blogging platforms. Because it can use the MetaWeblog API that Micro.blog supports, you can post directly to Micro.blog from MarsEdit.

![][image-4]

**Drafts for iOS.** Drafts by [Greg Pierce][10] of Agile Tortoise is a unique app designed to make it easy to write a quick text note and send it to other apps and services. Drafts comes with a built-in "Send to Micro.blog" action that will open the Micro.blog app on iOS. There is also an [actions directory][11] that includes additional actions from Drafts users, including a "Post to Micro.blog" that will publish a post directly to Micro.blog from within Drafts. When you use that action, it will prompt for an app token you can generate in your account on Micro.blog.

![][image-5]

**iA Writer for iOS and macOS.** [iA Writer][12] can publish to Micro.blog-hosted blogs. It uses the Micropub API, which is Micro.blog's native API for posting.

![][image-6]

**Ulysses for iOS and macOS.** Ulysses can post to Micro.blog from iOS and macOS. Ulysses supports publishing to a few blog systems, and you’ll configure them in the Preferences window on the Mac. You can start your longer drafts in Ulysses and then publish out to Micro.blog as needed.

![][image-7]

** Lillihub for the web.** [Lillihub][13] is a web-based app by [Loura][14] with a unique user experience, built just for Micro.blog. It has prominent links to conversations, bookmarks, and even special support for Micro.blog’s bookshelves feature.

![][image-8]

---- 

One of the things I'm most proud of with Micro.blog is that the API supports standards so you can use a variety of different apps for posting. There are so many different types of blogs out there, there shouldn't just be one way to post.

[1]:	https://kottke.org/18/03/twenty
[2]:	https://www.manton.org/2019/10/26/toronto-photos.html
[3]:	https://sunlit.io/
[4]:	https://micro.blog/mikehaynes
[5]:	https://micro.blog/hartlco
[6]:	https://micro.blog/vincent
[7]:	https://vincentritter.com/projects/gluon-for-micro-blog/
[8]:	http://micro.blog/samgrover/8104031
[9]:	http://micro.blog/danielpunkass
[10]:	http://micro.blog/agiletortoise
[11]:	https://actions.getdrafts.com/
[12]:	https://ia.net/writer
[13]:	https://lillihub.com
[14]:	https://heyloura.com

[image-1]:	https://book.micro.blog/uploads/2020/84e5773d18.png
[image-2]:	https://book.micro.blog/uploads/2020/7939f0d1cb.png
[image-3]:	https://book.micro.blog/uploads/2020/4075f8370a.png
[image-4]:	https://book.micro.blog/uploads/2020/bf06025a04.png
[image-5]:	https://book.micro.blog/uploads/2020/8a2054d07c.png
[image-6]:	https://book.micro.blog/uploads/2022/c037eee590.png
[image-7]:	https://book.micro.blog/uploads/2022/fa55be37d2.png
[image-8]:	https://book.micro.blog/uploads/2023/lillihub-screenshot.png
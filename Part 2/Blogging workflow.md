## Blogging workflow

_“kottke.org isn’t so much a thing I’m making but a process I’m going through. A journey. A journey towards knowledge, discovery, empathy, connection, and a better way of seeing the world. Along the way, I’ve found myself and all of you.” — [Jason Kottke][1]_

There’s no perfect blogging workflow that will work for everyone, all the time. There’s no single process, or even one goal, because everyone gets something different out of blogging. The strength of open standards is being able to pick the best tool for the job, rather than be locked into only one interface.

I personally use a variety of different apps depending on what I'm trying to do:

* If I'm posting a quick microblog post and know what I want to say, I type it into the Micro.blog app for Mac.
* If I'm posting a single photo, I use Micro.blog on my iPhone.
* If I'm posting a bunch of photos [like this post from Toronto][2], I use [Sunlit][3] to write a little something for each day.
* If I'm writing a longer post and have it all in my head, so I know I will post it very soon, I type it directly into MarsEdit and publish it to Micro.blog from there.
* If I'm writing a post and I'm not totally sure where it's going, or when I'm going to post it, I type it into Ulysses. This is the majority of my posts. Then I copy and paste it into Micro.blog.

And this only scratches the surface. There's Wavelength for podcasts, and some people prefer apps like Icro, Gluon, Dialog, or Quill. This is why we link third-party apps from the posting screen in Micro.blog.

One of the things I'm most proud of with Micro.blog is that the API supports standards so you can use a variety of different apps for posting. There are so many different types of blogs out there, there shouldn't just be one way to post.

---- 

Third-party apps for Micro.blog bring their own UI that might be better suited for certain workflows.

**Icro for iOS.** Icro is well-designed, fast, and takes a different approach to some features compared to the official Micro.blog app. In a few ways, it’s _better_ than the app I built. This is exactly what I hoped for. We wanted an official app so that there’s a default to get started, but there should be other great options for Micro.blog users to choose from.

![][image-1]

Thanks to developer [Martin Hartl][4] for building Icro and being part of the Micro.blog community. You can [download it for free from the App Store here][5].

**Dialog for Android.** There is no official Android app for Micro.blog, so third-party options are critical. [Mike Haynes][6] designed an Android app that can post to Micro.blog, browse the timeline, and reply to other posts while feeling more at home on Android than the web-based version of Micro.blog.

**Gluon for iOS and Android.** Gluon is the first cross-platform mobile app for Micro.blog. It supports multiple Micro.blog accounts and features like local drafts, muting, and themes. Developer [Vincent Ritter][7] has documented the development process [on his blog][8] through several iterations of the app.

![][image-2]

**Mimi Uploader for iOS.** [Sam Grover][9] built a new iOS app that is all about batch uploading photos to your blog. I love it because it takes a specific need and provides a really polished workflow just for that. After the upload finishes, you can copy Markdown or HTML to reference all the photos for easy pasting into another app or Micro.blog on the web.

![][image-3]

**MarsEdit for macOS.** Long-time Mac developer [Daniel Jalkut][10] has continued to improve his app MarsEdit through the years to support multiple blogging platforms. Because it can use the MetaWeblog API that Micro.blog supports, you can post directly to Micro.blog from MarsEdit.

![][image-4]

Remember that there are no passwords on Micro.blog. To sign in with an app like MarsEdit, use your Micro.blog username and an "app token" for the password. Your account comes with a default token for MarsEdit, but you can generate a new one whenever you want. Click on Account to view or manage your app tokens.

Start in MarsEdit by creating a new weblog. When prompted for the URL, enter your-username.micro.blog. This is where your published microblog lives, so MarsEdit will need to look there to automatically discover the XML-RPC endpoint.

Posting from MarsEdit supports microblog posts (leave the title blank), full posts with a title, and uploading photos. Limited HTML is also allowed and won’t be escaped

Because Micro.blog uses Markdown, we recommend keeping MarsEdit in "Plain Text Mode" instead of "Rich Text". You can switch this under the Post menu in MarsEdit.

**Drafts for iOS.** Drafts by [Greg Pierce][11] of Agile Tortoise is a unique app designed to make it easy to write a quick text note and send it to other apps and services. Drafts comes with a built-in "Send to Micro.blog" action that will open the Micro.blog app on iOS. There is also an [actions directory][12] that includes additional actions from Drafts users, including a "Post to Micro.blog" that will publish a post directly to Micro.blog from within Drafts. When you use that action, it will prompt for an app token you can generate in your account on Micro.blog.

![][image-5]

**iA Writer for iOS and macOS.** [iA Writer][13] can publish to Micro.blog-hosted blogs. It uses the Micropub API, which is Micro.blog's native API for posting.

To get started in iA Writer on iOS, go back to the first screen in the app and tap the settings icon → Accounts → Add Account → Micropub. You'll be prompted to approve iA Writer in Micro.blog. If you're not signed in yet in mobile Safari, you can sign in first and then try again:

![][image-6]

In a text document, tap the share icon → Publish → New Draft on Micro.blog:

![][image-7]

When you publish a post, it's saved on Micro.blog as a draft, and iA Writer opens a preview of the draft on Micro.blog. From there, you can tap to publish it.

**Ulysses for iOS and macOS.** Ulysses can post to Micro.blog from iOS and macOS, but we’ll focus on macOS here. Ulysses supports publishing to a few blog systems, and you’ll configure them in the Preferences window on the Mac. First click the “+” button under Accounts.

![][image-8]

You’ll be prompted to enter an “app token” for your Micro.blog account. This is like an app-specific password that lets Ulysses sign in to your Micro.blog account and publish to your blog. You can generate a new token for Ulysses in Micro.blog on the web under Account → “App tokens”. The “Micro.blog account” link in the Ulysses window will also take you right there.

![][image-9]

If you have multiple hosted blogs in Micro.blog, Ulysses will prompt for which blog you’d like to post to. Micro.blog supports multiple blogs so you can have an extra blog for a podcast, or photo blog at a different domain name, or just a test blog to try out theme changes without affecting your main site.

![][image-10]

When you’re ready to publish a blog post, click the share icon in the upper-right corner of Ulysses and select Publishing. Ulysses will preview the post and then when you click Publish, it will prompt for setting a title, categories, and whether to save the post to Micro.blog as a draft or make it live on your site.

![][image-11]

[1]:	https://kottke.org/18/03/twenty
[2]:	https://www.manton.org/2019/10/26/toronto-photos.html
[3]:	https://sunlit.io/
[4]:	https://micro.blog/hartlco
[5]:	https://itunes.apple.com/us/app/icro/id1375296597?ls=1&mt=8
[6]:	https://micro.blog/mikehaynes
[7]:	https://micro.blog/vincent
[8]:	https://vincentritter.com/projects/gluon-for-micro-blog/
[9]:	http://micro.blog/samgrover/8104031
[10]:	http://micro.blog/danielpunkass
[11]:	http://micro.blog/agiletortoise
[12]:	https://actions.getdrafts.com/
[13]:	https://ia.net/writer

[image-1]:	https://book.micro.blog/uploads/2020/84e5773d18.png
[image-2]:	https://book.micro.blog/uploads/2020/7939f0d1cb.png
[image-3]:	https://book.micro.blog/uploads/2020/4075f8370a.png
[image-4]:	https://book.micro.blog/uploads/2020/bf06025a04.png
[image-5]:	https://book.micro.blog/uploads/2020/8a2054d07c.png
[image-6]:	https://book.micro.blog/uploads/2022/c037eee590.png
[image-7]:	https://book.micro.blog/uploads/2022/09cc3d6f5d.png
[image-8]:	https://book.micro.blog/uploads/2022/fa55be37d2.png
[image-9]:	https://book.micro.blog/uploads/2022/19badf1cd7.png
[image-10]:	https://book.micro.blog/uploads/2022/fe6a9e2d93.png
[image-11]:	https://book.micro.blog/uploads/2022/7356ecf506.png
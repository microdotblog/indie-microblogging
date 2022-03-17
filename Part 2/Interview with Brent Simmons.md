## Interview with Brent Simmons

A bunch of people contributed to the development of JSON Feed, suggesting the structure of fields and the wording in the specification, but along the way it was Brent Simmons who guided the process. He drew from his experience building the feed reader NetNewsWire and having had to deal with all the feeds out in the real world, combined with a sense that to push back against centralization and silos we need a modern approach to feeds.

For this book, I wanted to go back farther in time, to talk to Brent about his early work with RSS, XML-RPC, and the UI of feed readers.

**Manton:** You and I were part of the Mac web server community in the mid-1990s. It was based around the WebSTAR server, originally developed as MacHTTP by Chuck Shotton. I have great memories from that community and wonder if anything stands out to you from those classic Mac OS days before Apple acquired NeXT?

**Brent:** Those days were *amazing*. I was relatively young, in my mid-20s, and the web was going off like fireworks — it was this thing that kept exploding, over and over, with new shapes and colors, and great big bangs, seemingly every day. I wanted to be a part of that.

At the same time, I also wanted to write software for Macs, because I loved them. I believed then — and believe now — that the Mac user interface is one of the great intellectual and artist achievements of my lifetime.

And then I found that there this was great community of Mac developers working on web software — WebSTAR was one of the biggest, but it was definitely not alone. When I joined that community, it felt like I had finally come home. Home for the first time.

I can’t help but notice that the themes of my career were there from the beginning: the web, Mac apps, and community.

**Manton:** You worked with Dave Winer at Userland Software from 1996 to 2002, a very influential time for early blogging and standards. What were your expectations when you joined Userland and what were the first projects you worked on?

**Brent:** That was my very first software job. I loved UserLand Frontier so much, and had become a member of the community — making things, sharing things, helping other people. When I was offered a job to actually work on Frontier I didn’t even have to think about it: it was a dream job.

I don’t recall what I worked on at first, but pretty soon the entire company was working on porting Frontier to Windows. I don’t think any of us had any particular love for Windows, but at that time it looked like Apple could fail at any minute, and people weren’t buying Mac apps or investing in companies that made software only for Macs. In order to survive, we needed a Windows version.

Once that was done, though, I started working on Manila, which was one of the very earliest of the hosted blogging systems. The first domain was editthispage.com, and anybody could get a free blog. And tens of thousands of people did.

Manila ran in Frontier running as a server, and we ran everything on Windows NT machines. They were just consumer machines from Dell. Dave had a T1 running to his house, and UserLand paid for one to run to my office in Seattle. Dave had a bunch of machines, and I had a bunch. Just consumer-level Dell machines, which we named Honker (it was fast), SuperHonker (it was faster), Nirvana (really amazingly fast), and so on.

My own blog, inessential.com, started out as a Manila blog. I couldn’t very well work on Manila without also having a blog, I figured.

**Manton:** What was it like working alongside Dave Winer as RSS and XML-RPC were getting off the ground? Could you imagine that these were formats that would still be in widespread use 20 years later?

**Brent:** XML-RPC I understood right away. It was a very simple XML-based data serialization format — very much a precursor to JSON. It also had a spot for a method name, so it was exactly like calling methods, and getting back a result, but over the web. We used this for a ton of things. So easy.

About RSS I was skeptical at first: it took me longer to get it. While I was working on Manila and other business priorities, Dave spent his time working on RSS readers. I respected him tremendously, and always gave him the benefit of the doubt, but I admit that at first I really wanted more of his help with the other things we were doing.

It was not till Radio UserLand shipped — a post-Manila project, written more by Dave and by Jake Savin, not much by me — that I got the hang of RSS. Radio UserLand was also a blogging app, but it was a blogging app that included a browser-based RSS reader. That’s what got me hooked on RSS.

Did I expect these formats would be in use 20 years later? I don’t think I ever thought about it like that, at all. We were all so busy inventing the future that I never really thought about the future.

**Manton:** Userland apps from that era like Manila and Radio Userland were native Mac apps, but the primary interface for blogging was through a web interface. Did you ever feel limited in the types of UIs you could build at the time, or was it only later that you wanted to work on a fully Mac-like interface with MacNewsWire, and then later NetNewsWire and MarsEdit?

**Brent:** It was always my personal dream to work on native Mac apps: I don’t really love doing web UIs. Near the end of my time at UserLand I was working on what we called the Frontier kernel, which was the Mac app itself. The browser-based UI was generated by the Mac app, which included a web server.

But doing native user interfaces was a *lot* more difficult in those days. We were still writing in C to the Macintosh Toolbox APIs. Doing web UIs was, for us, much quicker and easier — and, well, the kinds of things we wanted to do at UserLand were web things anyway.

Nevertheless, I dreamed of making Mac apps with native Mac UI. After leaving UserLand in 2002, that’s what I set out to do — and Cocoa promised to make this *far* easier than it had ever been before. I jumped right in, and I’ve never looked back.

**Manton:** The first version of NetNewsWire had both a reading and posting interface. You then split the posting into its own app MarsEdit, [writing at the time][1] that the File menu in a Mac application is like a statement about what is most important in the app — what type of data the user is working with. File → New could create a new subscription, like in a news reader, or it could create a new blog post:

> But if cmd-N creates a new weblog post instead, then that says that the most important new thing you create in NetNewsWire is a weblog post, which means it’s more a weblog editor than a newsreader. That would have been the wrong direction.

Following this logic with the File menu, the blog editing could never grow into the best interface for blogging unless it was split into its own app:

> The more we thought about it, the more it was obvious that the weblog editor had to be a separate application. In order to improve both NetNewsWire and the weblog editor, we needed to induce mitosis.

Do you ever wonder how the app would've evolved if you had kept reading and posting together in the same app?

**Brent:** The reason NetNewsWire included a blog editor was because Radio UserLand did, and Radio was NetNewsWire’s only competitor at first.

But, more importantly, I believed in the Radio UserLand model: you’d have stuff coming in from the from blogs you follow, and you’d reply to articles and link to them — not just start brand-new topics. The web is a conversation, after all.

(Also think of Usenet and email apps. You read and write in the same app.)

Note that this was before Facebook and Twitter, both of which have proved that people like having their feed of stuff in the same place where they write. Radio UserLand was ahead of its time in that way.

But I couldn’t see how to do that job well in NetNewsWire. Partly because I was younger and less-experienced than I am now — but also because expectations for Mac apps were quite different then.

In those days, Mac apps were all expected to be what we would now call pro apps. That meant they tended to be powerful and necessarily more complex. To smoosh together a full-featured RSS reader with a full-featured blog editor was a mistake, and it would be a mistake today.

What I would do these days — I’ve thought about it a ton — would be to write something that looks more like Twitterrific or Tweetbot. Instead of a three-paned RSS reader, you’d have one pane, a simple timeline with newest articles at the top. It wouldn’t even have read/unread status.

And, critically, you’d be able to post to your blog with a simple UI. It would be a lot like tweeting or posting to Facebook or Instagram, with the modification that you could write long when you want to.

That kind of app wouldn’t have found users in 2005 — people would have complained that it didn’t do x, y, and z, and they needed those things, and in 2005 they would have been right.

But I think that kind of app could fly today. People have learned — maybe in part from iOS — that casual, fun, easy apps are pretty damn cool, even on Macs.

When I restarted work on NetNewsWire some years back, it was the result of a choice: did I want to make an RSS reader that clearly descended from NetNewsWire, or did I want to write this single-timeline/blog-posting thing? It was a close call, but I picked NetNewsWire-style — and I don’t regret it, because I love this style of RSS reader and lots of other people do too.

I can’t help but note that the Micro.blog app is a lot like what I’ve described, and I think it’s marvelous. (I use it every day!)

But the Micro.blog Mac app doesn’t allow for adding RSS feeds from anywhere, because that’s not the point of the app, and so it’s not exactly the thing I imagined. I wish somebody would write that thing! NetNewsWire is open source, and I encourage people to use NetNewsWire code to get started on their own apps. Please do!

[1]:	https://inessential.com/2004/10/05/marsedit_user_interface_notes
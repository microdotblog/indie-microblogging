## Syndication

_“The magic of compatibility between products, that's a big part of what I do this for. All the great stuff is built around agreements between developers to let users move data between the products.” — [Dave Winer][1]_

After a domain name, the most important glue that holds blogging together is the feed. The feed takes all the variety in web sites — custom designs, navigation, URL formats — and strips it away to the essentials: a list of posts and some simple structured data for each post.

Feeds are separate files that exist alongside a blog's home page. Feeds usually contain the same posts as the home page, but stored in XML or JSON format instead of HTML. This allows developers to more easily build apps that can display a list of posts without needing to extract the important fields from the layout of the site.

Feeds make the web more accessible. With the introduction of the first feed reader, it was possible to follow many more blogs. It was much more efficient than manually checking on your favorite sites, wondering if they had posted anything new.

[In a post at the end of 1997][2], Dave Winer wrote about his first experiments that would lead to RSS feeds:

> When I edit the page, it's an outline. I type in items, and render the page from the most recent seven outlines. The whole process is automatic, there's almost no hand-coding of HTML, and that's made it possible for me to create a new flow in a different format, XML.

Dave predicted a new generation of applications based on XML that would exist alongside the web browser. The key was better writing tools that would abstract away the details. XML for every blog post would never catch on if the author needed to manually create the files. It had to be as simple as publishing a new post and letting the blogging software handle the feeds.

Netscape was developing a portal called My.Netscape.com. It allowed you to configure your portal home page with a visual grid of boxes, each box pulling from a different data source like weather or news. By leveraging XML feeds, the portal became an aggregation platform that could be extended with a wide variety of data sources, even from blogs.

Dave Winer’s scriptingNews format was an inspiration for the work Netscape was doing, but Netscape’s early experiment creating RSS used RDF, the Resource Description Framework. The markup was different, and Dave and Netscape initially worked together on a common format.

Netscape's interest in RSS was short-lived. No one really had ownership of the format. It was in this vacuum that Dave Winer iterated on the format with versions 0.92, 0.93, and 0.94, even as a separate group would develop RSS 1.0, moving it back to its roots with RDF.

Dave Winer later came to question whether throwing away his scriptingNews format was the right decision. [In a post in early 2020][3], Dave wrote:

> I turned a corner [in 2017][4] with my blog. I realized then, though I wouldn't have put it this way, the price I paid by merging formats with Netscape was too great. It forced blogging into the title-description-body model of journalism. But blog posts are more free-form, they don't all fit into that structure.

Back when Netscape was interested in RSS, it was a way to integrate content into a portal. Portals were the big thing in 1999. Social networks today are the new portals, but instead of looking at common formats to improve sharing data, each social network tends to create their own closed API.

One challenge that large platforms have when they have thousands of feeds to check is that polling takes time. They have to download each feed to see if there are any new posts, and many client apps don't refresh feeds very often. Part 5 covers how we can get real-time updates when a blog changes.

---- 

There’s a classic programmer joke, most widely known for the version with regular expressions:

> Some people, when confronted with a problem, think “I know, I'll use regular expressions.” Now they have two problems.

We can relate to it and laugh because programmers are often inventing more work for themselves in an attempt to automate their way out of a problem. The shortcut ending up as the longest path has the ring of truth to it.

In the spirit of that joke is an [XKCD comic][5] that is often shared whenever someone creates a new file format or standard: “Now there are 15 competing standards.”

![][image-1]

It resonated because it captures something that’s almost always true when starting a new format: the attempt to solve problems in the status quo. We all want to fix limitations in the old format, and format wars can inevitably result.

For Dave Winer in 2003, RSS 2.0 was done. Apps could be built on it as-is, and if the format remained frozen then apps would be guaranteed compatible.

In an [interview with CNET][6], Dave Winer talked about how he came to Harvard, where the RSS 2.0 specification was hosted. The school was interested in making it easier to share information between different parts of the school:

> They had a conference late last year where they were trying to establish what was the digital identity of Harvard University, and the idea came out. It's a very big decentralized school with a small core and a whole lot of schools that are part of it--the business school, the school of government, library sciences--and in that way it's sort of like a company with divisions. How do you get those divisions to work with each other and share information so they don't duplicate efforts? […] The solution sounded very much like Web logs, so a bunch of people told Harvard, "You should talk to Dave."

Harvard had been founded over 300 years earlier. Their libraries held thousands of books and documents. With that kind of stability, Harvard was a natural place for the frozen RSS specification.

Dave Winer followed up about the split of RSS in a post [in early 2019][7]:

> The two groups wanted to do very different things. Netscape, as far as I'm concerned, wanted to bootstrap syndication of web content, and that was validated by the enormous popularity of RSS for that application. They had a vision that was right. And yes, they did one day just disappear. I wanted to preserve the progress we had made and build on it. I loved the idea since feeds provided exactly the level playing field I wanted for bloggers and pros.

Sam Ruby had started a wiki to brainstorm an alternative to RSS, an effort that would lead to the Atom feed format. [A key motivation][8] was the frustration of not being able to update the RSS spec to clarify inconsistencies:

> The problem is that Dave Winer has declared RSS 2.0 the last version of RSS. We could write guidelines and recommendations but we'd be always be hobbled by the fact that the actual spec is untouchable.

There was good and bad about freezing RSS. While the goal was to have a stable foundation for app developers, the reality is that we ended up with a much more muddled set of standards. Atom was clearly specified but a different format, forcing developers to choose between RSS or Atom, or use namespaces to mix elements from Atom into existing RSS feeds.

This mixing can be seen in the `content:encoded` element, which is often used to be explicit about using HTML in an RSS feed. It’s in widespread use from the [RDF Site Summary module][9], but not technically part of RSS:

	<rss version="2.0" xmlns:content="http://purl.org/rss/1.0/modules/content/">
	...
	<title>Testing</title>
	<description><![CDATA[Hello world.]]></description>
	<content:encoded><![CDATA[<p>Hello world.</p>]]></content:encoded>

Atom also came about at a time when most blog posts were using titles, so [the Atom spec itself][10] requires titles:

> atom:feed elements MUST contain exactly one atom:title element

Not only is the title required, it also shouldn't be empty according to the Atom spec:

> It is advisable that each atom:entry element contain a non-empty atom:title element, a non-empty atom:content element when that element is present, and a non-empty atom:summary element when the entry contains no atom:content element.

This is not a good fit for a microblog post, which has no title. Meanwhile, XML in general — which both RSS and Atom are based on — is falling out of favor with developers.

And at the same time, podcasting has grown into a huge industry. Almost all podcast feeds are RSS, not Atom. When people talk about the technology behind podcasting, they mention RSS, not Atom. Even though RSS was a frozen format, it had all the momentum.

RSS is not going anywhere. Even if we explore other formats for syndication, all blogs should have an RSS feed. RSS forms the foundation for subscribing to blogs and delivering podcasts. It’s huge and the open web is a much better place because RSS exists.

So we should do two things: support RSS in its simplest form, cutting out all the cruft, and also support JSON Feed to make it easier to build new apps.

[1]:	http://scripting.com/2015/01/03/theMagicOfWorkingTogether.html
[2]:	http://scripting.com/davenet/1997/12/15/scriptingNewsInXML.html
[3]:	http://scripting.com/2020/01/19/145834.html?title=imRethinkingRssNow
[4]:	http://scripting.com/2017/05/05/iWantMyOldBlogBack.html
[5]:	https://xkcd.com/927/
[6]:	https://www.cnet.com/news/blogging-comes-to-harvard/
[7]:	http://scripting.com/2019/01/10.html#a200132
[8]:	http://www.intertwingly.net/wiki/pie/Motivation
[9]:	https://web.resource.org/rss/1.0/modules/content/
[10]:	https://tools.ietf.org/html/rfc4287

[image-1]:	https://book.micro.blog/uploads/2019/9ea8632ac3.png
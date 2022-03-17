## WordPress and Tumblr

_“The true meaning of life is to plant trees, under whose shade you do not expect to sit.” — Nelson Henderson_

Matt Mullenweg’s legacy is deeply entrenched, with bits that he coded or advocated for spread throughout the web. [Way back in a blog post in 2003][1], Matt wrote about his “dilemma” to find the best software to run his blog:

> Fortunately, b2/cafelog is GPL, which means that I could use the existing codebase to create a fork, integrating all the cool stuff that Michel would be working on right now if only he was around. The work would never be lost, as if I fell of the face of the planet a year from now, whatever code I made would be free to the world, and if someone else wanted to pick it up they could. I’ve decided that this the course of action I’d like to go in, now all I need is a name.

That name was WordPress. You can see in that post some of the principles that would remain with WordPress for nearly 2 decades: openness and longevity that still guide Matt’s company Automattic today.

After b2 was forked to create WordPress, Movable Type and WordPress were vying for popularity. One static, one dynamic. One Perl, one PHP. Although different approaches, together they cemented the idea of a blog database schema that has fields for title, body, categories, and keywords.

In recent years, WordPress has drifted away from its roots in blogging. When I attended a WordCamp in 2017, no one was talking about blogs. It was all about using WordPress as a full CMS.

WordPress’s Gutenberg block editor has also captured most of the development attention in the WordPress community, completing the shift away from simple, text blog posts to richer, full web pages. Gutenberg represented a multi-year vision from Mullenweg to make WordPress’s default editor competitive with modern blog platforms like Medium.

---- 

While WordPress was growing to become an even more capable full web site editor, Tumblr launched trying something different. In 2005, Jason Kottke blogged about first [discovering tumblelogs][2]:

> A tumblelog is a quick and dirty stream of consciousness, a bit like a [remaindered links][3] style linklog but with more than just links. They remind me of an older style of blogging, back when people did sites by hand, before Movable Type made post titles all but mandatory, blog entries turned into short magazine articles, and posts belonged to a conversation distributed throughout the entire blogosphere.

Tumblr was inspired by early tumblelogs as founder David Karp realized there was no simple, hosted service with a focus on tumblelogs. Tumblr was a microblogging platform before microblogging was a coined term. The new twist in Tumblr’s UI was post types: start a new post as a link, quote, chat, or photo. The UI adapted to the post type, with most types not using a post title field.

Lead developer and CTO [Marco Arment blogged in 2007][4] about potential self-hosted competition and the trade-offs for centralized hosted platforms like Tumblr:

> Some people just don’t feel comfortable having their data and services in someone else’s hands, while most people don’t want to (or can’t) host, maintain, and upgrade web software themselves. There are also different feature sets: installable software is more easily customizable with plugins and source modification, while hosted services can more eaisly provide community and directory features.

This ease of use was a key part of Tumblr’s growth. Tumblr attracted a diverse, large user base full of both traditional-looking blogs and lighthearted niche topics.

I reached out to Marco Arment to ask some questions about the early days of Tumblr for this book.

**Manton:** What was it like when Tumblr was just you and David Karp?

**Marco:** It started as most projects did at the time: building a web app, showing it to our friends, and having a few people try it out. Tumblr was one of a handful of projects we were working on at the time as a consultancy, with the other contracting projects paying the bills to enable us to experiment.

**Marco:** David and I worked very well together. In addition to being a great front-end developer and designer, he’s also enough of a programmer that he could build everything himself. But he was also wise enough to know when he’d reached the limit of his skills and should hire a specialist, and I was that specialist for his lower-level programming needs. He was able to focus more on the design and front-end coding, while I made everything fast and scalable behind the scenes, but he was still technical enough to do a significant amount of coding himself, appreciate and manage my work, and ask insightful and provocative questions.

**Marco:** We kept Tumblr as just the two of us for an unusually long time, which let us keep costs down and iterate very quickly. In retrospect, and I think he’d agree, we probably should’ve hired more people sooner. But we were both very young and very busy — a combination that hides the need to expand a team and provides no time with which to do so.

**Manton:** Were there any early clues that Tumblr would become so popular?

**Marco:** We had a few friends using it from its inception in late December 2006, but it really took off with [Gina Trapani’s Lifehacker article][5] in March 2007. From that day forward, growth was constant and aggressive — I forget the exact numbers, but I think it was in the ballpark of 20% growth per month.

**Marco:** When I was there (2006–2010), it felt like a great accomplishment for a small team and kept us very busy, but I never imagined us being a peer to the “big” social networks or publishing tools. We always felt like the independent underdogs in New York, making the alternative to the Silicon Valley startups for other eccentric nerds like us.

**Marco:** Ultimately, most of Tumblr’s popularity came after my departure in late 2010. Most Tumblr retrospectives I see in the press are written by people who joined after I left, about events that happened after I left, involving people I never worked with.

**Marco:** They usually don’t even realize or acknowledge that my era there existed. (Everyone thinks Tumblr started around the time they joined.) But it was an amazing ride, an era of my life that I look back upon very fondly, and probably the most exciting and popular thing that I’ll ever work on.

**Manton:** You wrote some [on your blog in 2007][6] about Tumblr’s dashboard and trying to automatically find blogs to show people, to help discovery for new users, while also flagging spam. What kind of tools did you build to automatically catch problems? At what point did Tumblr need a larger team to keep up with content moderation?

**Marco:** Tumblr started as a blog-publishing tool with no social features, so in the earliest days, discovery and promotion were very low priorities. As it grew, the social features grew with it and eventually became what people knew Tumblr for, but they were very rudimentary in the beginning.

**Marco:** I don’t even remember what the discovery system was in the post you referenced, but the imminent replacement I teased was most likely Tumblr Radar, a grid that displayed the most popular recent posts. (Digg was very big then, and this was effectively a mixed-media version of it.)

**Marco:** Radar’s posts were only displayed after human approval — mine, for a while. On my train ride to work each morning, I’d use a cellular-tethered laptop to browse a back-end list of the most popular posts and manually approve whatever seemed appropriate for a general audience.

**Marco:** Our first additional employee was Marc LaFountain, who handled customer support and community management. At some point, I believe we passed this role along to him.

**Marco:** Spam wasn’t a big issue for the first few years because we were careful not to create any incentives for spammers. To deal with the few rudimentary issues we had, I just wrote some simple heuristics that prevented most automated spam and flagged any suspicious accounts for review. I did this review at first, then added it to Marc LaFountain’s duties.

**Marco:** The role of content moderation on a publishing platform today is much more broad, challenging, and important than what we had to deal with in those early years. Most of the job back then was spam prevention and a handful of copyright claims. In retrospect, we were very lucky that our users in that era were mostly nerds and artists, and we didn't have the challenges of today’s social networks. (This is another area that obviously changed significantly after I left in 2010.)

**Manton:** For all these years Tumblr has stayed true to its roots of making it easy to quickly blog not just text but also links, quotes, or photos. Reblogging on Tumblr even predates Twitter's own retweets. Did y’all ever feel pressure from WordPress and other blogging tools to make longer, essay-like posts a bigger part of Tumblr?

**Marco:** Not at all.

**Marco:** We always saw blogging tools like WordPress as indirect competition at best, almost as if we were a magazine publisher and they were a book publisher. Traditional blogs almost seemed like a different medium with very different needs and goals.

**Marco:** People could (and did) write long-form posts on Tumblr, but it was never optimized for them, and that allowed us to build great features designed for short content. Similarly to how an RSS reader is a pretty poor way to read Twitter, and Twitter is a pretty poor way to read long-form writing, what we were building was different enough in both creation and consumption style that we never saw traditional blogs as direct competition.

---- 

Years later, when Yahoo! acquired Tumblr, [CEO Marissa Mayer said][7] that Tumblr and Yahoo! shared “a vision to make the Internet the ultimate creative canvas by focusing on users, design – and building experiences that delight and inspire the world every day.”

But the acquisition’s potential as part of Yahoo! never went anywhere. Marco had already moved on to dedicate more time to Instapaper. Tumblr changed hands again, to Verizon, as Yahoo! sold off many of its properties. Tumblr seemed derailed as other social networks gained momentum.

---- 

When App.net's crowdfunding was successful, I blogged about loving the transparency of the new platform, because co-founder Dalton Caldwell was blogging regularly:

> Where we only hear from Twitter’s CEO, Dick Costolo, through big news publications or at conference keynotes, for Dalton we hear it directly from his own blog posts, the way a small company should communicate. Being on the ground in posts and tweets is a perfect complement to his goal of treating users and developers as real customers.

Almost exactly 7 years to the day after I wrote that, Automattic acquired Tumblr. There’s a kind of symbolism to that date coincidence. Tumblr is effectively being re-funded.

Like Micro.blog, Tumblr is about making blogging easier. Like Micro.blog, Tumblr allows custom domain names for your blog, something no other major social network allows. Unlike Micro.blog, however, Tumblr’s community is only Tumblr blogs, although earlier versions of Tumblr supported adding RSS feeds. Micro.blog’s community brings together not just Micro.blog-hosted blogs, but people using WordPress, Mastodon, or home-grown IndieWeb solutions.

Tumblr seems in the best hands at Automattic since Tumblr was that small platform envisioned by David Karp and Marco Arment. Matt Mullenweg and the Automattic team have a bunch of work ahead of them to integrate Tumblr into the WordPress ecosystem. I don’t know how that’s going to play out, but I know that preserving all the Tumblr blogs and giving them new life is good for the web.

Micro.blog and Automattic may be on parallel tracks. Two companies wildly different in size and scope, but we can all learn from platforms that have come and gone, finding our own path to a shared vision of the future that embraces content ownership, supports healthy communities, and deemphasizes massive social networks. I’m wishing the team at Automattic the best.

People were pulled away from blogging, drawn to social networks that were faster to post to and easier to interact with friends. It's our job to pull them back to blogs by bringing the best parts of old-school blogging and modern social networks together.


[1]:	https://ma.tt/2003/01/the-blogging-software-dilemma/
[2]:	https://kottke.org/05/10/tumblelogs
[3]:	https://web.archive.org/web/20050924175553/http://www.kottke.org/remainder/
[4]:	https://marco.org/2007/07/13/gelato-an-installable-tumblr-clone
[5]:	https://lifehacker.com/geek-to-live-instant-no-overhead-blog-with-tumblr-244915
[6]:	https://marco.org/2007/06/06/its-almost-that-boring
[7]:	https://yahoo.tumblr.com/post/50902111638/tumblr-yahoo
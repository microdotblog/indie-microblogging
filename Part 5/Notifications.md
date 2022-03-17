## Notifications

_“My goal isn't to get the bits to you as fast as possible while you wait for them, but to have the bits arrive before you even know they're there.” — [Dave Winer][1]_

I like the term microblogging because it has “blog” in it. With blogging comes some assumptions: that you’re posting to a site you control, that it’s easy but a little formal, so that you invest time into it, putting more into your posts. When you put some thought into your writing, because it’s your name and your site behind the words, you’re less likely to make personal attacks on others.

Not everyone sees “microblog” with a positive connotation. Microblogging can also be more ephemeral, firing off quick posts like chatting. In an [interview with Recode Media in September 2018][2], Twitter CEO Jack Dorsey described wanting to distance his platform from blogging:

> One of the descriptions and labels that we had in the past that I always despised was microblogging.

Twitter has highlighted this difference whenever they can. They’ve trademarked the word "tweet". They’ve evolved their app UI to encourage conversations. They've emphasized live breaking news and hot takes.

The Twitter founders had not always agreed that it should be a messaging platform. In the book Hatching Twitter, author Nick Bilton framed the early debate between Evan Williams and Jack Dorsey. The co-founders were impressed with how useful Twitter was to communicate with friends after an earthquake in 2006:

> For Ev it was another clue in a theory he was developing about Twitter's role as a way to share news, not just status—Twitter as a communication network, not just a social network. He told Jack about the concept of Twitter as a news network, but Jack disagreed, instead seeing the earthquake tweets as an example of the speed of Twitter.

This speed of getting tweets to your followers was a perfect complement to the ease of use in the tweeting UI. A year later during the SXSW Interactive festival in Austin, Twitter was everywhere.

But by 2008, the technology behind Twitter seemed to be falling over. The user base was thousands of times what it had been at the big rollout at SXSW a few years earlier. Twitter’s original architecture hadn’t been designed for this kind of growth.

The timeline in a social network like Twitter presents a unique problem for scaling. When a new tweet is posted, everyone following that user should see the tweet in their timeline. From a programming standpoint, there are a couple ways to solve this:

* A relational database with tables for users, tweets, and the user following relationships. To build the timeline, you can join between the tables. This is fine for a small data set, but could be very slow when someone is following hundreds or thousands of users.
* A special database that is very good at storing lists of items, with data sets that represent each timeline for every user. When someone tweets, that tweet is effectively copied into the timeline of anyone who follows them. This makes retrieving the timeline very fast because all the data is pre-cached.

This process of sending tweets to everyone who needs them is called “fan out”, and it represented a redesign for Twitter's backend. Over years, Twitter worked to split their monolithic app into separate systems, and they used in-memory databases like Memcache and Redis that were more well-suited to addressing Twitter's performance issues.

Twitter eventually did get a handle on scaling. Twitter today is fast and reliable. But what of independent blogs? Polling for new posts across thousands or millions of blogs is difficult to scale. How do we get this same instant delivery of posts but across the whole web?

Long before Twitter was created, Dave Winer was searching for similar answers. He wasn’t working on a platform like Twitter. [In 2001][3] he was building tools that let him blog more easily, working in his favorite writing environment, the outliner. The goal was to get real-time notifications of changes to documents:

> Now it's possible, using the information in an RSS channel, to request that a centralized coordinator, a "cloud", send notification that a channel has changed. Either side of this conversation can use either XML-RPC or SOAP to communicate.

Dave continued:

> Most aggregators scan for changes once an hour, but in some situations we want to know immediately when a channel has changed. For example, we include RSS Boxes on many of our sites. When an editor routes a item to a box, we want the news to be displayed immediately, but we don't want to read the RSS channel on every hit. Notification makes it possible to always be current yet conserve bandwidth and server cycles.

That effort was rebooted in 2009 as rssCloud. But rssCloud was still based on XML-RPC, which was falling out of favor, and RSS itself saw little innovation during this period.

Around the same time, another group came together to develop PubSubHubbub. Short for "publish and subscribe" (with a hub), the name also translates to the clever acronym "PuSH".

Julien Genestoux was a co-author of the PubSubHubbub specification and founder of Superfeedr, itself a hub supporting publish and subscribe. [On the Superfeedr blog][4], Julien wrote that because social networks and blogs already had feeds that represented a user's stream of activities, they could be connected via PubSubHubbub to form more distributed social networks:

> The next step is to make these feeds “real-time” so that the consuming applications shouldn’t need to poll thousands of feeds or services. _To consume my friends information, I shouldn’t even need to be part of the network on which they publish._ **PubSubHubbub enables that.**

There were moments when it appeared that PubSubHubbub would be widely supported. WordPress.com supported both PubSubHubbub and rssCloud. Superfeedr also provided the service for Tumblr and Posterous. But the largest social networks were still based on private APIs, and in fact Twitter would start to phase out their real-time subscription API, reserving it for enterprise customers.

Google Reader would soon shut down. Everyone was too distracted with social networks, JSON, and mobile apps. It wasn’t the right time for real-time notifications for blog posts at web scale.

[1]:	http://scripting.com/2001/01/06.html
[2]:	https://www.recode.net/2018/9/14/17857486/twitter-jack-dorsey-nyu-jay-rosen-bias-neutrality-presence-politics-recode-media-podcast
[3]:	https://web.archive.org/web/20090326075735/http://www.thetwowayweb.com/soapMeetsRss
[4]:	https://blog.superfeedr.com/social-networks/federation/pubsubhubbub/xmpp/distributed-social-networks/
## Leaving Twitter

_“There aren't many companies that get to this level. And there aren't many founders that choose their company over their own ego.” — Jack Dorsey’s [resignation letter][1]_

The first version of Twitter used a database server with auto-incrementing numbers to represent the ID for each record. Years later such a simple relational database would present scaling problems, but in June 2006 when I joined, this database design was just how you started building a web app. For every new record added to a table representing users in the database, the ID for that record is incremented, giving the next user a higher user ID.

Because this number is available in the Twitter API and shown in some apps, you could see when someone joined the platform. I was the 897th person to sign up on Twitter. For years I was proud of this low, 3-digit user ID. I loved Twitter and would excitedly describe the platform to people who were first hearing about it.

In 2008 in Chicago, I was at the C4 conference for Mac developers. When the conference ended I shared a cab to the airport with Alex Payne, who built the first Twitter API. I was so excited about the potential for the platform that I probably had a dozen ideas for Twitter apps. Alex and I sat at a cafe at the airport, waiting for our respective flights, and talked about the future.

I built several third-party apps for Twitter after that. Tweet Library was an iOS app for keeping an archive of your tweets and organizing tweets into collections. Tweet Marker was an API that other apps could use to sync the timeline scroll position across apps.

[John Gruber wrote in 2009][2] that Twitter was perfect for experimenting with new apps:

> There are several factors that make Twitter a nearly ideal playground for UI design. The obvious ones are the growing popularity of the service itself and the relatively small scope of a Twitter client. Twitter is such a simple service overall, but look at a few screenshots of these apps, especially the recent ones, and you will see some very different UI designs, not only in terms of visual style but in terms of layout, structure, and flow.

When I announced Tweet Marker in 2012, there was a vibrant Twitter developer ecosystem. It was about to erode. Just a couple months later, [Twitter announced][3] their infamous 4-quadrant chart, discouraging certain types of Twitter apps.

![][image-1]

In one corner of the chart were the apps Twitter wanted to see. In another corner were the apps they didn't care about, which included some of my favorites. Twitter blogged:

> That upper-right quadrant also includes, of course, "traditional" Twitter clients like Tweetbot and Echofon. Nearly eighteen months ago, we gave developers guidance that they should not build client apps that mimic or reproduce the mainstream Twitter consumer client experience. And to reiterate what I wrote in my last post, that guidance continues to apply today.

Twitter was also limiting the number of auth tokens an app could have:

> Additionally, if you are building a Twitter client application that is accessing the home timeline, account settings or direct messages API endpoints (typically used by traditional client applications) or are using our User Streams product, you will need our permission if your application will require more than 100,000 individual user tokens.

In 2009, before Twitter had their own official Twitter app, developer Buzz Andersen and designer Neven Mrgan shipped an early third-party Twitter app, Birdfeed. Buzz was actively working on Birdfeed through Twitter's transition of their API from simple password-based authentication to OAuth, which required apps to register with Twitter.

Buzz said in a [tweet][4]:

> Twitter isn't just enforcing OAuth for technical reasons: it's a way of taking control of the platform.

Removing RSS feeds followed the same playbook. There used to be RSS feeds from Twitter for reading a user’s timeline. Without feeds and without open access to the API, Twitter could make the official apps the prominent way to use Twitter, driving up engagement and ad revenue.

[An email from Ryan Sarver][5] showed part of how Twitter was changing as a company, refocusing from building a network to selling a product. Reading between the lines, it seems that to effectively sell ads, Twitter felt they need to control the user experience. On Twitter clients:

> Developers have told us that they'd like more guidance from us about the best opportunities to build on Twitter. More specifically, developers ask us if they should build client apps that mimic or reproduce the mainstream Twitter consumer client experience. The answer is no.

Then over the weekend, [Ryan clarified][6]: “we are saying it’s not a good business to be in but we aren’t shutting them off or telling devs they can’t build them.”

IFTTT — If This, Then That — was a popular way to connect different platforms together, and it depended on open APIs. IFTTT was a useful tool that helped people do more with Twitter, even if they weren't developers. Turning off IFTTT support was the last straw for me personally because the decision seemed to incapsulate everything that was wrong about Twitter's direction.

[Matthew Panzarino wrote at The Next Web][7] about how IFTTT removal was a “red alert” to developers:

> This means that many third-party developers who thought that their complimentary services, which did not duplicate the features or feel of clients at all, were safe under the new rules will have to take a very hard look at their apps.

I had become disillusioned by this developer-hostile attitude, where third-party apps were supported only if they fit within Twitter's business model. App.net promised a better vision, but faded away. I experimented with posting short posts on my own blog where they could outlast any silo.

The more I posted to my blog, the more regret I had about all those years giving Twitter power over my own content. As [Marco Arment wrote in 2014][8]:

> Twitter started out as a developer-friendly company, then they became a developer-hostile company, and now they’re trying to be a developer-friendly company again. If I had to pick a company to have absolute power over something very important, Twitter wouldn’t be very high on the list.

Meanwhile, Twitter had gone mainstream. Alex Payne had left the company and Twitter was much different from a business and leadership perspective by the time the rest of the world started paying attention. Thousands of employees worked at Twitter. How many of them had experienced the early days of following friends’ tweets via SMS, when the service seemed genuinely new and important? The future had arrived but it was full of hashtags.

The unique tragedy with Twitter’s changing attitude toward developers is that so many of Twitter’s early innovations [did come from third-party developers][9]. The word tweet, the first use of a bird icon, and even the character counter started in Twitterrific. Twitter's new leadership displayed an incredible disrespect for the value developers added to both the ecosystem and core platform.

So I stopped posting to Twitter. It was many things. The limits on user auth tokens, which had already killed a few popular third-party Twitter apps; the problems with shutting down IFTTT recipes; the guidelines that restricted how you could use your own tweets.

I knew leaving would be difficult, so I set up a series of posts to discourage my future self from ever joining again. My final tweets were timed to go out on the anniversary of Steve Jobs’s death. They’re a collected moment, a tribute to both Steve and how great Twitter could be. I like that they’re forever pinned at the top of my profile page.

My last tweet was both a goodbye and a memory of what had made Twitter special. I wanted to highlight the good parts of Twitter because there were so many people causing trouble on the platform. For every beautiful tweet, there was hate and harassment and negative tweets and sarcasm and snark.

Overlapping the developer-hostile attitude was a growing realization that Twitter was overwhelmed with managing the community. Hate and harassment spread mostly unchecked. Something about the short, 140-character posts seemed to bring out the worst in people. (I'll cover community and replies in more detail in part 5.)

And then in 2018, the evolution of the Twitter API away from traditional client developers started becoming more real. [In a blog post announcing the change][10], Twitter outlined how they would retire older APIs, moving to new APIs with a different pricing structure that made little sense for traditional Twitter clients:

> We built a [migration guide][11] to assist in the transition from Site Streams and User Streams to the Account Activity API. As a few developers have noticed, there’s no streaming connection capability or home timeline data, which are only used by a small amount of developers (roughly 1% of monthly active apps). As we retire aging APIs, we have no plans to add these capabilities to Account Activity API or create a new streaming service for related use cases. Home timeline information remains accessible for developers via the [statuses/home\_timeline][12] endpoint.

With the API more limited, there was less incentive to build fun tools that worked with Twitter. [Tim Haines wrote about][13] how Twitter deprecating the streaming API led him to shut down his service Favstar:

> Twitter wrote that they’ll be replacing this with another method of data access, but have not been forthcoming with the details or pricing. Favstar can’t continue to operate in this environment of uncertainty.

It had taken nearly 6 years, but it felt like [2018’s API changes][14] finally wrapped up the work that started in 2012. The apps that are possible with the new Account Activity API are exactly the apps that were encouraged in those other quadrants. The pricing made no sense because it wasn’t designed for traditional Twitter apps like Twitterrific and Tweetbot.

Twitter’s history has been tumultuous. Jack Dorsey as CEO was out, then back in. The API was open, then closed, then more open again. And all through it, Twitter’s features haven’t changed much until recently.

The Twitter founders had stumbled onto something world-changing. The momentum of a unique idea carried them for years, even flawed, even as they lost their way. For indie microblogging to succeed, we must be more thoughtful and deliberate about the future.

[1]:	https://twitter.com/jack/status/1465347002426867720
[2]:	https://daringfireball.net/2009/04/twitter_clients_playground
[3]:	https://blog.twitter.com/developer/en_us/a/2012/changes-coming-to-twitter-api.html
[4]:	https://twitter.com/buzz/status/21402358130
[5]:	http://groups.google.com/group/twitter-development-talk/browse_thread/thread/c82cd59c7a87216a/7dd46c26157c9e29
[6]:	http://groups.google.com/group/twitter-development-talk/browse_thread/thread/c82cd59c7a87216a/7dd46c26157c9e29
[7]:	https://thenextweb.com/twitter/2012/09/21/why-ifttt-forced-remove-twitter-triggers-red-alert-developers/
[8]:	https://marco.org/2014/10/20/wsj-twitter-peace-offering
[9]:	http://furbo.org/2011/03/11/twitterrific-firsts/
[10]:	https://blog.twitter.com/developer/en_us/topics/tools/2018/enabling-all-developers-to-build-on-the-account-activity-api
[11]:	https://developer.twitter.com/en/docs/accounts-and-users/subscribe-account-activity/guides
[12]:	https://developer.twitter.com/en/docs/tweets/timelines/api-reference/get-statuses-home_timeline.html
[13]:	https://favstar.fm/pro
[14]:	https://www.macstories.net/news/twitter-announces-new-end-of-life-date-for-apis-and-pricing-that-affects-third-party-apps/

[image-1]:	https://book.micro.blog/uploads/2019/6b980c7c4e.png
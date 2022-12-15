## Unattended algorithms

_"Technology is inherently a force multiplier, by default it amplifies the already powerful more than the less privileged, widening existing power gaps." — [Tantek Çelik][1]_

An algorithm is just code a programmer wrote, often to process data or display it to the user. Apps have many algorithms. Very few of them are noteworthy.

The word "algorithm" for social networks takes on special meaning because it is used to explain why something doesn't work the way we expect it to. The "algorithmic timeline" is a normal timeline, but with posts in an order that we can't predict. Technically, a chronological timeline is _also_ controlled by an algorithm, but the algorithm is transparent: it puts the posts in order by date.

The way a feature works influences what users can do and how they interact with the platform. The algorithms that make up a feature, if developed thoughtlessly, can lead to a user-hostile or counterintuitive experience.

[Om Malik blogged about][2] the early days of Twitter, when they were so busy it was easy to accidentally standardize the way the platform worked without thinking through what impact certain features would have:

> I was there at the proverbial birth of Twitter. All along, it has been held together by proverbial chewing gum and tape. There wasn’t much thought about how things could go wrong. Instead the focus was: Can we keep the machines running? Can we keep growing? Can we stay competitive with Facebook? Until some of us started questioning their data and their platform challenges, it didn’t seem to be a top priority.

What drives the algorithms? Ad-based social networks want more engagement: clicks, likes, and retweets. The Verge covered some of how engagement is measured in [an article about Twitter topics][3]:

> Finally, Twitter looks at engagement: how many other people who care about this topic liked, retweeted, or replied to a tweet? The more people are interacting with the tweet, the more likely it is to make the cut.

TikTok is all algorithm. You don’t follow anyone. You don’t organize feeds or topics. Just let it show you popular, entertaining videos, endlessly.

For TikTok, the algorithm is considered the secret sauce, playing a large role in the app’s success. When the Trump administration attempted to force a sale of TikTok to a US-based company, the Chinese government pushed back with a new regulation controlling the sale of algorithms like the one that powers TikTok. It became a deal-breaker for a potential acquisition by Microsoft, who did not want to own TikTok without also controlling the algorithm.

Neil Stephenson, in an [interview with PC Magazine][4] for his new book, talked about the problems with social media algorithms:

> We've turned over our perception of what's real to algorithmically driven systems that are designed not to have humans in the loop, because if humans are in the loop they're not scalable and if they're not scalable they can't make tons and tons of money.

I think more social networks should [do things that don't scale][5], prioritizing safety over profit. For example, in Micro.blog the featured posts in Discover are curated by humans instead of algorithms.

In contrast, significant parts of Facebook and Twitter seem to run unattended. [Jay Rosen said in an interview][6] for Anil Dash’s podcast, Function:

> They build a machine that they couldn't control and they couldn't know exactly what it was doing. So we've built this thing and in a sense, no one is running it. And in that, there are things that it's doing to the culture and the environment that we cannot track.

After the film The Social Dilemma came out, [Facebook published a paper][7] trying to counter it:

> Facebook uses algorithms to improve the experience for people using our apps — just like any dating app, Amazon, Uber, and countless other consumer-facing apps that people interact with every day. That also includes Netflix, which uses an algorithm to determine who it thinks should watch ‘The Social Dilemma’ film, and then recommends it to them. This happens with every piece of content that appears on the service. 

But Netflix is a highly-curated service where every film has been approved or funded. The Netflix algorithm can’t accidentally promote the type of terrible, dangerous content that sometimes surfaces on Facebook.

The combination of massive amounts of user-generated content on Facebook, an overwhelmed, outsourced content moderation staff — Facebook’s scale makes it unlike Netflix or any other smaller, curated service. And Facebook’s algorithm naturally tries to give you more of the same instead, leading you deeper into your filter bubble, because broadening your interests to more diverse content might turn you away.

There was more pushback against Facebook after they refused to remove an edited video of Nancy Pelosi in 2019, choosing instead to try to educate users that the video was fake. Monika Bickert, Facebook's vice president of global policy management, [went on CNN][8] to defend their decision. She described how Facebook works with fact-checking organizations to independently confirm whether something is accurate:

> As soon as we get a rating from them that content is false, then we dramatically reduce the distribution of that content, and we let people know that it is false so they can make an informed choice.

I signed in to Facebook to try to understand what they had done. I actually had trouble finding the video at first, maybe because none of my friends on Facebook had shared it. Searching for Nancy Pelosi did include Facebook groups such as "Nancy Pelosi is Insane" and "Americans Against Nancy Pelosi", [featured prominently][9] in the search results. If you came to Facebook to hate a politician, and discuss that hate with other users, Facebook sure made it easy.

I finally found the video, but there was no callout that it was fake. The version I saw was captured with a camera pointed at the video playing elsewhere, likely confusing Facebook's algorithm for finding an exact copy of the video.

Kara Swisher wrote in an editorial [for The New York Times][10]:

> The only thing the incident shows is how expert Facebook has become at blurring the lines between simple mistakes and deliberate deception, thereby abrogating its responsibility as the key distributor of news on the planet.

This abrogation of responsibility takes other forms too: calling for regulation on what content should be removed, and outsourcing some work to independent fact-checkers. Both efforts are effectively delay tactics. Facebook can't outsource everything. Someone has to make the tough decisions.

Twitter developed an algorithm to surface news you might be interested in directly in your notifications. This space for notifications was previously reserved for @-mentions you received from other users. [Matt Haughey blogged about][11] how the algorithm now seems optimized for outrage:

> The “in case you missed it” feature that is the default sort had grown to constantly stoke outrage. It would show me the most RTed and liked tweets at the top, often up to 24 hours after they were posted. In our current political climate that meant for 24hrs after any major event, I would see tons of tweets stuffed into the top of my timeline, even hours after things were debunked or stories shifted.

Users retweet posts that are controversial. Twitter’s trends algorithm rewards spreading the sensational, the newsworthy, the topic that might spark surprise or outrage. [Kara Wisher wrote in The New York Times][12] that social networks "are designed so that the awful travels twice as fast as the good".

In [an interview with 60 Minutes][13], YouTube CEO Susan Wojcicki said that the scale of YouTube wouldn't work if they had to review more content. The recommendation algorithm is so integral to YouTube that the CEO can't conceive of a version of YouTube without it:

> If we were held liable for every single piece of content that we recommended, we would have to review it. That would mean there’d be a much smaller set of information that people would be finding. Much, much smaller.

Facebook is trying to solve this problem with more moderation, but it's a band-aid on a system that is working [as designed][14] to surface "relevant" content for more ad views. It's not enough without significant changes to the algorithms as well.

---- 

Donald Trump was impeached on November 18th, 2019. Three months earlier, the investigation had begun after a whistleblower reported on potential wrongdoing and abuse of power by the president.

One defense of Trump was to target the whistleblower himself, attempting to reveal his identity and attack the process instead of the substance of the report. Facebook and YouTube both moved to block the spread of the whistleblower's name. Twitter initially said they would not, as reported [by the Washington Post][15]:

> Twitter defended its decision to allow the sharing of the CIA officer’s name, saying the tweets in question did not include the type of private details that go against the platform’s rules.

Facebook went further. Facebook spokesman Andy Stone told the Washington Post:

> Any mention of the potential whistleblower’s name violates our coordinating harm policy, which prohibits content ‘outing of witness, informant, or activist.’ We are removing any and all mentions of the potential whistleblower’s name and will revisit this decision should their name be widely published in the media or used by public figures in debate.

An algorithm that surfaces content for users, such as when Twitter added news to the notifications screen, can also do the opposite: de-emphasizing certain information like the whistleblower's name.

A week after Facebook and YouTube announced they would block the whistleblower's name, they had been largely unsuccessful. [The New York Times][16] followed up on users coordinating how they shared the name to avoid being detected:

> But Facebook users, for example, have been creative in their efforts to sidestep the company’s content moderation. They have avoided using the name within the text of their posts, which could alert A.I. systems screening for it. Instead, they have included it in the URL or inside an image. Others intentionally added characters such as dollar-signs and asterisks to avoid Facebook’s automated moderation.

The algorithm must be continually tweaked to accommodate users trying to sidestep it. If an algorithm _amplifies_ misinformation while platform rules are written to _slow_ the viral spread of that information, an unattended algorithm that can’t adapt will be at odds with those rules, creating an unwinnable battle for moderators.

Technology is neither a force for good or bad in the world. An algorithm, developed by accident or with little care, is most certainly going to lead astray. It must be tended.

[1]:	https://tantek.com/2020/009/t1/technology-force-multiplier-not-neutral
[2]:	https://om.co/2019/09/06/kickshitter/
[3]:	https://www.theverge.com/2019/11/6/20948547/twitter-topics-launch-sports-gaming-entertainment-test
[4]:	https://www.pcmag.com/news/368417/neal-stephenson-explains-his-vision-of-the-digital-afterlife
[5]:	http://paulgraham.com/ds.html
[6]:	https://glitch.com/culture/function-episode-19/
[7]:	https://about.fb.com/wp-content/uploads/2020/10/What-The-Social-Dilemma-Gets-Wrong.pdf
[8]:	https://www.washingtonpost.com/politics/2019/05/25/nancy-pelosi-fake-video-facebook-defends-its-decision-not-delete/
[9]:	https://www.manton.org/uploads/2019/2819855181.png
[10]:	https://www.nytimes.com/2019/05/26/opinion/nancy-pelosi-facebook-video.html
[11]:	https://a.wholelottanothing.org/2019/03/06/optimizing-for-outrage/
[12]:	https://www.nytimes.com/2018/10/30/opinion/cesar-sayoc-robert-bowers-social-media.html
[13]:	https://www.cbsnews.com/news/is-youtube-doing-enough-to-fight-hate-speech-and-conspiracy-theories-60-minutes-2019-12-01/
[14]:	https://www.ruinedby.design/
[15]:	https://www.washingtonpost.com/technology/2019/11/08/facebook-youtube-move-block-spread-supposed-whistleblowers-name-twitter-permits-both-name-photos/
[16]:	https://www.nytimes.com/2019/11/14/technology/whistleblower-name-facebook-youtube.html
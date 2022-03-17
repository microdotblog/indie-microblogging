## Harassment

_"It’s worrying how easily the most vile of fringe views can be elevated by seemingly-benign features when they're applied at the scale of YouTube or Facebook." — [Nick Heer][1]_

Buzz Andersen, the developer of the third-party Twitter app Birdfeed who had warned about Twitter using auth changes to lock down their platform, also saw how the tone of conversations was changing. From [his blog in 2014][2]:

> Twitter in 2014 feels like it has settled into a default state of hostility and rage.

Years after Buzz posted that quote to his blog, not much had changed.

Something about 140 characters exaggerates our best and worst qualities. 140 is good because it encourages easy posting, but for some people it’s a little too short, and they don’t think before they type.

Even though the limit is 280 characters now, which I do think can encourage more thoughtful replies, many people have been trained on short replies.

At the beginning of 2017, [Lindy West wrote for the Guardian][3] about the harassment she’s had to deal with on Twitter:

> I talk back and I am "feeding the trolls". I say nothing and the harassment escalates. I report threats and I am a "censor". […] I have to conclude, after half a decade of troubleshooting, that it may simply be impossible to make this platform usable for anyone but trolls, robots and dictators.

She deleted her account. Something was fundamentally broken because Twitter didn’t plan for harassment from the beginning.

[Danah Boyd gave a speech][4] after accepting an award from the Electronic Frontier Foundation. She talked about harassment in the workplace, not just online, highlighting that this takes work to solve. There are no shortcuts:

> Taking short-cuts may be financially profitable in the short-term, but the cost to society is too great to be justified. In a healthy society, we accommodate differently abled people through accessibility standards, not because it’s financially prudent but because it’s the right thing to do. In a healthy society, we make certain that the vulnerable amongst us are not harassed into silence because that is not the value behind free speech.

Frustrated by these platforms, many people in 2017 and 2018 took a break from Twitter and Facebook or quit completely. The IndieWeb maintains a partial list of [silo quits][5]: folks in the tech world like Susan Fowler and Leo Leopard; celebrities like Jim Carrey and Cher; and Journalists like Walt Mossberg and Mike Elgin.

Some people retreated to Instagram, hoping to find a quiet place to escape harassment or politics. As Taylor Lorenz wrote about for The Atlantic, Instagram itself [had a massive harassment problem][6]:

> Even lifestyle Instagrammers, long [considered the platform’s bread and butter][7], have begun questioning their place on it as a result of rampant harassment. In June, fashion-and-beauty Instagrammer Suzanne Jackson, who has more than 237,000 followers, [spoke out][8], saying that she and other influencers are “no longer ignoring” the abuse they receive on the platform

Alternative social networks have come and gone, from App.net to Ello. They haven’t cracked this problem. They are usually just as centralized and would suffer from similar abuse if they got popular enough.

---- 

There have been attempts to automate our way out of the harassment problem. Some programmers likely view harassment as a software bug that can be worked around. As I was launching the Kickstarter for Micro.blog, I fell into the same trap, thinking I could automatically flag hurtful posts for review.

The nuance of language — and the many ways that people can be jerks online — makes detecting harassment very difficult. Manual review and moderation can't be avoided.

Casey Newton investigated Facebook's content moderators for The Verge [in a tragic story][9] about outsourcing what should be one of Facebook's most important tasks: catching abusive posts and disturbing photos. Moderators would review the worst posts on the platform that were flagged for review, so bad that the moderators would have panic attacks or become depressed, needing counseling. It was revealed to be a traumatic, stressful job.

Using contractors allowed Facebook to scale up quickly around the world for much less cost than a permanent employee:

> The use of contract labor also has a practical benefit for Facebook: it is radically cheaper. The median Facebook employee [earns $240,000 annually][10] in salary, bonuses, and stock options. A content moderator working for Cognizant in Arizona, on the other hand, will earn just $28,800 per year. The arrangement helps Facebook maintain a high profit margin.

Facebook is right to hire thousands of content moderators. But those people should be real employees with healthy working conditions, not people who Facebook feels no responsibility to take care of.

This is the most damning article I've ever read about Facebook, not just because of the unacceptable way the moderators are treated, but because of what it says about Facebook's approach. Facebook is hiring contractors because they think this is a short-term problem, only needed long enough for them to develop the machine learning and artificial intelligence necessary to automatically catch problems.

We will always need human curators. But there are a range of things that better software can help detect.

Webmention is a modern version of TrackBack, which was very susceptible to comment spam. TrackBacks included an excerpt and link to include as a comment, and there wasn't usually any verification that the site sending the TrackBack actually linked to the blog post. Spammers could send arbitrary TrackBacks to hundreds or thousands of unrelated sites, essentially sprinkling spam links across the web.

Vouch is an extension to Webmention that helps address this. When sending a Webmention with Vouch, a `vouch` URL parameter is added in addition to the `source` and `target`. This extra parameter is the URL for a third site that has linked to you before, and which the target URL has also linked to.

[The IndieWeb wiki][11] describes the motivation for sites receiving a Webmention:

> You should implement receiving Webmention with Vouch in order to automatically block all automated spam and to aid in moderation of mentions.

If we can automatically trust the incoming Webmention, it can be accepted and shown on our blogs without being held for moderation. And, importantly, we are less likely to be harassed by someone who has been vouched for by someone else we've linked to before.

---- 

Instagram also made a renewed push in 2019 to minimize harassment [by detecting text that looked offensive][12]:

> In the last few days, we started rolling out a new feature powered by AI that notifies people when their comment may be considered offensive before it’s posted. This intervention gives people a chance to reflect and undo their comment and prevents the recipient from receiving the harmful comment notification. From early tests of this feature, we have found that it encourages some people to undo their comment and share something less hurtful once they have had a chance to reflect.

Instagram would [later expand the feature][13], actively warning users if they tried to post a new photo caption that was "similar to those reported for bullying".

These are good features, but we shouldn't be fooled into thinking all community issues can be solved through automation. Facebook, Instagram, and Twitter still have a massive task ahead of them.

Silicon Valley likes to think of web-based platforms that can scale to great profitability as having "zero marginal cost". That is, the cost of running the platform does not increase significantly as more users are added. It's not like scaling a company that sells physical goods, where there are obvious manufacturing or shipping expenses for every new customer.

There is a cost for these social media platforms, though. It's just a cost that they have been avoiding until now. For massive platforms, there must be a comparable large staff to stay on top of harassment and misinformation.

[1]:	https://pxlnv.com/linklog/reply-all-louder/
[2]:	https://log.scifihifi.com/post/99480324316/twitter-for-all-its-good-is-a-hate-amplifier
[3]:	https://www.theguardian.com/commentisfree/2017/jan/03/ive-left-twitter-unusable-anyone-but-trolls-robots-dictators-lindy-west
[4]:	https://medium.com/@zephoria/facing-the-great-reckoning-head-on-8fe434e10630
[5]:	https://indieweb.org/silo-quits
[6]:	https://www.theatlantic.com/technology/archive/2018/10/instagram-has-massive-harassment-problem/572890/
[7]:	https://qz.com/quartzy/1293498/is-there-a-difference-between-a-blogger-and-an-instagrammer-anymore/
[8]:	https://evoke.ie/2018/01/06/showbiz/gossip/suzanne-jackson-bullies-campaign
[9]:	https://www.theverge.com/2019/2/25/18229714/cognizant-facebook-content-moderator-interviews-trauma-working-conditions-arizona
[10]:	https://www.businessinsider.com/facebook-median-pay-240000-2017-2018-4
[11]:	https://indieweb.org/Vouch
[12]:	https://instagram-press.com/blog/2019/07/08/our-commitment-to-lead-the-fight-against-online-bullying/
[13]:	https://instagram-press.com/blog/2019/12/16/our-progress-on-leading-the-fight-against-online-bullying/
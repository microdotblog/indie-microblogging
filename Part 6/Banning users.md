## Banning users

_"In terms of sheer engagement, objectionable content is the most popular.” — [Why The IndieWeb?][1]_

As we approached the end of 2018, Micro.blog was still gaining traction. We were rolling out new features every week. We had the Micro Monday podcast. There was still plenty to do, but it felt like everything was falling into place.

And then I got this mention on Twitter that made my heart sink:

> Hey @microdotblog , what's your position on white supremacists using your tools? Because i just found one, and he's got a paid account.

I followed up with the Twitter user who had reported this to get the details. It was true. We had noticed this Micro.blog user when they first created their account, and it seemed strange, but after an initial post they had never posted again. Without the context that this Twitter user provided, we didn't know if action was necessary.

Hate speech is not tolerated on Micro.blog. I first checked if this user had replied or harassed any other Micro.blog users. They had not. In fact, no one was following this user. Our approach of making it difficult to accidentally stumble upon a random user had worked.

We draw a line between your blog and how it affects other users in the community. This is the premise behind _open gardens_. Your blog is your own, at your own domain name, and if it’s not interfering with other users — by harassing or spamming them — then we leave your blog alone. But even with this principle on the separation between your blog and the community, some content can’t be allowed. White supremacy has no place on Micro.blog.

We are small enough that we can at least skim through many posts that come through micro.blog. Spammers often create free accounts. They use the 10-day trial to post advertisements for herbal supplements or dating services. Those are easy to find, and because these “users” aren’t going to pay even $5 to keep posting, no one usually notices. We can delete their account or they fade away on their own.

Reporting is valuable when we miss something. It’s not the first line of defense, but as in the case of the white supremacist reported from Twitter, user reporting can provide important context we might otherwise miss.

Most users are trying to do the right thing and sometimes just get carried away in a conversation. Passions are strong especially around political topics. In those cases, more could be done to help users take a break from the conversation, such as temporary pausing replies to let everyone cool down.

[Cheryl Cicha of Iconfactory posted about][2] an effort to introduce new emoji specifically for calling attention to potentially bullying behavior:

> The goal was to create friendly, non-confrontational emoji that are easy to identify when seen in a timeline. They are intended to be used to let others, including friends, know they’ve overstepped or to help others identify people who behave badly on a regular basis.

This has a lot of potential. There's a place for privately reporting a user, especially someone who doesn't appear to care what other people think, but most people are trying to do the right thing and might just need a reminder.

On the other side are clearly fake accounts, set up to contribute to content farms or spam other users. At Micro.blog we've disabled thousands of these accounts, but we're a tiny platform compared to the task Facebook faces. [CNN reported][3] that Facebook has shut down billions of accounts:

> So far this year, Facebook has shut down 5.4 billion fake accounts on its main platform, but millions likely remain, the social networking giant said Wednesday. That's compared to roughly 3.3 billion fake accounts removed in all of 2018.

In Micro.blog we can also hide or block individual replies from the timeline. This does not affect the user’s blog, where they can still display all their own replies, but if there is harassment or unwanted replies it can help prevent a conversation from turning more hateful. This is a feature we very rarely use.

Similarly, Twitter has experimented with letting users control whether replies are even allowed on their tweets, or to [hide specific tweets][4] in the conversation as we do in Micro.blog.

Andy Baio [said on Twitter][5] reacting to this feature:

> Not mentioned here: if you hide a reply, Twitter will show a big modal pointing out that the author hid some replies, drawing way more attention than just leaving them alone.

This is like a smaller-scale version of the side effect when Trump’s tweets were banned, or Twitter preventing links to the New York Post article about Hunter Biden, but put in users’ hands. Sometimes it might be better to just quietly hide a reply from everyone but the reply’s author, letting the conversation wind down instead of escalate.

---- 

At the end of 2019, Jack Dorsey [dropped a bombshell][6] about a project Twitter would start exploring in 2020:

> Twitter is funding a small independent team of up to five open source architects, engineers, and designers to develop an open and decentralized standard for social media. The goal is for Twitter to ultimately be a client of this standard.

I should be excited about this, but instead my first reaction was frustration. Ten years after early Twitter employees like Blaine Cook and Alex Payne were pushing for a more open architecture, _now_ Jack Dorsey realizes Twitter is too big and creates a team to work on... [blockchain-based solutions][7]?

> Finally, new technologies have emerged to make a decentralized approach more viable. Blockchain points to a series of decentralized solutions for open and durable hosting, governance, and even monetization. Much work to be done, but the fundamentals are there.

Even with all the current excitement about the blockchain, for the web any technology with its roots in cryptocurrency may be a solution in search of a problem. Just as Microformats was a simpler approach to metadata compared to RDF and the Semantic Web, more traditional web APIs are more than capable of undergirding the evolution of the web instead of crypto.

Anything the blockchain touches will have new complexity and energy resource trade offs. As Mastodon founder [Eugen Rochko posted][8]:

> It's frustrating how cryptocurrency has poisoned all conversation about decentralization.

The first step for Twitter should be to check out the IndieWeb. There are people who have been thinking about and working toward more open social networks for years.

After a closer reading of Jack's tweets, though, I think my first interpretation wasn't quite right. Twitter isn't necessarily interested in decentralizing _content_ or even identity on their platform. Why would they be? Their business is based around having all your tweets in one place.

[Early in the thread][9], Jack hints at what Twitter is trying to do:

> First, we’re facing entirely new challenges centralized solutions are struggling to meet. For instance, centralized enforcement of global policy to address abuse and misleading information is unlikely to scale over the long-term without placing far too much burden on people.

This "burden on people" is the resources it would take for Twitter to actively combat hate and abuse on their platform. See all the thousands of moderators that Facebook has hired.

Klint Finley at Wired [wrote about how moving to a decentralized protocol][10] like Mastodon’s ActivityPub could help Twitter in terms of moderation:

> That approach gives individual communities more control over their experience and if adopted by Twitter would mean the company wouldn’t be the sole arbitrator of what can and can’t be seen online. But it doesn’t solve all the problems that big platform companies face. For example, quarantining problematic content doesn't address problems related to misinformation and disinformation.

[Ben Thompson followed up][11] on how it could narrow Twitter's focus:

> A truly decentralized network would justify Twitter washing its hands of content moderation completely at the network level, while ramping it up at the app level.

If Twitter is hoping to outsource curation to shared protocols, it should be _in addition to_ — not a replacement for — the type of effort that Facebook is undertaking. I've outlined a better approach in the chapter on open gardens and in the conclusion to this book, but most IndieWeb-friendly solutions don't seem compatible with Twitter's current business.

Nathaniel Popper wrote [an article in The New York Times][12] about Jack Dorsey’s tweets and the reaction from others hoping to wave the blockchain into next-generation social networks:

> Mr. Dorsey is following in the steps of the many cryptocurrency advocates who have argued that the underlying technology could be used to record all the users and activity on a social network, and to agree on a single set of rules for the network, without having any single company in charge. He said, though, that it would most likely take “many years.”

In the end, with the continued chaos of Elon Musk’s Twitter takeover, [Jack Dorsey wrote a longer post][13] outlining his thinking about moderation and new protocols. It built on his previous comments, but with seemingly more conviction that centralized moderation was not going to work, and that instead users should have in their hands new algorithms for shaping what content they want to see:

> The biggest mistake I made was continuing to invest in building _tools for us to manage_ the public conversation, versus building _tools for the people_ using Twitter to easily manage it for themselves. This burdened the company with too much power, and opened us to significant outside pressure (such as advertising budgets). I generally think companies have become far too powerful, and that became completely clear to me with our suspension of Trump’s account.

Project Blue Sky, the effort to develop a new social media protocol that Jack Dorsey had helped get off the ground, had also published a specification for the AT Protocol. It prioritized a decentralized approach, similar to Mastodon’s ActivityPub, but contrary to the earlier suggestions about using crypto, blockchain is not part of the AT Protocol. It did put significant thought into identity and account portability:

> The DNS handle is a user-facing identifier — it should be shown in UIs and promoted as a way to find users. Applications resolve handles to DIDs and then use the DID as the stable canonical identifier.

Using the `@example.com` DNS syntax matches Micro.blog’s own method to send an @-reply to other web sites. The AT Protocol then maps it to a more cryptic identifier — DID, or [Decentralized Identifier][14] — that the user does not need to see.

And meanwhile, we still have existing IndieWeb standards. Like the AT Protocol, the IndieWeb has always prioritized domain names. If the AT Protocol takes off, there could be a shared philosophy between it and the IndieWeb about using domain names for identity.

---- 

In 2018, Alex Jones and his conspiracy theory-fueled site Infowars finally ran against several platform’s rules around hate speech. [From The New York Times][15]:

> After weeks of criticism, YouTube, Facebook, Apple, and Spotify all acted to essentially erase many of his videos and posts from their services. In many cases, the companies are saying he violated their terms regarding hate speech and a number of other rules. Alex Jones today in his show dedicated nearly all four hours to what he called censorship of his platform.

As covered in previous chapters, this is not censorship. Banning Alex Jones limits his ability to use other platforms to amplify his message to followers, but he still had his own web site and podcast. Removing a podcast listing from Apple’s podcast directory (or from Spotify or Overcast) does not prevent a podcaster from broadcasting, because Apple does not host the podcast audio files directly. Jones would just need to do the extra work of getting his message out to followers on his own. Platforms have no obligation to help him.

Apple also removed the Infowars app from the App Store. While Jones can still have his articles on his own web site, removing the iOS app is a little more tricky than removing a podcast, because there is no other way to distribute iOS apps directly. If Apple would open up iOS to side-loading, their job to curate the App Store becomes easier because developers have another path to direct distribution.

---- 

No chapter on banning users is complete without revisiting the elephant in the room: Donald J. Trump. For years, Twitter and Facebook defended their decision to keep Trump on their platforms, but that certainty from leadership kept getting chipped away at. First flagging Trump’s posts as inaccurate. Then limiting their ability to be retweeted and spread.

The reaction when Trump tweeted a journalists email address was typical of the baby steps to rein in Trump’s use of the platform to incite. [Twitter locked his][16] account until he removed tweet:

> A Twitter spokesperson tells me that President Trump’s account was locked after he shared the NY Post columnist’s email address, and that to unlock his account, he had to agree to delete that tweet.

With the 2020 election, the momentum to de-platform Trump became too great to ignore. There was a tipping point where the threat of violence became inarguable. Attorney General Merrick Garland said in a [2021 announcement about countering domestic terrorism][17] that the justice department is focused on violence, not on ideology. “We do not prosecute people for their beliefs.”

Social networks have a different role than the government. For hate speech that could amplify threats of violence, social networks do have a responsibility to stop online speech potentially bringing physical harm into the real world.

Casey Newton captured this shift against Trump [in a post for his newsletter Platformer][18], written on January 6th, the day of the insurrection at the US Capitol. Casey had previously opposed Twitter de-platforming Trump, but he couldn’t defend that position any longer:

> By inciting the violent occupation of the US Capitol, Trump has given up any legitimate claim to power. In 14 days, barring catastrophe, he will be out of office. The only question is how much damage he will do in the meantime — and we know, based on long experience, that his Twitter and Facebook accounts will be among his primary weapons.

The next day, [Mark Zuckerberg announced][19] that the temporary block on Trump’s account would be extended indefinitely. Mark outlined why the insurrection was the clear turning point to take action because amplified political speech had spread to violence:

> Over the last several years, we have allowed President Trump to use our platform consistent with our own rules, at times removing content or labeling his posts when they violate our policies. We did this because we believe that the public has a right to the broadest possible access to political speech, even controversial speech. But the current context is now fundamentally different, involving use of our platform to incite violent insurrection against a democratically elected government.

> We believe the risks of allowing the President to continue to use our service during this period are simply too great. Therefore, we are extending the block we have placed on his Facebook and Instagram accounts indefinitely and for at least the next two weeks until the peaceful transition of power is complete.

When the narrative flipped against Trump, the changes at the big platforms snowballed. Alex Jones’s ban from YouTube earlier was almost a trial run. Trump banned from Facebook, Instagram, and Twitter. The iOS app Parler banned from the App Store. Conservatives often talk of free speech, but no one is guaranteed amplification.

Aza Raskin, co-founder of the Center for Humane Technology, [has spoken about][20] the difference between speech and reach. “We are not guaranteed the right to freedom of reach,” he said. Reach is amplification, usually at a higher level of the internet stack and not a foundational level preventing someone from speaking at all.

We use lower-level services like Amazon Web Services and Linode as if they are indistinguishable from having our own servers at a data center now, so I still think they are probably the wrong part of the stack to ban companies unless laws are broken. But it would be less of a gray area if AWS wasn’t so huge.

At the very least, it’s important to acknowledge that AWS and Twitter are completely different types of services. Twitter started taking moderation seriously way too late, and now it feels like the momentum has spilled over into every type of service, maybe too quickly, as no major platform wants to be the last one to ban Trump.

Twitter and Facebook organized safety councils to guide their actions, attempting to have independent oversight especially when banning high-profile figures like Trump. When Elon Musk acquired Twitter, chaos unfolded, and the Trust and Safety Council was disbanded. [In a statement][21], the previous members of the council wrote:

> Over recent weeks, we have been gravely concerned by Twitter leadership’s apparent disregard for the due process and investment of resources required for effective content moderation.

This echoed the feeling among many Twitter users that Elon Musk was making things up as he went along, acting largely on impulse, without a coherent strategy.

About a week after the insurrection, Jack Dorsey used [a Twitter thread][22] to explore his thoughts about banning Trump. In the tweets he seems clearly hesitant to ban, and perhaps with a different CEO at Twitter the ban would’ve come earlier. He again mentions open standards and crypto as possible long-term solutions, but lays the blame with how Twitter has managed their platform today, irrespective of what might be possible later:

> having to ban an account has real and significant ramifications. While there are clear and obvious exceptions, I feel a ban is a failure of ours ultimately to promote healthy conversation.

He’s right, but only partly. It is a failure of the community. It does have ramifications. But some of those ramifications are baked into the Twitter platform through design choices. Banning would not be so severe if Twitter was intertwined more with the open web and blogs, where moving content while retaining ownership is a matter of routine.

[1]:	https://briefs.video/videos/why-the-indieweb/
[2]:	https://blog.iconfactory.com/2019/11/proposed-anti-bullying-emoji/
[3]:	https://www.cnn.com/2019/11/13/tech/facebook-fake-accounts/index.html
[4]:	https://twitter.com/Twitter/status/1197551185894559744
[5]:	https://twitter.com/waxpancake/status/1197643029131100160
[6]:	https://twitter.com/jack/status/1204766078468911106
[7]:	https://twitter.com/jack/status/1204766085037248512
[8]:	https://mastodon.social/@Gargron/106987830364525291
[9]:	https://twitter.com/jack/status/1204766082206011393
[10]:	https://www.wired.com/story/jack-dorsey-help-you-create-own-twitter/
[11]:	https://stratechery.com/2019/bluesky-the-twitter-protocol-tragedy-alternatives/
[12]:	https://www.nytimes.com/2019/12/18/technology/facebook-twitter-bitcoin-blockchain.html
[13]:	https://www.getrevue.co/profile/jackjack/issues/a-native-internet-protocol-for-social-media-1503112
[14]:	https://www.w3.org/TR/did-core/
[15]:	https://www.nytimes.com/2018/08/06/technology/infowars-alex-jones-apple-facebook-spotify.html
[16]:	https://twitter.com/Olivianuzzi/status/1313509484296368130
[17]:	https://www.justice.gov/opa/speech/attorney-general-merrick-b-garland-remarks-domestic-terrorism-policy-address
[18]:	https://www.platformer.news/p/its-time-to-deplatform-trump
[19]:	https://www.facebook.com/zuck/posts/10112681480907401
[20]:	https://twitter.com/aza/status/1269106535185051648
[21]:	https://cdt.org/insights/joint-statement-on-the-disbanding-of-the-twitter-trust-and-safety-council/
[22]:	https://twitter.com/jack/status/1349510769268850690
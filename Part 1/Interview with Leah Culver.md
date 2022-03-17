## Interview with Leah Culver

The more I revisited the early platforms of 2005-2010, before Twitter and Facebook had completed their takeover of social media, the more I wanted to hear the perspective of the founders who were building other tools at the same time.

Leah Culver was the co-founder of Pownce along with Kevin Rose and Daniel Burka. She talked to me about those early days in an interview in late 2019, with the new perspective of everything that has happened to the web over a decade after releasing Pownce.

This is an edited version of the full interview. In the few years since this interview took place, Leah has sold her podcast company Breaker to Twitter and joined Twitter’s Spaces team, working on live audio conversations.

**Manton:** I know it's been a while since Pownce. 2007? You kind of started the project on your own, or how did it get started and how did you bring other people in?

**Leah:** So actually, it was kind of a collaboration between myself and 2 co-founders, Kevin Rose and Daniel Burka. And I would say that the idea wasn't like one person. It was a mix of ideas. I know that Kevin was really interested in the file aspect of things, like being able to share things. It was early Dropbox-ish days, so there weren't really ways to share things. And what's crazy is thinking back on it now, it's not just files as in you think like boring documents. It was even photos were difficult to share with people. This is pre Twitter even displaying any photos. And so the idea was you could share photos with people, but you could also share snippets of audio or snippets of basically anything.

**Leah:** So he was very interested in the file aspect. I was really interested in the social aspect, like how do we keep in touch with people? And this was very early days of Facebook, pre-News Feed, I think, or early days of News Feed. Basically the idea of these quick — we take it for granted now that you can just check things like Instagram or Twitter or Facebook to see what people are doing in your life. But that was totally new at this time. It was still very early days of like, "Hey, I just want to know what my friends are doing." And I think that has become such a powerful mode of communication now. But back then it was really early and that's what I was interested in. 

**Leah:** And then Daniel Burka did all of our design and he was really key in figuring out how this all works and looks. And some of his designs actually later made it into Facebook. So the idea of being able to share links and photos. That little picker at the top of Facebook was definitely Daniel's influence, though inspired by Tumblr as well. They had a similar sort of design.

**Manton:** Yeah, it did seem unique. The fact that you had "send a message" or "upload a file". Even events, which I thought was interesting.

**Leah:** We had events, which blows my mind because that feels so new in Facebook. Facebook in the past 2 years has really upped their events game, and Pownce was really strong on events way back then.

**Manton:** At the time, I know some people kind of thought of Pownce as like it's Twitter, but it's got all these extra features. Did it feel to you at the time that you were one-upping other social networks and other platforms, like you were adding more?

**Leah:** Well, Tumblr also existed at the time, which felt more like a blog. So we were trying to be somewhere in between Tumblr and Twitter. Twitter was just short messages limited to character counts and was really only text-based and no images, no whatever. And then we were trying to be somewhere in between. We wanted to be faster than blogging, like you could post things quickly. And we actually were really early mobile, too. So as soon as the iPhone launched, we had an iPhone app. As soon as they had apps, we had an app launched with the initial app launch. And so we were thinking about like, really, how can we send things the quickest way possible to friends? I think our tagline was something like "send stuff to friends".

**Manton:** And a part of that was also, do you want to share with everybody? Like the public?

**Leah:** So you could totally share publicly but you also could do like friends-only stuff, which now we're seeing with Instagram has a close friends only. Facebook has always sort of had those sort of privacy controls, but Pownce really was pioneering in that aspect, the share only with friends. And later, we saw companies like Path do a very similar route to that. I loved Path for sort of like the private sharing aspect. Or Snapchat even doing more private one-on-one sharing.

**Manton:** Yeah. I know you had a mobile app and then the timing was kind of interesting to me because the iPhone was out, but there wasn't an SDK until a year later. And so I feel like, you know, Pownce was right there. Right before the SDK, but also it didn't really last, multiple years later, where everybody had iPhone apps. Did it feel like you weren't sure... I guess some people kind of "missed" mobile, but you were there just at the right time.

**Leah:** I don't feel like we missed mobile, but it was very early. So I don't think people were really using mobile apps the way that we do now. What was really fun is like we got to pioneer some mobile things. So I got a chance to work on OAuth and oEmbed, two specifications — it's still around, or at least their influence is still quite heavy. One of the really fun things was Mike Malone, who was our iOS engineer who built most of our iOS app, worked on the system to app-switch to log in. So every time an app is like "log in with Facebook or Twitter" and you switch over to the Facebook app and back and he sort of pioneered — that was like his innovation using sort of the protocols, so registering the protocol to do that callback, which was really cool. So there's still stuff today that I'm like, "Oh, yeah, we invented that." Which is really cool. 

**Manton:** Yeah, and so you you were involved in OAuth, the spec coming basically right around the same time I guess. It must have been an early — because I think 1.0 was even a little bit after.

**Leah:** No, it was around the same time. So OAuth 1.0 was actually earlier than iPhone apps. So I think that was probably 2007, and it was a collaboration between myself and a bunch of other authors, but most notably folks from Twitter and...

**Manton:** Blain Cooke was on it...

**Leah:** Yeah, Blaine Cook was on it. Chris Messina was on it. EHL was on it. And then a bunch of people from Google and things got involved later. And then we had the fun of Facebook rewriting it a couple of years later to only use SSL. And it was like, "Okay, thanks Facebook. Great." So now, I'm a big fan of OAuth 2, but it has some assumptions baked in that we didn't have with OAuth 1, which mainly is that SSL at the time was really expensive to do. And now it's just industry standard and it's very cheap. So that was a good innovation.

**Manton:** So you rolled out the API and OAuth was part of that. I want to say that was kind of in the middle. It was after the launch, right, that you started getting developers?

**Leah:** Yes, it was almost a year after launch and it was hugely in demand. At the time, the idea of having an open API was just really exciting for developers in a way that we don't really see even today, which is unfortunate. Breaker doesn't have a public API and we don't really have people asking for it. I think that back then we had whole companies just working on APIs, right? We had Mashery. This was the start of Twilio and other companies — Urban Airship or things like that — where their whole business was an API. It's actually the start of Stripe as well.

**Leah:** So around this time APIs were super hot and developers loved to create projects on top of APIs, and I think we've seen a lot less of that lately. I think it's in some ways an effect of the maturation of the software industry, for better or worse. I actually think it's gotten worse, that things went that way.

**Manton:** I know there was a Google Group for API discussion, which I think maybe has been lost to time. But working with developers and iterating on the API, what did that feel like at the time?

**Leah:** Oh, it was super fun. I would say I'm a developer's developer. I love working on projects that other people can hack on and seeing what they're doing. And so it was a lot of fun. 

**Manton:** And I know you launched with an Adobe Air native app.

**Leah:** That's so fun because I was talking about the iPhone app, and we made a desktop app in Adobe Air. One of the reasons we chose to do it was Adobe was pushing it pretty hard. It was cross platform and it was really cool. A fun project to work on.

**Manton:** Did that use the API before the API was public, or did that use something else?

**Leah:** That's a good question. It's the same API. We only had one API. I just don't remember when it went public versus when we used it internally. It probably had coincided with adding auth through OAuth. So as soon as we had OAuth in place, we launched publicly. To be honest, I think we might have launched also with HTTP Basic Auth, which nowadays over SSL is probably almost okay, but then wasn't as great. 

**Manton:** Just sending passwords in the clear. 🙂

**Leah:** Yeah, which now wouldn't be so great. But now with SSL, it's almost like... I mean, everybody does OAuth, because it's easy. It's easy for users.

**Manton:** I want to get back to... You were talking about trying to — kind of like blogging, but way easier, and also the messaging and the other features. Was there actually a character limit?

**Leah:** There was, in some sense, but nothing like Twitter. We didn't have the restrictions of SMS. Because they were based on SMS, and we didn't... It was really the post-SMS world. We had the iPhone app come out. We were very focused on just being desktop and mobile only. And not so SMS-based, I guess.

**Leah:** What's crazy is if you remember at the time, like Venmo was SMS-based, which blows my mind to think back, that Venmo is as old as Pownce was, but nobody used it then. SMS was not the future of communication. 🙂

**Manton:** Now we accept that Twitter is huge and Facebook is huge. We have these massive platforms. The scale is hard to kind of deal with. But back then, it feels like there was a lot of competition, and there were people trying different things. Did you get a sense back then that Twitter was going to "win", and be as popular as it's gotten? Or did you get a sense that, "No, we can make a run for this? We can go head to head."

**Leah:** Yeah. I definitely thought there was a lot of players in the game. There were a lot of different apps. And then we get people being like, "Oh, I can't use another social app. I'm just so tired. I just want to use one." So we don't think of that now because I feel like it's almost the opposite. We're so sick of only having one platform, like, "Oh, everything is Facebook." Instagram is Facebook. Facebook is Facebook. It's annoying that I log in to Facebook and it's like, "Hey, you made a friend on Instagram. Don't you want to make a friend with them here?" It's like, "No Facebook, I don't." Nowadays I think there's this hunger. People get on TikTok and they're like, "Yes, finally, a new social network." But it was the opposite then. It was like we had social network fatigue. It's like, "Oh, I don't want to log into another service." Okay, make up your mind.

**Manton:** It's interesting because people didn't want to keep going to the next thing and moving their friends over. But at the same time, like you said, most of these services had APIs and they tried to be open and now we have these huge platforms which are closing their APIs off, and being less open, especially Facebook. And I wonder how that affects people's ability to jump between platforms or feel trapped.

**Leah:** Yeah, I feel just attitudes have shifted so much in the past 10 years. When we started, everyone was building social apps. It was really fun. There was a lot of choice. And then users were saying, "Oh, I'm fatigued. I don't want to move around."

**Leah:** And then we got the monoliths: the Twitter, the Facebook. And then people were like, "Oh, no, what have we done?" We have these small group of companies who have all of our data and they're run by white men. Like we didn't choose the right choices here. We decided to put all our faith into these big VC-backed companies. And who did the VCs pick? They pick people of a singular background who have a very narrow point of view of the world. And so even though the platforms are full of people with diverse backgrounds using the platforms, the people at the top and the leadership and the content moderation and all of these things is influenced by a very small group of people who are very homogenous. 

**Leah:** And I think that's a problem. One of the things I'm most sad about was, you know, I was young and Pownce was acquired pretty early. And I don't know how much control I had over it. I was pretty young and probably the least influential person on the founding team. And so I don't feel like I had a lot of control over the fact that we were acquired and shut down. But at the same time, I wish I would've fought a little bit harder, just so that we could have at least some other kind of viewpoint in our big social networks. 🙂

**Leah:** And I noticed in your book... you know, "what is the future?" I do think there might need to be some pushback against the same type of social networks being completely in control. And whether that's users owning more of their data. I don't know if that's even possible because, like I said, there is this fatigue of moving my friends over. I just think we want more variety in the people that have power in the tech industry. So it's like how do we enable that? Is that through legislation? Is that through changing how our VC system works and how companies are backed? I don't know. I'm hoping there'll be more change. 

**Manton:** Me too.

**Leah:** It doesn't look so promising at the moment. 🙂 Poor Snapchat is getting kicked around by Facebook. Not that Snapchat doesn't have the same type of homogenous leadership that Facebook has, but it would be nice to see them at least have a chance.

**Manton:** You talked about the diversity, and also you mentioned moderation and trying to stay on top of community issues. That's something I'm really interested in. I know back in the old days, most of us didn't really think about that because we're building stuff and we're not really thinking 5 years, 10 years down, what happens if our platform gets big? Pownce had a public feed and you had a lot of places that problems could happen. But I'm wondering if they ever did happen.

**Leah:** Oh, yeah. I want to say, this was not like people weren't thinking about it. In fact, we had our community manager, Ariel Waldman, who blogged about it back in 2007 — the treatment of community. She actually fought back against sort of Ev Williams at Twitter and some of the things that they were doing — the lack of moderation and respect for the community. It's an interesting read now. Looking at things through a different lens, many years later, you're like, oh, wow, this is really early talk about community and moderation. 

**Leah:** But it wasn't that people weren't thinking about those issues. It was that it was a lower priority than scaling and growth and keeping the sites running. Twitter had a lot of scaling problems. So all of these things were more top of mind than community. And nowadays we can sit back and we can say, "Okay, things are running." Facebook and Twitter run. They're not falling over every day. And now we have the opportunity to think more about moderation and content. 

**Leah:** And to be honest, back then I think everyone thought like, "Oh, freedom of speech, blah, blah, blah." But we don't realize a company is not the US government. We don't have the obligation to ensure — like we don't have the same constitution that the United States has. Private businesses are allowed to sort of set their own rules and guidelines. And I wish that more founders and leaders of companies really thought about that. What do you want your community to be like? What do you want your company to be like? I think there are more thoughtful and less thoughtful companies when it comes to sort of these things. So I don't want to say all of them don't think about it, but I think the whole community could benefit from having people thinking about these things more. 

**Manton:** How big was the team when in the middle there, when you sold or before? Because you mentioned having a community manager early on... 

**Leah:** Oh, tiny, tiny. Three founders, support person, back-end engineer, and an engineer. Six people, seven? Something around there. So Pownce never got very big in terms of employees. We were in the process of hiring another person when we were acquired, so we were still tiny.

**Manton:** Six Apart acquired and you went to work there. They had TypePad already. They had Vox. What were your expectations of combining Pownce with the blogging platforms that Six Apart had?

**Leah:** So this is a tough question to answer because there's like what I know now versus what I knew then. So at the time they had TypePad, Vox, and LiveJournal. And what we were really encouraged by was the fact that Vox and LiveJournal were like these thriving communities. 

**Leah:** I guess I should back up and say why we were acquired, which was that 2008 happened. And Ron Conway was probably our main investor. I think he was the biggest investor in Pownce. And he had this whole like "good times are over" thing. RIP, good times. And he was like, "Oh, I'm going to sell off all of these small investments I made." And then there was pressure from Digg... Kevin and Daniel were both employed by Digg full time. And there was this pressure to get them back working on Digg more and stop paying attention to Pownce. So there were these couple of different forces in play and we needed to raise more money in order to sustain the site. So instead, we were like yeah, let's explore acquisitions. Six Apart wasn't the only company we talked to you, but they were the one that we thought would be the nicest landing for Pownce.



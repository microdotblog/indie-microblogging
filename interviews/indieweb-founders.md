**Manton:** Take me back to 2011: the founding of IndieWebCamp. What did that feel like? How you all got together. How the first IndieWebCamp got started.

**Tantek:** You weren't at the Federated Web Summit in 2010, were you? Did you hear about it? Did it even cross your radar?

**Manton:** I assume it did. But that's already been a while. 

**Aaron:** Nine years ago...

**Tantek:** Because I think that's where the inspiration originally came from. 

**Aaron:** So 2010 was the Federated Social Web Summit — in Portland — and that was the invite-only but "you could kind of ask for an invite"-style event.

**Tantek:** Which we now know greatly biases towards people that feel privileged enough to ask for an invite, so it's sort of a bad way to do it. I didn't even put that together until the last year. Yeah, don't do that kind of private conference.

**Aaron:** So I ended up there, Tantek, as well as a bunch of others. It was a fun group, but the thing that we took out of it was that the focus seemed to be on people building things for other people, building specifically platforms. They were coming with platforms and trying to make them work together. Which is a fine goal, but that wasn't my personal interest in it necessarily. So it was more like, "oh, I have this Buddycloud thing, let's make it work with Friendica". Or Diaspora was there. 

**Tantek:** The Diaspora 4 were there, which was cool. That's where I really got to spend time with them.

**Aaron:** And there was also a lot of solving problems in theory without actually testing them out or building something first. And a couple of pretty in the weeds discussions that I ended up sitting in on and be like, this is really complicated. I feel like there is a better solution. That was where SWAT0 the concept was formed as well, right? Interoperability tests between social networks — can someone post a photo of somebody else using a different system be notified that they were tagged in a photo and then a third person comment on the photo and have that comment notification appear on the person who favorited it. Everybody has to be using different software for that test to pass. SWAT0: social web acid test.

**Tantek:** It was actually really hard. 

**Aaron:** Very hard. It still is.

**Tantek:** As far as we could tell no one actually got it to work across different sites. 

**Aaron:** The goal with SWAT0 was to have three different systems interoperating. Several people claimed that they supported everything needed for SWAT0 themselves. But by definition that doesn't solve SWAT0 because you need three different implementations. So there were several people who were like, "I can be every person in this — every role in this test". But then there's no one to test it with, because only one person would do that at a time. And we are still kind of in that situation sadly. It's still a very hard problem. We did in 2015 have a demo of it working between three different recommendations, although each implementation only was able to be one or two of the roles of the three. 

**Manton:** And that was using Webmention? 

**Aaron:** Yeah, exactly. 

**Manton:** So back in 2002 what was the technology to.. It was way after pingbacks and trackbacks.

**Aaron:** Yeah, the thought was the OStatus stack. Atom. Salmon for the responses. 

**Tantek:** PubSubHubbub, I think. 

**Aaron:** I believe so, yeah. For finding the photo in the first place. 

**Tantek:** But Salmon for the notification. 

**Aaron:** Salmon for the notification of the comment. But in order for someone to see it in the first place they would be following an Atom feed, probably, with PubSubHubbub.

**Manton:** And so now Salmon is making a comeback with Mastodon, right? 

**Aaron:**  No, it's already done. 

**Manton:** It did briefly make a comeback and then got replaced. 

**Aaron:** Mastodon ripped out their whole code and replaced it with ActivityPub. So after that event we were like, "okay, that was cool, but we want to focus on people being more empowered individually to participate in this federated network." 

**Tantek:** Everyone got to give lightning talks. That was part of it. 

**Aaron:** Yeah, yeah. 

**Tantek:** Which was great. About any topic, like why they were there and... What was your lightning talk on? 

**Aaron:** Probably location stuff, because I was just starting geolocate at the time. But the sense I got was that the assumption was that in order to participate in a federated social network, you have to be on a platform that supports the protocols. The only way to do that was that if someone built the platform that interoperates with other platforms, and then you as an individual join one of those platforms. There was no "just my web site". 

**Tantek:** Or one-person platform. 

**Aaron:** Or single-person platforms was like: why would you do that? That was the feeling there. That was why we did IndieWebCamp the year after, because we wanted to approach it from the grassroots of: someone should be able to take their web site and be able to use their web site to participate in the same distributed social network — federated social network.

**Manton:** As the conference was wrapping up, did you have a feeling that y'all would probably do IndieWebCamp, or was it making friends and catching up with people.

**Tantek:** We were mostly catching up with people, meeting new people. I was just looking at my notes, because I actually put my entire talk from it on their wiki because it's like that's how it'll survive. Turns out wikis are more persistent than PowerPoint. 

**Manton:** So in that time... 2010 is actually a really interesting time because Twitter had been around for a few years and really gained a lot of steam, and actually a lot of early bloggers — who were blogging all the time in the early days — around 2010-ish they dropped off. They started just doing Twitter. 

**Tantek:** Even just 2009... 

**Manton:** Twitter satisfied that "I'm going to post something". And you can see that. I went back recently and looked at a bunch of people that were doing blogging software. Founders of Blogger, Movable Type, and Six Apart people. And very few of them kept their blog through that period. So could you sense that at the time?

**Tantek:** Totally. Just even personally, the last blog post I wrote on my old blog was in August of 2008. I did not have anything on my own site in 2009. 2009 was a really weird transitional period, because I both saw that happening and I saw it happening to myself. And then the other thing that happened simultaneously — which I think helped — is that Twitter was really unreliable in 2009. We all switched to Twitter and then it got really unreliable. It was so frustrating.

**Tantek:** First of all I'm embarrassed that I'm not posting to my own site anymore, and then I'm frustrated because this damn tool is never up. And that's really where I came up with the idea of, well, I should post to my own site and if I could set up a system where I can always just post to my own site, whether or not Twitter was down, then I can just have my site post to Twitter when it comes back up. And I can abstract away that frustration of their site being down. Abstract away their unreliability, while still getting that participation with friends thing. So 2009 is when I started working on what's now my web site. Launched in 2010. January 1st, I'm like: from now on everything is going on my site first.

**Tantek:** And then the Federated Social Web Summit happened and I was like, "woah, okay". But the platform perspective that Aaron was pointing out. Wait a minute, you don't need to use a whole platform. Everyone can do this themselves. So that was my lightning talk, basically, and it even ended with... I'll show you the summary: use your own site as your identity; publish on your own site; and then syndicate with PubSubHubbub. That's still true. 

**Manton:** And the first one, importantly... The very first principle of the IndieWeb principles is that. Use your own site, own your own content. Domain names are a big part of that. Really the biggest thing. Unfortunately domain names have not changed since 2010. They haven't changed since 2000. It's interesting that something so important, that step one is still really confusing to people. 

**Aaron:** Yeah.

**Tantek:** Oh, that's you're going with that. I thought you were going with like, "they're still around". 

**Aaron:** And it's still just as hard. 

**Manton:** I'm going with: why aren't they easier? Because a lot of what the IndieWeb does, if you look at Microformats and Micropub and all these core parts of the IndieWeb, they're built on HTML and HTTP where we have some control over making things easier and having other standards. 

**Tantek:** Yes. 

**Manton:** Is there hope for making DNS also easier for people, or are we just kind of stuck with this for a while? 

**Tantek:** The irony is I don't know what you're comparing it to. Look at the amount of time it takes you and the form you have to fill out to get a new phone number. I would challenge you to do an AB test. How long it takes to get a new phone number from scratch, not having a phone number, to how long it takes to getting a new domain name. And I would bet that it's actually fewer steps to buy a new domain name. So I definitely sympathize that it could be easier to buy domain name, but compare it to other forms of identity that people take for granted. It is less work to do. Or maybe the hard part is picking a domain name. 

**Aaron:** Yeah, that's part of it. A phone number just gets assigned to you. 

**Manton:** And everybody kind of knows how phone numbers work, I guess. No one's surprise that there's a 3-digit area code, and a 3-digit number, and a 4-digit... Whereas with domain names there's certain things (and IP addresses) that people are surprised by. 

**Aaron:** Getting the domain is the first step. But then once you have it you have to know that you now need to set up DNS on it and point it at a hosting provider. And that's the part that's different from a phone number. Because once you have a phone number, it almost certainly came with a phone. You don't buy a phone number and then assign to a phone. You do that all as one step. 

**Tantek:** It turned out that the equivalent of phone number registrars, all cell phones... It would be as if every domain name registrar — and a lot of them do now — sell hosting. So right off the bat, they're like, "here's a domain name, do you want us to flip on a simple web site for you?" A lot of them do that. That has changed. 

**Aaron:** Yeah. That's true, actually. That has gotten better. It used to be that GoDaddy or Name.com or NameCheap only did domain names. And then they all started adding hosting plans to their product. 

**Tantek:** Which makes sense. 

**Aaron:** It absolutely makes sense. And when you use the hosting plan provided by the registrar it is actually very easy, because it is more like you just go there, type in the domain you want, pay, and then now you have the empty shell to put stuff on. Doing something with the empty shell of a hosting plan is another step, but at least they do make the DNS to hosting step combined into one. 

**Tantek:** Other hosting providers have made it easier to one-key turn on WordPress, turn on Known. I don't know there's a domain name registrar that also has easy hosting that also has a simple turn on a web site CMS. 

**Aaron:** DreamHost does a pretty good job of it. 

**Tantek:** That's true. DreamHost probably has the most pieces that they've put together. And they were the first to do LetsEncrypt automation. Domain name, security, hosting. So that's evolved. It's very impressive to watch, even during the whole eight years of IndieWebCamp.

**Manton:** And comparing it to the phone numbers, if you go get a phone from someone they can always give you a phone number — if you go to Verizon or AT&T. And maybe where we need to be eventually with the web is that any place you can go get a web site can give you a domain name, which is not really true right now. The big companies can, but a smaller webhost can't necessarily. 

**Aaron:** You can, but it's more work as a service provider. There's plenty of domain resellers. I built a system to do that at one point, where we wanted to be able to offer domains as part of the product we were offering. So I found a domain reseller that had an API and hooked it all up. You would come to us and click the button for, "I want this web site with this theme." It worked seamlessly. 

**Tantek:**  Even GitHub should it doing that, right? 

**Aaron:** Right, for GitHub Pages. Instead of just offering GitHub Pages and being able to map a domain to it, why shouldn't they offer their own domain registration. 

**Tantek:** And make a little money. There's incentive there. 

**Aaron:** It would be a no brainer for Micro.blog to offer that feature. Sign up for the Micro.blog account then right there type in what domain you want and it just works. 

**Manton:** I'd love to do that. 

**Tantek:** It's also the kind of thing you could always add. "Yeah, now I'm ready for a domain name.". 

**Aaron:** Yeah, you upgrade your subdomain to a real domain. 

**Manton:** So you had mentioned with the changes in the last seven years... Going back to that first IndieWebCamp. We're just wrapping up IndieWeb Summit 2018. Does it feel the same in terms of the community and what people are excited about? Obviously standards and everything else have evolved. 

**Aaron:** The biggest shift in that context that I've seen between the original ones, specifically, although even from 2014 to now. Now we actually have a lot more stuff working together than we did in 2011, obviously, and even in 2014. At the beginning it was the same goal, the same ideals, but we couldn't demo me commenting on someone's post. That didn't work until way later. And because of that the sessions were all drastically different, because there wasn't a thing to coalesce around except for the ideals of own your data, have a domain name, do stuff on your web site. So if you go back and look the original sessions from 2011 to 2014, it's a wide variety of things. Now at IndieWebCamps you end up with a lot of people who are coming to it and then become aware that there are things that work and then want to learn how to do those things. Now at the beginning of the second day we have the intro to the building blocks session. What is IndieAuth. Get WebMention working. Even in some of the IndieWebCamps there will be a whole track of unconference sessions about those building blocks for the whole day, where it's people who know they want to learn these things that already exist.

**Tantek:** You had a session called "own your phone number". 

**Aaron:** That's right. Yeah, I have actually kept that up. My phone number and my cell phone are completely disconnected. They're not coupled. So my phone number is provided by Google Voice and I forward it to a phone number that I don't know that my cell plan is on. I have no idea what my phone number is — the one on my phone. And I give out my Google Voice number as my identity. 

**Manton:** When as that talk?

**Aaron:** That was 2011. 

**Tantek:** The talks were so varied back then. We were just figuring out so many basics that a lot of the talks were very exploratory. We figured out some things like, "okay, I figured out how to syndicate into Buzz and Twitter, how about other places?" Then there was advocacy for plain text formats and there was a BitTorrent session. 

**Aaron:** Yeah, I think that's the biggest shift I've seen is that there's so much more stuff that's actually working now that's functional. And it means that people are coming and wanting to learn that. And of course there's still the experimental stuff. There was a good set of experimental sessions at this event. But there's a lot more of: we have stuff working now that you can figure out and learn how to use. 

**Manton:** There's two things, too. There's all the IndieWeb-friendly formats and protocols are much more mature and established now, so that you could talk about the building blocks as a real thing. But then there's also... It seems like the software is much further along. A bunch of people will come to the IndieWeb and they use WordPress, because WordPress powers 30% of the internet and it's super popular. But there's still a pretty good mix in the demo sessions and what people are hacking on of WordPress stuff and also "no, I rolled my own". 

**Tantek:** Yeah, in fact lots more rolled their own, which is not representative I think of people out there in general. 

**Manton:** What do you think about the fact that WordPress is a very dominant platform. Is that good because there's an agreed thing there everyone can use the same plugins, or are there any drawbacks? 

**Aaron:** WordPress specifically because it's self-hostable, that benefit ends up overriding some of the other drawbacks of that kind of approach. The danger with something being so dominant.. It's the monoculture problem. We don't want to be in a situation where we just have WordPress instances talking to each other. That doesn't actually solve the problem. 

**Tantek:** Or just have Mastodon talking to each other. 

**Aaron:** Just Mastodon or just Diaspora or whatever, right. That's the danger. That's the thing we're trying to avoid. 

**Tantek:** Because that has lots of even worse consequences. 

**Aaron:** Yes, exactly. And even when it's a friendly company like Wordpress that's behind it, it doesn't matter — the same problems. 

**Manton:** You start to build like platform-specific... It's different than just building for the web in general where anybody can bring their own site and plug in. With Mastodon specifically, it's based on open standards but it also feels very opaque in a way how stuff talks to each other. It's a little more difficult to just build a web site and be compatible. 

**Tantek:** It's also levels of barriers to entry. Because that's one thing that myself and I think a bunch of people at the 2010 Social Federated Web Summit we're frustrated with was a lot of the standards being tossed around — every generation has its own standards — were really hard, like Salmon. I tried to read through the spec and understand what it was doing, and I could not wrap my head around enough of it to even start anywhere coding. 

**Aaron:** I had the same experience at that event. I even then later, a year ago, tried to revisit the spec because Mastodon was using it. I feel like I should be able to have my web site just be a part of this network. I refuse to make a new Mastodon account and treat it as a POSSE destination because that completely defeats the purpose of what Mastodon itself is even shooting for, which is an actually distributed social experience.

**Aaron:** So I was like, "okay, it can't be that hard now". Certainly things have gotten better, and I should be able to just take my web site and add the stuff it needs. I still can't figure it out. And then they went and dropped Salmon anyway and switched to ActivityPub, so I'm glad I didn't spend my time on that.

**Tantek:** It turns out that the difficulty of the standard to implement makes a big difference. Because if it's super difficult then you end up with only a handful — maybe even just one or two people on the planet — that can implement it, and then you get monoculture by default. In effect, not by design. One of the things we realized was that the antidote to that is to make the standards as simple as possible. Literally as dumb and simple, and frankly decomposed. So that's where we came up with the building blocks idea rather than having a stack. And the idea that building blocks is you pick and choose the ones that you need for your use cases. That doesn't mean you're committed to implementing a layer after layer after layer to get to a certain point. That was a big insight. The more accessible the standards are for any developer to build their own solution. That means that the more they're going to get exercised, the more that they'll get good interoperability, the more that they'll be a community around it. Because that's really what it came down to. 

**Tantek:** I think that's kind of where the IndieWeb community started to form — start to really grow and gain critical mass — is the growing number of people that were like, "oh, I can implement that on my web site in an hour or less." And then in a day they could do it amazing things. 

**Aaron:** And it's demonstrated by the fact that like you look at the RSVP list on the event page, there there's like over 20 people who have been able to have their picture show up on the RSVP list, which works by having them publish a page on their own website and send a WebMention to the event page. That's pretty cool. They didn't have to go and read through a whole spec that talks about everything from using an app to publish to your site to then have a federation protocol behind it. They just need know about this much of the whole picture in order to have that work. And that's a quicker win. Now maybe you expand and start working on the rest of the building blocks. 

**Manton:** Webmention is a great example of something that is as simple as it possibly can be. Can't really get that down any simpler. So people get it. Microformats is similar in that it's very approachable and transparent. If you know HTML you can figure out how to do that. You have Microformats 1 and 2, and remind me... Because Microformats predates... 

**Tantek:** ...IndieWeb. 2005. 

**Manton:** And did that launch at SXSW or something like that? 

**Tantek:** Shortly thereafter. I think we had sessions about it at SXSW in 2005, in March. The site launched in June itself. Until then we had just been doing it on the Technorati wiki. And my co-founder of the Microformats.org community, Rohit Khare. He's like, "hey, happy birthday, I bought you a domain name." And I was like, "really, you think this is worth having its own domain name?" That was my actual response. 

**Aaron:** Wow. 

**Tantek:** Because it seemed like such a simple stupid dumb thing. And he's like, "yeah." Okay, I guess we should do this then, and then we set up the site and well, what do you need on a community site. You need a mailing list, you need a blog, you need a wiki. So we set all those up. Since then we've learned that the primary ways of actually making progress are the wiki and IRC channel (or Slack) — an archived IRC channel. But that was definitely a response to, again, complexity. Like the whole RDF world — all that insanity — and the Atom/RSS wars back in the day, and then Atom going to IETF instead of W3C because there was a giant fear that it would just be turned into RDF at W3C. That's how Microformats 1 started. 

**Tantek:** We basically did make it look as dumb as possible. Let's just take the names of the terms from the vCard spec and use them as class names. That was  what I proposed in 2004 at FooCamp. And I ran it by Ray Ozzie at the time, who was like architect at Microsoft or something, but also just from Lotus Notes, you know he has a long history. He's like, "yeah, that could work.". 

**Manton:** So now we're almost 15 years since then. Looking forward, there's a lot of talk about generations — 1, 2, 3, 4 — moving up and making it more approachable and just easier for people to use. Obviously we can't predict 15 years from now. Who knows what's going to be around. Is Twitter going to look the same, are blogs going to be same... 

**Tantek:** Is Twitter going to be around? 

**Manton:** Exactly. There're no guarantees. A lot of people... So much time, they don't remember before Twitter and Facebook and so it's hard to imagine sometime that things things could go away. But they could. They're just web sites. Businesses built by people that make mistakes and do good things sometimes. 

**Tantek:** Yeah, sites that become boring and people move on to what's interesting. I think Facebook really extended their lifespan by buying Instagram.

**Manton:** So moving forward, how soon... Because I'm kind of impatient and I want everybody to blog on their site immediately, like tomorrow, and for it too easy to use. But this stuff takes time. 

**Tantek:** Totally. 

**Manton:** Where do y'all see just over the next few years. How close are we to making this more mainstream or is this going to be just more time churning away building tools, trying to spread awareness. 

**Tantek:** It's kind of hard to predict. I do feel like we're entering a new phase right now. I think we've had two phases, two very long phases of the IndieWeb community so far. One was this I almost want to say like Big Bang phase in the very beginning where there were all these different things coming out. People trying all kinds of different approaches, like Ward Cunningham did his federated wiki project. He figured out a way to do all this Javascript-based wiki federation thing that he loved. And other approaches. But then we started to coalesce around: use your own site, use Microformats. We actually used Ping back for a while until Sandeep Shetty showed up and he's like, "hey, I've got this proposal for a simpler version called Webmention that does this." And everyone in the community was like, "well, that completely aligns with our values of making things simpler." So we instantly adopted it even though none of us knew who this guy was. And then we just ran with it. 

**Tantek:** So the first four years was this explosion of getting basics working. We got RSVPs and events working by 2013. And that was kind of like, "whoa, we federate events and RSVPs," which we were always looking for ways that in the actual things we do, how can we use the technology that we're making. And after that, clearly we need to get these standards — that are barely specified — solid, testable, working, dependable, to reach the next level of stability.

**Tantek:** And then there was the second phase which was the work of making all these standards formal and reliable and secure and handling edge cases. We did that from I would say 2014 through 2017, and a lot of that was done in the social web working group that I was co-chair and Aaron was in, edited a bunch of the documents. Evan Prodromou was also co-chair, from StatusNet. But that was kind of a maturing phase. There were a lot of new features people were figuring out all the time, and new infrastructure like Bridgy during that phase. But I feel like a big part of that second phase was everything that was getting built was getting fed back into fixing the standards. People would build something, they would get to the point where they were like, "hey, this didn't quite work, we have to fix a standard to handle that." Okay, we fix it. They get it working. We have test suites for all these standards. And now when people are implementing things like Webmention or Micropub or whatever they're not really running into new problems. What they're running into is questions of how, not "this doesn't work". So we've reached this level — and I think Microsub, that might be one of the last pieces that kind of wrapping it up. That's why I feel like we're closing on the second phase.

**Aaron:** And IndieAuth, too, because that was only written as a spec this year. Before that it was actually very interoperable, and there are several implementations before, but it was never written down as a proper spec. So that's now this process of let's formalize that. 

**Tantek:** And we even formalized how do we update the Microformats parser spec and the vocabulary. That's been much more formalized as well. So people have an idea that when I proposed something, when can I depend on something vs. what's experimental, and then what's the path. 

**Aaron:** So you mentioned these two phases of... 

**Tantek:** The Big Bang, the amazing explosion of cool stuff and then this sort of maturing of the standards to make stuff work reliably even just amongst theirselves. You mentioned you want everyone to have their own presence. But when I think about that I think, "people want things that are reliable, that just work." And I think this second phase was us doing the difficult plumbing work of the details to make things just work. 

**Aaron:** That leads into what I think is the next phase is getting more people building systems using these building blocks. When that happens, and you're a great example of this...

**Tantek:** Yeah, there's an overlap. I think Micro.blog was evidence that that phase was ready to enter. 

**Aaron:** So now as someone who is building out a platform that is intended for end users... Whereas I'm building my web site. I do not want an end user to use that software. It is not the goal explicitly. But you're building software that is intended for end users. You now have a pattern to follow where if someone else comes along with the same goal and build something, they work together. And so I think in order to reach the goal of people can just use this stuff out of the box, we need more people building tools that are intended to work out of the box for people on the same stacks. And four years ago, if you had come around and started this thing, there wasn't a pattern to follow to make that work across implementations. And there is now, because of the work over the last four years, since 2014, of formalizing these specs, and having that actually hardened. 

**Tantek:** And we also did it the hard way. 

**Aaron:** Totally. 

**Tantek:** We tried to do each spec as its own little building block piece. I would say hard but honestly I think greater chance of long-term success. The traditional approach that architects take is the stack approach or platform approach where they figure out the entire API. The whole thing. If you look at how OStatus happened, or even like ActivityStreams and ActivityPub. That's very much a "we're going to solve the whole problem". And then we'll iterate that whole big thing and then it turns out that's both really hard to do and once again you end up with the problem that there's only a handful of people that can implement it. 

**Aaron:** And also I think more importantly that also has the problem of: if you realize there's a mistake in it, then you have to essentially throw out the whole thing and make a version 2. And Microformats is a good example is this evolution. Microformats 1 vs. Microformats 2... they're completely incompatible. They don't work the same way, but you can still send a Webmention with Microformats 1 markup and it works. Webmention doesn't have to change. So people build out Webmention tools and infrastructure, the thing on top of that is the Microformats to make it actually look good and make ia comment work. Microformats can change and evolve, and Webmention doesn't have to evolve. Whereas when you end up with a monolithic stack, if you're like, "oh crap, we don't like the things we decided for this layer in the stack." We can't just swap out that layer because then the whole stack breaks. That's part of why the approach we've taken is harder, because you have to treat each one independently and evolve each one is on schedule. And they all have their own their change-control process. 

**Tantek:** It looks more chaotic. 

**Aaron:** Yeah, and it is little more overhead in terms of: each spec has its own document and test suite that is for each one specifically. But I do think that's the better approach for a longer term success. 

**Aaron:** We're essentially entering this third phase of now we have stuff, we need the tools built on it, but we also don't want to then four years from now turn around and say to everybody who's built these tools, "oh, we've changed now, we've decided that we're going this whole different approach and redo all your stuff." No, we want to make sure that those are all based on ideas that are technically proven and easily swappable in small pieces if you need. But if we were to suddenly say, "we decided that Webmention doesn't work and we need a third parameter and go fix Micro.blog." You'd be like, "well crap, now what, do I do that, do I abandon it, break interop and continue iterating on my own product?" 

**Tantek:** The other big that happened is that we expanded greatly in Europe. International. I think that really started with... was it 2013, the first Brighton IndieWebCamp? We're looking to try to scale it beyond — and we've done this somewhat in Europe — but I think we want to see more of it. The things in the community running and people running IndieWebCamps and Homebrew Website Clubs without needing to even check with Aaron or me.

**Tantek:** I would be happy to help out as a guide or mentor more than a leader in that respect. And I think that's the way we're going to keep scaling it. And in the next 4 years, I would like to see us in more countries. I would like to see us reach more diverse populations. Maybe people that aren't just in the tech crowds, but people that are not earning as much money, right? Everyone has a phone number supposedly. No matter what you're earning or not. And I even hear from developers of new services that kids just use SMS, they don't even want to deal with e-mail. And so people doing new apps have purely SMS-based sign-up flows and all that. So there's definitely opportunities to reach — to keep innovating and figuring out how can we reach even a broader set of folks in that regard.
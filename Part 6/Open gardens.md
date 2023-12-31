## Open gardens

_“There are never purely technological solutions to societal problems.” — Molly White, [Blockchain Solutionism][1]_

In technology, the _walled garden_ is a platform where one vendor controls distribution. If you want to make an iPhone app, your only choice is for Apple to approve it and sell it in the App Store. If you want to send a tweet, your only choice is to register on Twitter's platform.

Walled gardens like the App Store are user-friendly and developer-hostile. They take power away from independent publishers and put it in the hands of gatekeepers. The problem is exclusivity: there is only one gate, and those stuck outside are unable to distribute the same content. You can make Android apps, but not iPhone apps. Nothing exists outside the walls that closely resembles what is inside.

Apple uses the gate of App Store review to collect a percentage of a developer’s revenue. [In an internal email][2], Steve Jobs wrote that Apple could force developers to use their in-app purchase system:

> The first step might be to say they must use our payment system for everything, including books (triggered by the newspapers and magazines). If they want to compare us to Android, let's force them to use our far superior payment system.

Twitter is also a walled garden. Like the App Store, it is a closed platform with proprietary formats and a limited API. The difference is that Twitter's garden is poorly curated and full of weeds. The walls are in such disrepair it's hard to even tell where they are.

[Mike Monteiro emphasized this frustration in a post][3] about the daunting, insurmountable problems facing Twitter’s leadership team. He talked about meeting in person with Jack Dorsey:

> We discussed Twitter’s role in the world stage. And I admired his vision, but feared his approach. Jack, and to an extent Twitter’s pet porg Biz Stone, have always believed that absolute free speech is the answer. They’re blind to the voices silenced by hate and intimidation. The voices that need to be protected. But anyone who’s ever tended a garden knows that for the good stuff to grow, you have to deal with the bad stuff. You can’t let the weeds choke the vegetables.

The issue isn’t that Twitter doesn’t care. It’s instead a design flaw in the platform. Because tweets don’t exist outside of Twitter, when you’re banned from Twitter, you need to start over with a new format or on a new social network. For this reason, and because their business depends on a large user base, Twitter is hesitant to throw anyone off their service. They’re unwilling to tend the garden for fear of pulling too many weeds.

It doesn't matter who is guarding the walled garden's gate if increasingly no one wants to go inside. So there's a better word than "gatekeeper" to describe what we're really after in building a great community-focused platform. It's "curator". Someone who is responsible for maintaining the best experience for users.

The answer to a walled garden is not to create a platform without rules. It's not outsourcing decisions to algorithms, with recommended users and topics that can be gamed or lead new users astray. That's not enough for the challenges brought to us by massive, ad-based social networks, where fake news and hate can spread quickly.

We need a new approach. Not controlled only by algorithms, but also not a walled garden that limits distribution of content. We need a system that prioritizes curation while preserving the freedom to publish outside of silos, with APIs based on the IndieWeb that are open by default instead of locked down with developer registration.

I think of this as an _open garden_. It's an open platform that also cares deeply about maintaining a healthy environment. Outside of the garden, the soil is the same and the same plants can grow, and you are free to copy flowers and trees from inside the garden and cultivate them yourself or let them grow wild. But inside is well-curated. Inside strives to be a high quality, safe environment.

In my Kickstarter video for Micro.blog, I talked about this for social networking and blogs:

> If we start to separate the publishing from the social network, it unlocks something. It empowers writers to feel like they own their work, even if that's short posts. And it frees social networks to build a safe community, without worrying about censorship, because no matter what the networks do you can always post to a site with your name on it.

The fundamental problem in walled gardens like the App Store and Twitter is that they are closed. If they open up, they could in fact double-down on curation. There would be no need to loosen their quality standards because there's an easy path to publishing without review by using the open web.

I first wrote about this in 2014 in the context of [learning from Beats Music][4]. For Apple to deemphasize their algorithmic top 200 lists in the App Store they would need to focus on curation. Here's what Beats was doing:

> Instead, they have a bunch of people — musicians and writers who deeply care about music — curating playlists. The top 25 playlists in a genre are so buried in the app that I had to search them out just to write this blog post, because they seem to carry no more weight than any other playlist. Much more common are playlists like “our top 20 of 2013”. That’s not a best-selling list; it’s based on real people’s favorites.

After Apple acquired Beats Music, they brought some of those curation lessons over to Apple Music, and later redesigned the App Store with more featured apps and stories. There is only so much they can do, because the foundation of a walled garden is difficult to change.

[Seth Godin highlights][5] how the incentives to curate are not well-aligned with Apple's business:

> Apple gets some zing for a recommended podcast now and then, or for a heavily promoted record, but the same rule is generally true with them–98% of all their content is driven by the algorithm, not a human with something at stake. They don’t care which record you pay for, as long as you pay for something.

Twitter has likewise created an environment that ties their hands on curation, with discovery driven by trending hashtags and retweets. And for each rare time a popular account is banned for hate speech, there are still thousands of trolls who are making life miserable for users. Because there is no alternative, Twitter must allow nearly all content on their service. Because it exists apart from the open web, Twitter must give its worst users too much leeway before banning their account.

The open garden solves this problem. It's the same web inside a platform like Micro.blog as on the rest of the internet. By adopting open standards but also drawing a line across which we can apply community rules, it's possible to build features that protect users.

Even the bigger platforms are starting to realize this. Adam Mosseri, head of Instagram, [talked about the added flexibility from open standards like ActivityPub][6] when a user leaves or is de-platformed from Threads:

> If you’re wondering why this matters, here’s a reason: you may one day end up leaving Threads, or, hopefully not, end up de-platformed. If that ever happens, you should be able to take your audience with you to another server. Being open can enable that.

And with blogs we can go further than taking your followers with you, as Mastodon supports with account migration, by also allowing posts and your identity to move between platforms.

By encouraging the use of personal domain names, when Micro.blog does need to ask a member of the community to leave for violating our guidelines, that blogger can take their domain name and content with them, continuing to post to their own blog but blocked from interfering with the community. The curators of the platform have more freedom to block harassing posts because those problematic users can retreat to their own web site and leave everyone else in the community alone.

To summarize:

* Open gardens have curators instead of gatekeepers.
* Open gardens use standards so that the same formats exist inside and outside the platform.

This is only possible by embracing the open web. I believe it's an important part of the way forward for all great platforms.

[1]:	https://www.youtube.com/watch?v=G0k_GjxuJDM
[2]:	https://www.justice.gov/atr/case-document/file/486656/download
[3]:	https://medium.com/@monteiro/merry-last-christmas-jack-dorsey-59f82c06f02b
[4]:	http://www.manton.org/2014/02/ending_the_app.html
[5]:	https://seths.blog/2019/07/surrendering-curation-and-promotion/
[6]:	https://techcrunch.com/2023/07/05/adam-mosseri-says-metas-threads-app-wont-have-activitypub-support-at-launch/
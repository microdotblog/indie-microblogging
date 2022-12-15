## Discovery

_“Understand well as I may, my comprehension can only be an infinitesimal fraction of all I want to understand.” — Ada Lovelace_

When a platform is just getting started, it’s common to have a “global” timeline: a section of the app that shows all recent posts. New users can browse the timeline to get a sense of what people are posting. If something looks interesting, they can follow that person. It’s a useful discovery tool.

Eventually the platform outgrows the global timeline. If the platform is successful, there will quickly be too many posts to keep up with, so it becomes a burden instead of useful. The timeline will have to be just a snapshot of random posts, and later disappear altogether.

There’s also the issue of clutter. Without filtering, the global timeline might contain test posts and other garbage that isn’t particularly welcoming to new users. It might expose hateful or harassing posts.

With Micro.blog we tried something different. Instead of showing all new posts, the Discover section is a curated timeline. We manually include posts in the timeline to give new users a slice of the activity on Micro.blog. It’s a place to find posts and users to follow.

Would a curated timeline scale to the number of tweets that Twitter processes every minute? No, but we never want to be that big, because big platforms are inherently part of the problem, no matter the best intentions of their founders.

Small companies like Micro.blog can do take a different approach that wouldn’t work for others. It’s something that Paul Graham captured in his famous essay [Do Things That Don’t Scale][1], reminding early startups that they don’t need to build something that can reach scale right away, because chances are they’ll never get very big:

> Tim Cook doesn't send you a hand-written note after you buy a laptop. He can't. But you can. That's one advantage of being small: you can provide a level of service no big company can.

[In her post][2] about how we curate Discover, Jean underscored this point that we do this by hand:

> You control the posts on your own blog, and when you choose to follow someone, you see all of their own posts in the timeline. But for Discover we want to provide an easy-to-skim cross section of posts, so the culling is done by hand: no algorithm, no upvoting, no promotions.

Instagram also had an early focus on manual curation, featuring photographers that they wanted to highlight on the platform. Instead of any random junk picked by an algorithm because it was popular, curation by the Instagram team set the tone, helping inspire what kind of photos would be posted by others.

As Sarah Frier wrote in No Filter:

> Because Instagram didn’t have an algorithm or any way to re-share photos, there was no natural way for content to go viral. So Instagram employees had the opportunity to decide for themselves what kind of user behavior to reward, handpicking interesting profiles to highlight on their company blog.

It's an approach that more platforms will return to as they become overwhelmed with the viral spread of the wrong types of posts. They don't want to be known for misinformation and hate speech.

[Ben Thompson wrote about this on Stratechery][3], that users are not guaranteed promotion on social networks:

> There is no right to be promoted, by individuals or by algorithms; on the contrary there is the most responsibility to moderate what is promoted. This is where Facebook and YouTube deserve the most scrutiny.

---- 

Micro.blog doesn't have special support for hashtags. It doesn't automatically link them. There's no global search yet. While Micro.blog users can include hashtags anyway, especially if they are cross-posting to Twitter, I've found that the timeline is much cleaner and readable without hashtags.
 I'm not saying we'll _never_ have hashtags. But I'm not in a particular hurry to introduce native support for them. (Once a feature is added, it can't easily be taken back. So we try to be deliberate in everything we do.)
 Hashtags and Twitter trends go together. They can be a powerful way to organize people and topics together across followers. But they can also be gamed, with troublemakers using popular hashtags to hijack your search results for their own promotion or unrelated ranting.
 It's the organizational and discovery aspect of hashtags that I most wanted to bring to Micro.blog. At the beginning of 2018, there were several discussions on Micro.blog about book clubs and reading, and this seemed like a perfect topic to experiment with. I've also noticed that people love to include an emoji in their microblog post as a kind of theme indicator — everything from 📚 to 🏀.
 So we introduced a search collection using emoji, starting with books. Just include 📚 with your microblog text about a book you're reading or related topic, and your post will automatically be collected on `/discover/books`. There's also an emoji link at the top of the Discover section in the iOS and Mac apps.

People liked this enough that we started to generalize it and surface other topics. There are dozens of new emoji that Micro.blog tracks, like 🧶, ☕️, or 🏳️‍🌈. There is a community page maintained by Jason Burk with suggestions for new emoji that Micro.blog should support.

There is a bit of a chicken-and-egg problem with some less common emoji. Tagmoji in Micro.blog should reflect what emoji are actually being used, but sometimes it helps to add a tagmoji to Discover first, as a bootstrap to get more people to use it.

This splits off some discussions from the main Discover section, making it cleaner. It’s how we can scale the curated parts. There could be teams of curators who are only focused on their own section, so the task of keeping an eye on Micro.blog never feels overwhelming.

---- 

The tagmoji for 📷 is special. It doesn’t automatically collect any post that uses the 📷 emoji. That would be too limiting, when there’s already a good way to know if something contains a photo: the `img` tag.

However, we don’t want to include every image in 📷 automatically. There could be sensitive photos that would be shocking and not all-ages appropriate. There could be many screenshots and other non-photos. While including some of those is good, most of the photos should be actual photos. They should inspire.

So like the main Discover timeline, 📷 is hand-curated. It is a parallel collection to Discover, with some of the same posts. But it can contain many more photos than Discover, since it’s better for Discover to have a mix of both photos and text microblog posts.

We can also present the photos in new ways. On the web in Micro.blog, there’s an option to show a grid of photos:

![][image-1]

Sunlit, our companion iOS app for photos, can also pull from the photos feed. It uses this for the Discover tab inside the app.

---- 

Mastodon also has limited search. Mastodon prevents full-text search: Explained [on Twitter][4]:

> Prevent harmful behaviours like namesearching or finding people to harrass based on keywords. If you want your post to be found based on keywords, you use a hashtag.

Mastodon still has a global timeline. But you have to accidentally find the posts instead of looking for them.

Instagram disabled the recent hashtags view leading up to an election, to prevent misinformation from spreading quickly. [They said][5]:

> Starting today, for people in the U.S. we will temporarily remove the “Recent” tab from hashtag pages. We’re doing this to reduce the real-time spread of potentially harmful content that could pop up around the election.

Because there would be no recent unfiltered posts where anything can surface, only the top posts that have been reviewed by Instagram would appear for the hashtag. It is a more curated solution, where posts are reviewed before they appear instead of after, when it might be too late to fact-check a post.

[In an interview with Kara Swisher][6] for the Sway podcast, Snapchat founder Evan Spiegel talked about the concern that harmful videos might go viral. They focused on building a platform that would allow human curation of viral videos because those videos would reach as many people:

> And on the other hand, with broadcast content, the government has applied a much higher standard to what you’re allowed to broadcast on television, for example. And so, we’ve built that into our platform with our content guidelines. And that’s why, as I mentioned, we were concerned about a platform that essentially allows videos to go viral. And we really had to build a lot of this moderation infrastructure where humans actually review the content that’s reaching a large audience.

It’s okay if every platform has a different approach to curation. Some platforms like Micro.blog make it difficult for posts to spread virally, and others like Snapchat or Facebook may catch the viral spread and throttle it down if it’s harmful content or misinformation. What is not okay is to have no curation at all, with popular trending keywords and posts spreading like fire, fueled by algorithms unchecked.

[1]:	http://paulgraham.com/ds.html
[2]:	https://micro.welltempered.net/2019/06/13/curating-the-microblog.html
[3]:	https://stratechery.com/2019/why-cloudflare-matters-the-absence-of-gatekeepers-promotion-versus-moderation/
[4]:	https://twitter.com/joinmastodon/status/1460692720561934340
[5]:	https://twitter.com/InstagramComms/status/1321957713476280320
[6]:	https://www.nytimes.com/2021/05/20/opinion/sway-kara-swisher-evan-spiegel.html

[image-1]:	https://book.micro.blog/uploads/2020/0b23018e05.png "Screenshot of Sunlit photos grid"
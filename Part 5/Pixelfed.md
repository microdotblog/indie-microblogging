## Pixelfed

Mastodon has inspired developers to create additional new services that can be more open versions of popular platforms. Bookwyrm is a book sharing site with features similar to Goodreads. PeerTube is a video sharing site. Pixelfed is a photo sharing site based heavily on Instagram's UI, but compatible with Mastodon.

Pixelfed developer Daniel Sup first heard about Mastodon in 2016. He was coming from Statusnet, an early federated platform known for its technical implementation if not necessarily its UI, and Daniel found Mastodon’s UI a refreshing change.

I interviewed Daniel Sup over email for this book and he described how the development of Pixelfed started:

> Around 2016 I started working on a GNU/Social successor using the Laravel framework. I picked it back up in early 2018 and made a lot of progress for a few months until I started implementing federation support. That is when I realized I made a mistake with the database schema, it would require a significant refactor [0]().

> At that time I had discovered Pleroma and decided to research other social networks, two weeks later I shared the first screenshot of Pixelfed.

Like Mastodon, Pixelfed is open source, so developers can run their own versions of it. The original instance, `pixelfed.social`, stopped accepting registrations after about 10,000 users. Developer @dansup [posted about the news][2] in May 2019:

> It was a tough decision to make, I think it will pay off in the long run 😉

The goal was to accelerate the adoption of other instances and further underscore the need for working federation between Pixelfed and Mastodon. Because most people's instinct is to join the "first" instance, by default that instance will become much larger than any other. This is what has happened with `Mastodon.social`. By forcing new users to find a new instance, it spreads the load around, creating smaller communities.

Sup also told me about how well he think the decision was working:

> I'd say it worked out as expected, we are seeing overall growth across instances even as pixelfed.social active users declines [1](). I've seen a few single user instances, once our invite system is shipped I expect we'll see more closed group instances.

Pixelfed looks remarkably similar to Instagram. Where Instagram is still primarily used from mobile phones, though, Pixelfed started as a web interface. It supports posting from the web, including applying filters to photos:

![][image-1]

[In early 2020][4], Pixelfed also added a new featured called Restricted Mode that makes a personal instance more suitable to be privately shared with family and friends:

> Restricted Mode will allow you to require authentication for every page and disable federation support with a single command.

By disconnecting your Pixelfed instance from the larger network of Pixelfed and Mastodon instances, you can use it like a personal version of Instagram. This again gets us back to smaller social networks, easing the transition away from ad-supported silos. It also may be appealing to Facebook users who want a private way to share photos, which has not been a major focus of either Micro.blog or the IndieWeb.

Sup would also hang out in the IndieWeb chat, and I asked him about the opportunity to bring more of the IndieWeb principles and formats to ActivityPub-based apps like Mastodon and Pixelfed. “I believe adding IndieWeb principles and specs like MicroPub to Pixelfed aligns with our long term goals,” he told me.

Large platforms, even if they are backed by open standards, should be avoided if your identity is inseparable from that silo's domain name. Be careful that you aren't quitting one silo (Instagram) only to join another silo (a large Pixelfed instance).

Rather than looking for "another Twitter" or "another Instagram", we should look at the plumbing behind Mastodon and Pixelfed and support that with indie blogs. That plumbing is mostly referred to as ActivityPub, although Mastodon is really a blend of multiple APIs like WebFinger, ActivityPub, Atom feeds, and even some IndieWeb formats.

[2]:	https://mastodon.social/@dansup/102166878559849519
[4]:	https://mastodon.social/@pixelfed/103542563320249737

[image-1]:	https://book.micro.blog/uploads/2020/3d2b9de6dd.png
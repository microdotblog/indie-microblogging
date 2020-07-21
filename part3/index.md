# Part 3: IndieWeb

The idea for IndieWebCamp came out of the [Federated Social Web Summit](https://www.w3.org/2005/Incubator/federatedsocialweb/wiki/Federated_Social_Web_Summit_2010) in 2010. Held in Portland, this conference was invite-only, attracting primarily developers who were contributing to platforms such as StatusNet, OStatus, and Diaspora:

> A one-day summit by those implementors working on building the federated social web. This means building upon open web protocols that allow for various web projects to interoperate.

Co-organizer [Evan Prodromou blogged](https://web.archive.org/web/20100715062843/http://status.net/2010/07/13/what-is-the-federated-social-web) about how current social networks were too isolated from the rest of the web, with little or no interoperability:

> From the point of view of a typical social web site, if you don't have an account on that site, you don't exist. The only way for your friends on that site to interact with you is if they invite you to join the site.

But Tantek Çelik and Aaron Parecki felt the event was too focused on _platforms_ interoperating, especially between larger companies, and not focused enough on _personal_ web sites being able to participate in social networks. The evening of the last day of the conference, they talked about how they could refocus the conversation around owning your own data.

The phrase "indie web" had been used before. John Gruber used it [in a tweet a year earlier](https://twitter.com/gruber/status/3429789407) in 2009:

> Mark Pilgrim’s “Dive Into \_\_\_\_” is one of the best brands of the indie web.

[Tantek Çelik also referenced](http://tantek.com/2010/123/t2/blogger-turned-off-ftp-what-indie-web-diso) "indie web" when commenting on Blogger turning off publishing to self-hosted blogs:

> Blogger turned off FTP May 1st http://blogger-ftp.blogspot.com Who/what will step up for the indie web?

By the end of 2010, Amber Case and Crystal Beasley had joined Tantek and Aaron to help organize an event around the IndieWeb, and the first IndieWebCamp was held in Portland in the middle of 2011.

Over the years, IndieWebCamp as a term describing both the conference and the movement has evolved to simply "IndieWeb". The IndieWeb usually describes the part of the web that is made up of personal blogs and smaller, independent platforms, as well as the community that works to forward the mission and build new tools.

IndieWebCamp as a 2-day event is still the way that most people in the community get together, with several IndieWebCamp events held throughout the year in the United States and Europe. IndieWebCamps are usually over a weekend. The first day is for sessions on topics that are brainstormed by attendees. The second day is a hack day to work on projects.

I had never attended this style of un-conference before my first IndieWebCamp. It's often called BarCamp-style. BarCamp conferences started in 2005 and were originally a reaction to the invite-only FooCamp organized by Tim O’Reilly. BarCamps were open to anyone and often centered around web technologies. The Federated Social Web Summit was also a BarCamp-style conference.

While it’s less structured than a traditional conference that has fully planned sessions and prepared talks, the informal nature of IndieWebCamp lets the conference adapt to what attendees that day actually want to talk about. Session ideas are proposed on sticks notes that can be moved around to schedule the day.

![](https://book.micro.blog/uploads/2020/cef6b1bb0e.jpg "Sticky notes for session planning at IndieWebCamp Austin 2017")

Many of the details in the formats we’ll cover in this book started as open discussions in these kind of sessions, then iterated on throughout the year in the IndieWeb chat and wiki.

Once a year, a larger IndieWebCamp called IndieWeb Summit is held in Portland. Once or twice a month, regular local meetups are held in many cities. Those local meetups are called Homebrew Website Club, as a nod to the tinkerer culture of the old Homebrew Computer Club, or simply IndieWeb Meetup.

IndieWebCamps and meetups can be online too. In the wake of COVID-19, most in-person meetups were cancelled. Instead of IndieWeb Summit 2020, organizers held IndieWebCamp West, an online version using Zoom, chat, and the IndieWeb wiki — many of the same tools that had already been used for in-person events to allow for remote participation.

---- 

At IndieWeb Summit 2019, [co-founder Tantek Çelik opened the conference](https://archive.org/details/indieweb-summit-2019-state-of-the-indieweb) to talk about the state of the IndieWeb, including a major story that had been written for The New Yorker by Cal Newport. Tantek said:

> We got some amazing press this past year. IndieWeb has hit the mainstream. The New Yorker covered an article — literally titled "Can 'Indie' Social Media Save Us" — and essentially immediately referenced the IndieWeb.

There's one sentence [in Cal Newport's article](https://www.newyorker.com/tech/annals-of-technology/can-indie-social-media-save-us) that I keep going back to, and that underscores so much of what the IndieWeb is about:

> The Internet may work better when it’s spread out, as originally designed.

This is the spirit of the IndieWeb. It's okay to have centralized services to make software easier for people, because it's too much to expect that everyone should run their own server. The web can be "spread out" on multiple layers: a more diverse set of platforms, so that not all the power is concentrated in a couple massive platforms like Facebook; and more personal domain names, so that even if Micro.blog hosts thousands of blogs, each one has its own identity on the web and can be moved.

The next few chapters will outline the most important IndieWeb formats and protocols. While there is broad agreement on the principles of independent web publishing across the IndieWeb and the origins of Micro.blog, Micro.blog itself was devised separately from the IndieWeb. Increasingly as I was developing Micro.blog, there were so many parallels between what I was building and what the IndieWeb was doing, that I jumped at the chance to incorporate as many IndieWeb protocols and formats as possible.

The IndieWeb had already laid the foundation. There are significant new parts of Micro.blog that were inspired fully by the IndieWeb.

But there are certain areas where we diverge slightly. Micro.blog makes heavy use of JSON Feed, for example, while the IndieWeb often prefers a JSON representation of Microformats. The IndieWeb also documents many post types — RSVPs and check-ins — that are not strictly needed for microblogging.

Indie microblogging and the IndieWeb are complementary. We share the same priorities. I've helped organize 3 IndieWebCamps in Austin and regularly try to promote standards coming out of the IndieWeb.

---- 

The formats and protocols that the IndieWeb community builds on are referred to as "building blocks". There are three building blocks in particular that I consider the pillars of the IndieWeb:

* **Microformats:** A markup format using CSS class names to add metadata to web pages.
* **Micropub:** An API for posting to a web site.
* **Webmention:** A protocol for notifying another web site that you've written about one of their posts.

There are additional APIs, such as WebSub (a way to subscribe to a feed to avoid the delay of polling) and Microsub (for building reader apps). We'll discuss WebSub and Microsub more in Part 5, in the context of decentralization and real-time notifications.

The rest of this part will focus on Microformats, Micropub, and Webmention. But first, let’s go through why we blog — the value of owning our content and making it last.
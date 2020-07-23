## Silos

_"Big technology platforms are now singular points of failure as much as they are single points of protection against malicious intent.” — [Om Malik](https://om.co/2020/07/16/more-than-just-a-twitter-hack/)_

There's a bit of a paradox with silos in terms of permanence. Silos that have withstood the test of time, like YouTube, can be stable places to store content. But so many silos fail, the more common outcome is for you to lose everything you've posted there.

The [IndieWeb documents several characteristics](https://indieweb.org/silo) of a silo, such as requiring an account, only allowing interaction with other silo members, and limiting the type of content you can post.

Not all centralized services are silos. The key trait of silos is _isolation_. Silos wall-off and limit our control over content, usually by storing all content at their own domain name rather than allowing personal domain names.

Using silos, we give up control, no longer having power over the URLs of our own content. Frank Chimero wrote about trading away this control for convenience [in an essay about web design](https://frankchimero.com/writing/the-webs-grain/):

> Up to a point, swapping autonomy for ease is a pretty good trade: who wants to run the math on their accounting books or call the restaurant to place a delivery order? But if taken too far, convenience becomes a Trojan Horse. We cede too much control and become dependent on something we can no longer steer. Platforms that promised to bring convenience to a process or intimacy to a relationship now wedge themselves into the transaction as new middlemen. Then, we’re left to trust in the benevolence of those who have the power to mold our dependencies.

Facebook, Twitter, and Instagram are silos that promise ease of use, but they don't mention what we give up by using them. Medium.com has also increasingly become a silo through pivots away from its roots around blogging.

At first I had resisted adding cross-posting to Medium from Micro.blog because Medium might be someone’s primary blog, so it made more sense for you to post directly to Medium yourself. Then you could add the RSS feed to Micro.blog, so that posts show up in the Micro.blog timeline.

But then [Medium discontinued support for custom domain names](https://help.medium.com/hc/en-us/articles/115003053487-Custom-Domain-FAQ):

> As of November 2017, Medium is no longer offering new custom domains as a feature. Instead, you can create a publication on Medium that will live on a medium.com/publication-name URL.

If you can’t even have a domain name for your blog, it’s clear that Medium is much less a true blogging platform and really just a social network for long-form content. It’s a very poor solution for anyone who wants to own their content, but it can still be a natural choice to cross-post your blog posts and reach Medium’s audience.

The IndieWeb has a special acronym for cross-posting: [POSSE](https://indieweb.org/POSSE). Post (on your) Own Site, Syndicate Elsewhere. It emphasizes starting at your own site first before cross-posting to other silos.

When you enable Micro.blog cross-posting to Medium, Micro.blog takes the HTML of your post and sends it to Medium. It supports titled essays or short microblog posts without a title.

[Dave Winer wasn't optimistic](http://scripting.com/2017/08/24.html#a112323) watching Medium change:

> We're in the long tail of the demise of Medium. They'll try this, and something else, and then another thing, each with a smaller probability of making a difference, until they turn it off.

This concern with Medium is representative of many silos. Because they defaulted to Medium-branded user blogs on medium.com instead of your own blog at a personal domain name, there was a risk that if Medium didn't work out as a business, many great posts would disappear along with the service. You might get more readers in the short-term, but it's a bad trade-off when links break and you have to start all over again.

[Nick Heer wrote about](https://pxlnv.com/blog/kinja-medium-sameness/) the "sameness" of Medium sites — how the sites blur together as just pages on Medium's platform. Several prominent sites have left:

> Earlier this year, _Film School Rejects_ and _Pacific Standard_ [moved away](http://www.poynter.org/2017/after-being-wooed-by-medium-some-publishers-are-beginning-to-leave/459998/) from the platform; this month, the Awl announced that they [went back to WordPress](https://www.theawl.com/2017/08/somethings-different/) with their old custom theme. The _Ringer_ and _Backchannel_ also [left Medium](https://gloss.xyz/media/the-awl-leaves-medium-turns-off-the-platforms-lights/). Once again, I can tell those sites apart from each other.

I think Medium has good intentions. But the premise was wrong, with an emphasis on `medium.com/@username` URLs that aren't portable, and no way to get a custom domain. Medium is now stumbling forward, trying to find the right path because their foundation isn't right.

Different silos will have different strengths and impact on the web, but they usually share these qualities:

* Content lives at the silo's primary domain name — facebook.com or instagram.com — instead of your own domain name.
* Content is not well-connected to the rest of the web. You can link to other content, but the silo encourages you to put many different types of content directly on their platform.
* Content is often interspersed with ads. Decisions about what features a silo will support are then driven by increasing the stickiness of the platform and ad revenue. Some silos like Flickr may be supported by premium subscriptions instead of ads.
* Content can be exported but it's usually in some custom format specific to that silo rather than a common format that could be used across multiple platforms.

Silos should not be the primary place to store your content. If you want to stay engaged with a community on a silo, you should post to your blog and then cross-post to the silo, or comment on posts on the silo in addition to your main web site.

Silos can often make good mirrors for your content. By cross-posting automatically to a silo, you create a copy of your posts that can be used not just for discovery for users on that silo, but also as an extra backup of your posts.

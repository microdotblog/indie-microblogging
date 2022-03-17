## Cross-posting

_“Everything has been said before, but since nobody listens we have to keep going back and beginning all over again.” — André Gide_

When App.net was first taking off, many microbloggers struggled with how to decide where to post their short-form writing. Should they post some topics to Twitter and others to App.net? Should they cross-post everything to both services? At the time, there was an informal consensus that cross-posting was a cheat. It couldn’t take advantage of each platform’s strengths, and followers might often see the same post twice.

I now believe that cross-posting is a good thing. Photos, as one example, are frequently cross-posted to both Instagram and Facebook. Tweets can be sent to Twitter as well as our own blogs. Years from now you end up with an archive of all your short-form writing at your own domain by default.

Many apps like Instagram or Swarm support and even encourage cross-posting, making it easy to share out from their platforms. It’s good for developers because it helps spread knowledge of the publishing app, and it’s good for writers because it means there are multiple copies of our content.

In her book about the founding of Instagram, No Filter, Sarah Frier described how Instagram used cross-posting to stay connected with other services while growing Instagram’s own network:

> What if they made a social network that came with an option to deliver your photos to Foursquare, Facebook, Twitter, and Tumblr all at once? Playing nice with the new social giants would be easier than competing with them. Instead of having to build a network from scratch, the app could just piggyback off already-established communities.

The goal with Micro.blog is for us to get back to our roots with blogging — to write on our own web sites first, not as an afterthought to Twitter. Cross-posting is an important bootstrap for that.

The IndieWeb’s [POSSE][1] is an acknowledgement that we don’t always want to completely ignore the big social networks. It’s pragmatic:

> POSSE is about staying in touch with current friends now, rather than the potential of staying in touch with friends in the future.

With cross-posting, we can prioritize posting to our own site, while still staying engaged with existing friends. Social networks may come and go, but the canonical version of our posts live at our own indie microblog.

### Setbacks

At one point it looked like Facebook was serious about creating a platform with as much access through APIs as possible. After the 2016 election and Cambridge Analytica, Facebook started to scale back their APIs. It also became unlikely that they would add to the Instagram API, which had never allowed cross-posting _to_ Instagram from other apps, only _from_ Instagram.

Facebook turned off API access for creating new posts unless they were sent to a Facebook page. I adapted Micro.blog to that change, but it already severely limited the usefulness of cross-posting to Facebook. Ryan Barrett, creator of the Brid.gy service, disabled all Facebook support after that change:

> Facebook’s [moves to restrict its API][2] to improve privacy and security are laudable, and arguably the right idea, but also mean that users can no longer use third party apps like Bridgy to create posts.

After Facebook required Micro.blog to re-apply for even this limited access to posting to Facebook pages, we were rejected and had no choice but to remove the feature. I hoped that by officially saying goodbye to Facebook support we could focus on making the other cross-posting options in Micro.blog more robust.

The dependency on other APIs can already be like a whack-a-mole game of adapting to changing APIs. Early Twitter apps would stop working if they weren't updated to version 1.1 of their API, not to mention the developer-hostile policy changes that could obsolete some apps. There were similar upgrades necessary when LinkedIn redesigned their API.

Facebook went beyond just changing their API. They actually removed basic functionality.

Facebook and Instagram are at odds with the principles of the open web. I never want to remove a Micro.blog feature that users find valuable, but in this case we had little choice, and it’s best for Micro.blog to move on from Facebook cross-posting.

### Usernames

When I first set up cross-posting, I decided to dust off a test Account I wasn't using: `@manton2`. I considered it an experiment and didn't want to continue to post to my original Twitter account.

You may want to use an existing Twitter account and stay active on Twitter, replying to posts and occasionally reading the timeline. Or you may want to disengage with Twitter and have your account as more of a one-way communication from your blog.

Seth Godin, author or Purple Cow and The Dip, among other popular books, has been blogging every day for years. He chooses to not interact with Twitter at all, only mirroring his blog posts to a special `@sethsblog` Twitter account.

In [an interview with Gary Vaynerchuk][3], Seth talked about why he blogs instead of using social media:

> If you want to develop — to get through the dip, to be the best at something — you're going to have to say "no" to a lot of things. [...] When Twitter came along I said, "I could be really good at this, because I'm early." But I would have to use my blogging time to be pretty good at this.

It's about focus. There is not enough time to do _everything_. By focusing on our blogs, we're creating content that can last, that we can own, but we can still use cross-posting to reach an audience on larger platforms like Twitter.

Inspired by Seth Godin, I renamed my Twitter account to `@mantonsblog` to better reflect that posts start on my blog. My attention is on Micro.blog, and I'll only occasionally check replies on Twitter.

### Setting up cross-posting in Micro.blog

Micro.blog is based heavily around RSS and JSON feeds. As Micro.blog processes the posts in a feed, it adds the posts to the Micro.blog timeline, and it is also during this processing that it can send the posts to other social networks.

To configure cross-posting, click Account → "Edit Feeds & Cross-posting". This page shows the feeds for your account. For sites hosted on Micro.blog, it will usually just include 1 feed, but you can also add feed URLs for external blogs outside of Micro.blog.

![][image-1]

Next to the RSS feed you would like to automatically cross-post, just click the "Add Twitter" link. You'll be prompted to authorize your Twitter account, or an account on another service.

Once enabled, any new posts (after you enable cross-posting) will be sent to Twitter, with these rules:

* Short posts without a title, and less than 280 characters, will be sent to Twitter unmodified.
* Longer posts without a title, but longer than 280 characters, will be truncated with a link back to your microblog.
* Posts with a title, regardless of length, will be sent to Twitter using the title and a link back to your microblog to read the full post.
* Up to 4 photos embedded in a post are automatically downloaded and attached to your tweet. Photos should be larger than 200×200, to avoid accidentally cross-posting small buttons and tracking images that some blog systems include.
* The first link in a post will be appended as a URL to the end of the tweet.

Similar rules apply for Medium, LinkedIn, and Mastodon, but with different length restrictions since the 280-character limit is specific to Twitter.

You can continue to reply directly on Twitter, and also on Micro.blog. Replies posted directly on Micro.blog aren't included in your microblog RSS feed, so they won't be sent to Twitter.

### IFTTT

Another option for cross-posting is a service like IFTTT. This is a good choice if you need to post to platforms that Micro.blog does not support.

[IFTTT][4] — short for "if this, then that" — is a great solution for connecting different web services together. With just a few clicks, you can configure IFTTT to take the microblog posts in your RSS feed and automatically send the post content to Twitter.

Start by [creating a new applet][5]. For the first part — the "if this" — select the [RSS Feed channel][6]. Add a "New feed item" trigger, which will run the IFTTT recipe whenever the RSS feed includes a new post.

![][image-2]

Enter the URL for your RSS feed. On Micro.blog, the default RSS feeds are at `yourdomain.com/feed.xml`. If you only want to cross-post from a specific category on Micro.blog, you can use the format `yourdomain.com/categories/my-category.xml`.

![][image-3]

The second half of the recipe uses the [Twitter channel][7]. Configure the "Post a tweet" action to take the RSS item content and send it to Twitter as the tweet text.

![][image-4]

In the tweet action, you want to replace the text with the special `{{EntryContent}}` value. This will take the full text from the RSS feed and include it in the tweet.

![][image-5]

You can continue to reply and favorite directly on Twitter, and also on Micro.blog. Replies posted directly on Micro.blog aren't included in your microblog RSS feed, so they won't be sent to Twitter.

### WordPress

If you're using WordPress, you can also use plugins to handle cross-posting. The Jetpack plugin has a feature called Publicize that connects to Twitter and other platforms. You can enable it in WordPress under Jetpack → Settings → Sharing.

There are also more specialized plugins, such as [WP to Twitter][8].

The IndieWeb-friendly [Syndication Links][9] plugin by David Shanske will also keep a record with each post for where it was cross-posted to. That way you can add links or icons from your blog post to the same post on other platforms.

Syndication Links also improves the integration between Micro.blog and WordPress. [Chris Aldrich blogged][10] about the recent update:

> ...this plugin now provides for a per-post decision about exactly what content to send to Micro.blog. It also naturally provides a syndication link from your site back to the Micro.blog post.

Cross-posting is an optional part of indie microblogging. It’s a good way to keep one foot in the door of other social networks if you're not ready to leave them behind, with the added bonus of having an extra copy of your posts on the web.


[1]:	https://indieweb.org/POSSE
[2]:	https://developers.facebook.com/blog/post/2018/04/04/facebook-api-platform-product-changes/
[3]:	https://www.youtube.com/watch?v=D65-9sz7V0g
[4]:	https://ifttt.com/
[5]:	https://ifttt.com/create
[6]:	https://ifttt.com/feed
[7]:	https://ifttt.com/twitter
[8]:	https://wordpress.org/plugins/wp-to-twitter/
[9]:	https://wordpress.org/plugins/syndication-links/
[10]:	https://boffosocko.com/2019/12/15/syndication-links-now-supports-per-post-syndication-to-micro-blog-from-wordpress/

[image-1]:	https://book.micro.blog/uploads/2020/f7e6a1a29d.png
[image-2]:	https://book.micro.blog/uploads/2020/19bc72e9f6.png
[image-3]:	https://book.micro.blog/uploads/2020/7787779d2a.png
[image-4]:	https://book.micro.blog/uploads/2020/a26199d375.png
[image-5]:	https://book.micro.blog/uploads/2020/730c6548b5.png
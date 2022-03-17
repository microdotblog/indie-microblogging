## RSS for microblogs

Even if RSS doesn’t need to change, some types of apps would be better off if we took a fresh look at the elements in an RSS feed. What is really needed, and when faced with multiple “correct” options, which should we choose? As more writers embrace microblogging, it’s an opportunity to simplify our feeds and tools.

There have been proposals for _adding_ things to RSS to make it more suitable for microblogging and social networks. RSS 2.0 uses XML namespaces to add new types of data to a feed. Dave Winer in 2012 proposed his own `microblog` namespace with additions such as linking to the archive of someone's microblog posts. Dave [blogged at the time][1]:

> It understands full links vs shortened links. It defines a calendar-structured archive, so you can store all your posts in RSS format. This has been a long-standing problem, and this solution really works.

None of these suggestions are strictly necessary for microblogging with RSS, though. Some features, such as referencing archived posts, can also be accomplished with [RFC 5005](), which documents how to support paginated RSS feeds to include many more posts than would normally be in a default feed.

Instead of adding things to RSS, we should be taking away — simplifying the required elements to make feeds more readable and consistent.

This chapter is my proposal for a bit of housekeeping around microblogging. It’s not a new format. It’s just a guide for producing the best RSS. I’ve divided this proposal into 3 sections below.

**Minimum viable elements**

Look at the average RSS feed and there’s a lot of junk in it that most RSS readers ignore. While there’s nothing wrong with including extra XML elements, we should strive for a feed that is simple enough to be easily read. The fewer redundant and unused elements, the more consistently that different RSS readers will interpret it.

Here’s an example of an RSS feed whittled down to its essential elements. Most feeds should look like this by default, and only add additional elements from the RSS spec or RSS extensions when it’s absolutely required (such as the enclosure element for podcasting).

	<rss version="2.0">
	 <channel>
	   <title>Manton Reece</title>
	   <description>Manton's weblog.</description>
	   <link>http://www.manton.org/</link>
	   <item>
	     <title></title>
	     <description><![CDATA[
	       <p>Hello world.</p>
	     ]]></description>
	     <pubDate>Fri, 04 Sep 2015 15:32:32 +0000</pubDate>
	     <guid isPermalink="true">http://www.manton.org/2015/09/3007.html</guid>
	     <link>http://www.manton.org/2015/09/3007.html</link>
	     <author>@manton</author>
	   </item>
	   <item>
	     ...
	   </item>
	 </channel>
	</rss>

**Title is optional**

The existing RSS spec says that title is optional. In fact, in the early days of blogging, tools such as Radio Userland and Blogger didn’t even have titles. We got away from that with the popularity of Movable Type and WordPress, even though some modern apps like Tumblr still look at a title as unnecessary for certain post types.

With microblogging, the title will frequently be empty or missing. Do tweets have titles? No, and neither should short microblog posts published through a traditional blog platform. Skipping the title removes some friction in the writing process, making it easier to write a quick post and send it out.

From the RSS spec:

> All elements of an item are optional, however at least one of title or description must be present.

RSS readers must be prepared for a title-less RSS item. If you're building a feed reader, instead of inserting “Untitled” as the placeholder title, think about how your reading UI can accommodate microblog posts gracefully. Blank titles (where the title exists but is an empty string) are equivalent to a completely missing title element.

**HTML post text**

The description XML element in RSS wasn’t originally intended to support HTML. It was often a text summary or opening paragraph of an article, rather than the full text. With microblogging, you always want the full text inside the RSS feed, including any styled text or inline HTML links.

Some feeds will include the plain text version of a post in the description element, and the HTML version in a `content:encoded` element, as specified by [this RSS namespace extension][3]. This should be avoided in favor of a single `description` element with the full HTML, using CDATA syntax to avoid escaping characters:

	<description><![CDATA[
	  <p>Hello world.</p>
	]]></description>

In modern apps, rendering simple HTML is common. If an RSS reader can’t show HTML, it should strip out the HTML tags itself. It’s not up to the feed to provide multiple versions. If both `description` and `content:encoded` are present in a feed while parsing, for compatibility it’s acceptable to prefer whichever includes HTML.

[1]:	http://scripting.com/stories/2012/03/27/rssForMicroblogging.html
[3]:	http://purl.org/rss/1.0/modules/content/
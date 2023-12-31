## Blog archive format

_“Why bake your pages instead of frying? Well, as you might guess, it’s healthier, but at the expense of not tasting quite as good. Baked pages are easy to serve. You can almost always switch servers and software and they’ll still work.” — [Aaron Swartz][1]_

We have a blog at our own domain name. We include Microformats in our web pages. We use software that supports protocols like Micropub and Webmention to make posting easier, and to connect conversations across blogs.

All of these help give our blog resilience, but it’s not enough. We also need a plan for backups and portability, for when we inevitably do need to migrate to a new platform.

[In the 449-page report][2] by the U.S. house judiciary subcommittee on antitrust, they recognized the importance of data portability to balance the dominance of tech companies like Facebook. The section of the report on potential remedies covers the high switching costs for users, suppressing competition unless portability is required:

> Data portability is also a remedy for high costs associated with leaving a dominant platform. These costs present another barrier to entry for competitors and a barrier to exit for consumers. Dominant platforms can maintain market power in part because consumers experience significant frictions when moving to a new product. Users contribute data to a platform, for example, but can find it hard to migrate that data to a rival platform. The difficulty of switching tends to keep users on incumbent platforms. 

Platforms like Twitter, Facebook, and Medium offer data export, but each in a different format. And even more open blogging platforms do not have a standard interchange format.

As I’ve been improving the import and export functionality in Micro.blog, I’ve done a lot of work with WordPress’s WXR format, which is based on RSS. Because it’s just an XML file, it contains only the content on a blog that can be represented as text. Any uploaded photos are not included in WXR.

Instead, what WordPress and Micro.blog do when processing a WXR import is to attempt to download any photos referenced in the file during import. This requires that the files are still online at their original URLs. It’s no help if you need to restore or migrate a blog and all you have is a WXR file.

WXR is also very WordPress-specific, full of redundant WordPress elements that might be difficult for other blogging platforms to replicate exactly.

An alternative solution is to not use a file format at all, but instead use protocols to directly transfer data between platforms. The [Data Transfer Project][3] is backed by Facebook, Google, Apple, and Twitter. [In late 2019][4], Facebook started testing support for transferring photos based on the Data Transfer Project:

> At Facebook, we believe that if you share data with one service, you should be able to move it to another. That’s the principle of data portability, which gives people control and choice while also encouraging innovation. Today, we’re releasing a [tool][5] that will enable Facebook users to transfer their Facebook photos and videos directly to other services, starting with Google Photos.

The Data Transfer Project is quite complex, though. The example code is dozens of Java source files. It may be fine for large platforms, but will be difficult to implement for smaller projects and nearly impossible for most IndieWeb sites.

And for large platforms like Facebook, supporting the Data Transfer Project might give the appearance of openness without having to allow transfer of the more valuable parts of their network. [Ben Thompson wrote on Stratechery][6] about how these platforms still have competitive advantages and are unlikely to make it easier to move away:

> Back in the days of Facebook’s Open Graph initiative — which is at the root of controversy surrounding Cambridge Analytica — Facebook was giving away all of the data developers might want, the better to get developers on the Facebook platform. The company drew the line, though, when it came to other social networks.

Data portability is an important part of Micro.blog and the IndieWeb. If you have an IndieWeb-friendly blog with your own domain name, the assumption is that you can move to another hosting provider at any time.

For Micro.blog, we also experimented with a feature to push an entire site’s Markdown, HTML, and photos to GitHub. This was a complete mirror and good for migrating to another server. It introduced so many extra files, though, it was not reasonable to expect that other blog platforms could support the same level of detail.

I’d be happy to ignore the WordPress-centric nature of WXR and use it as a common blog archive format if WXR provided a mechanism to store photo uploads. Helping people migrate from WordPress to Micro.blog-hosted blogs has only emphasized to me that a better format is needed.

In chatting with the IndieWeb community, the idea was proposed that an HTML file using `h-feed` would provide portability and also an added bonus: it could be opened in any web browser to view your archived site. Photos could be stored as files with relative references in the HTML file. It would include a JSON Feed file, too, so that importers could choose between using a Microformats parser or JSON parser.

The files inside the archive look something like this:

* index.html
* feed.json
* uploads
	* 2017
		* test.jpg

The basics from `h-feed` would follow this structure in the `index.html` file:

* h-feed
	* h-entry
		* p-name
		* e-content
		* dt-published
		* u-url
	* h-entry
		* …

Only `index.html` and `feed.json` are required. Any other paths in the archive would be determined by the contents of the HTML. (I’m using “uploads” in this example, but it could just as easily be “archive”, “audio”, or any other set of folders.)

For large sites, the HTML can be split into multiple files with appropriate `<link>` tags in the header to page through the additional files. While it can contain CSS and your full blog’s design, for Micro.blog the HTML is lightweight: just enough to capture the posts, not a way to transfer templates and themes between blogs.

The whole folder is zipped and renamed with a `.bar` extension. That makes it easy to move around and upload all at once.

---- 

The nice thing about this format is that you can unzip these archives to preview your entire site in any web browser, and it contains all the related photos and other files.

I’ve been working on improving support for Blog Archive in Micro.blog. Version 2.3 of the Mac app can now import .bar files with a nice preview window and progress. It can import into Micro.blog or external Micropub and WordPress blogs.

![][image-1]

When the Mac app uploads photos for your blog from the archive, it rewrites img tags in your HTML to use the new URLs, so it’s a good way to migrate a blog with no or minimal cleanup needed afterwards.

Tools that want to process these files can choose between parsing the Microformats or JSON Feed version of the blog. IndieWeb-friendly tools may find it easier to work with Microformats, and new apps can use any JSON parser.

When generating a .bar file, I recommend having plain HTML in index.html with common Microformats like h-feed, h-entry, u-url, dt-published, and e-content. In the JSON Feed, you can use content\_text for the source Markdown or HTML if you have it, and then HTML in content\_html. Micro.blog will prefer content\_text if it’s there.

For an example to test with, check out this file: example.bar. This contains a few posts and screenshots from our Epilogue blog.

I really hope this format catches on. The files can be big, but they give you a single file that you can backup anywhere.

---- 

This is one of the strengths of the IndieWeb's approach to suggesting multiple building blocks instead of a single monolithic standard. Smaller, focused standards can be reused in different ways, such as using Microformats as the basis for a new archive format.

[1]:	http://www.aaronsw.com/weblog/000404
[2]:	https://judiciary.house.gov/uploadedfiles/investigation_of_competition_in_digital_markets_majority_staff_report_and_recommendations.pdf
[3]:	https://datatransferproject.dev/
[4]:	https://about.fb.com/news/2019/12/data-portability-photo-transfer-tool/
[5]:	https://www.facebook.com/dtp
[6]:	https://stratechery.com/2019/portability-and-interoperability/

[image-1]:	https://book.micro.blog/uploads/2021/3dd2c8d5f3.png
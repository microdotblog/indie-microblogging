## Using HTML

_“HTML documents represent a media-independent description of interactive content. HTML documents might be rendered to a screen, or through a speech synthesizer, or on a braille display. To influence exactly how such rendering takes place, authors can use a styling language such as CSS.” — [HTML5 specification][1]_

The most misunderstood part about Micro.blog is that it's primarily a Twitter replacement. It's not. It's a different view into the web, like a feed reader. The Micro.blog platform is the glue to make that possible. The platform is a byproduct of trying the reach the goal, not the goal itself.

Indie microblog posts are just blog posts. They may have more limitations — no title, shorter text, and usually simpler formatting — but they still use HTML like any blog post.

We should avoid special formats that require new clients to be written. By using HTML for indie microblog posts, blog posts work consistently on the web, in feed readers, and when writing a new post from a blog editor.

By contrast, tweets are effectively stored as plain text. Twitter parses the text and stores extra metadata for it, such as keeping track of where @-mentions and links are.

Pulling a tweet from the Twitter API, you might get a response that looks like this:

	"text": "Hello world!\n\nHere's a link: https://micro.blog/",
	"entities": {
	  "urls": [
	    {
	      "url": "https://t.co/KrFEuTQtGo",
	      "expanded_url": "https://micro.blog/",
	      "indices": [ 28, 47 ]
	    }
	  ]
	}

When showing the tweet on the web, Twitter converts new lines and URLs to HTML. Native apps are likewise responsible for taking the plain text and rendering it with clickable links.

The same post on an indie microblog will use HTML:

	<p>Hello world!</p>
	<p>Here's <a href="https://micro.blog/">a link</a>.</p>

Whether you're seeing the post on the web, reading it in a feed reader, or getting it from Micro.blog's JSON API, it will always look the same. Indie microblog posts are just parts of a web page. They can be adapted for different client app UIs by styling with CSS.

Photos on indie microblogs are `img` tags. Keeping it this simple means it will be compatible with any existing blog software.

When posting a photo with Micro.blog, the text is included first, followed by one or more photos:

![][image-1]

Here's what the HTML for that post looks like

	<p>New stickers.</p>
	<p><img src="https://manton.org/uploads/2018/97e0da903d.jpg" width="600" height="600"></p>

Micro.blog scales down photos to about 1800x1800, and uses 600x600 in the HTML. This 3-1 ratio looks great on the iPhone's 3x retina screens, and is a good width for most of the default themes.

It might be tempting to just paste in domain names or URLs and expect they will be correctly linked by a client. And in some cases they might be. But you should always produce HTML with proper links, so that it works in a wide variety of RSS readers.

Micro.blog pre-processes some text. If you paste in a URL, Micro.blog will automatically create a Markdown link for it, using the domain name as the link title. When you edit the post again, you'll see the Markdown link.

If you enter this text for your post:

	Here's a link: https://micro.blog/

After it saves to Micro.blog, it will become:

	Here's a link: [micro.blog](https://micro.blog/)

From there, it can be converted to HTML with a standard Markdown processor. This happens automatically when publishing your post to a Micro.blog-hosted blog. And if you ever migrate your blog to another platform, all the Markdown will continue to work, because it didn't include anything special just for Micro.blog.

This gets back to a core principle: we are not inventing a new format or protocol. We are building on existing web standards. Indie microblogs should gracefully fall back to work in web browsers and feed readers.

### Allowed HTML tags

Some microblog clients will use a web view to display blog posts, and some clients will write their own renderer for HTML in a post. HTML tags should be restricted to a common set that will be well-supported everywhere. The most basic styling includes tags such as `b`, `strong`, `i`, etc. CSS and class names won’t be used because they are usually based off of a site’s full design which won’t be available from a post in a feed.

Micro.blog’s full list of supported tags include:

* `a`, `span`, `b`, `i`, `img`, `strong`, `em`, `div`, `p`, `br`, `blockquote`, `ul`, `ol`, `li`, `code`, `pre`, `audio`, `video`, `source`

And these attributes are allowed on certain elements:

* **a**: `href`, `title`, `class`
* **span**: `style`, `class`
* **img**: `src`, `style`, `class`, `width`, `height`, `alt`, `loading`
* **audio**: `src`, `controls`
* **video**: `src`, `controls`, `width`, `height`, `preload`, `poster`, `alt`, `playsinline`, `style`, `class`
* **source**: src, type

For `style`, only these CSS property names are allowed:

* `width`, `height`, `max-width`, `max-height`, `min-width`, `min-height`, `border`

Any HTML tags or attributes not in this list will be stripped out. This also includes removing JavaScript. While you can use JavaScript as much as you want on your indie microblog, Micro.blog will prevent it from running in the timeline so that it can't interfere with other posts or users browsing the timeline.

There is one thing to watch out for when using HTML for links instead of always showing the URL: it is possible for a nefarious user to trick someone into clicking on a link. Platforms that use HTML may choose to always show the domain name next to the link, to give the user more information about where the link goes.

### Markdown

Not everyone should have to learn HTML or even know what it is. [Markdown][2] is an alternative markup format that is easy to learn and popular enough that it has become a de-facto default for many text editors. But Markdown was created with HTML in mind, so by using Markdown we get consistent HTML output instead of custom markup for an individual platform.

While most of Markdown's syntax is allowed on Micro.blog in posts and replies, you should limit markup to simple formatting and links so that it reads well in microblog posts.

**Emphasis:** To emphasize some words or phrases, surround the text with single underscores. This will produce italic text when shown on your microblog and in the timeline:

	Here is some _italic_ text.

For stronger emphasis, surround the text with two asterisks. This will produce bold text:

	Here is some **bold** text.

**Links:** You can link to another URL by using the following syntax, with the title of the link first, followed by the URL:

	Go check out [this web site](http://micro.blog/).

**Blockquote:** To quote from another blog post, include a paragraph (separated by blank lines) that starts with the `>` character:

	> This is a quote from someone else.

**Headers:** While headers shouldn't be used in short microblog posts, they can be useful for longer posts and custom pages. Start a new line with one or more "#" characters to turn the line into a header:

	## Section 2

### Inline photos

Photos in Markdown are where more attention is needed. Because Markdown syntax for referencing an image does not support width and height attributes, it is best to use the `img` HTML tag directly.

When cross-posting from your blog to other services, Micro.blog checks the width and height to determine if it's a photo that should be included in the cross-posting. Some platforms use small images for emoji or tracking pixels. We don't want to include those when sending the post to other services. If there is no width and height attributes, Micro.blog will try to quickly download the image to check its size.

When writing longer blog posts with multiple photos in apps like Sunlit, the app is responsible for first uploading all the photos, then creating the full HTML for the post with references to the uploaded photos.

### Quotes

Since the first official standard for HTML — HTML 2.0 in 1995 — we have had the `blockquote` tag. This is used to wrap around a quote from someone you are linking to. If your microblog post format supports basic HTML tags, you can use `blockquote` rather than inventing a new format for retweet-style posts.

It then becomes a UI problem of how best to create and display quotes, not a format or protocol problem. Every platform can have its own approach to creating quotes. Micro.blog has a mostly hands-off approach, letting you use Markdown to create quotes like this:

	Great line from a book I'm reading:
	
	> Cups were filled and refilled, making you drunk with the illusion of changing the world.

Micro.blog uses block quotes for its “Embed” link on posts in the timeline. This copies some HTML to your system clipboard for pasting into a new post, using [Quotebacks][3] to style the post so that it looks nice.

Platforms that invent their own format for retweet-style quotes may have other incentives. By formalizing a quote as its own distinct type of post, they can measure the reach of a quote. On Twitter, quotes are treated very similarly to retweets. On Mastodon, after initial reluctance to have a quotes feature, there has been pressure from the influx of Twitter users to Mastodon to also adopt quotes.

---- 

Using HTML helps decouple content from platforms. Twitter, Instagram, and Snapchat would love everyone to post content in those platforms’ format, because then native ads which are the same size as your own content can be inserted into the platform’s dynamic feed. Posting content as HTML to your own site lets the content be readable in a variety of services based on the open web, from pages at your own domain name, to feed readers or newsletters.

[1]:	https://html.spec.whatwg.org/multipage/
[2]:	https://daringfireball.net/projects/markdown/
[3]:	https://quotebacks.net

[image-1]:	https://book.micro.blog/uploads/2020/c6af49b770.png
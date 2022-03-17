## Building blocks

_“This particular disposition of the secondary projections relative to the primary projections which is the essential feature of the invention provides for a vast number of possible combinations of adjacent bricks.” — LEGO patent_

Microformats are included directly in your blog’s HTML. Other IndieWeb services will be external — not embedded in your web pages, only linked from them.

Most of what we think of as the core IndieWeb building blocks have their own specification, and multiple pages on the IndieWeb wiki. There's one standard that's so simple it doesn't need its own spec: the `link` tag. It's less a building block and more like glue, connecting different IndieWeb services to your blog.

Need to tell feed readers where your RSS or JSON feeds are? That's a `link` tag on your home page, invisible for readers but quietly forming a relationship between documents — that the referenced JSON Feed is an “alternate” of the current web page:

	<link rel="alternate" type="application/json" src="/feed.json">

We’ll outline several standards that all work together this way, linking your home page to API implementations using the `link` tag. The `link` tag connects those APIs to your blog, whether it's a static site that needs external, dynamic applications for some interactions, like receiving comments via Webmention, or whether most of the functionality is hosted together in a single system like WordPress.

Linking building blocks makes your blog more modular. Individual components can be upgraded or replaced without starting over. From the [IndieWeb wiki][1]:

> From a systems perspective, designing a modular system is harder than designing a monolithic system; however over time a modular system has a much better chance of evolving and adapting to changing needs and a diversity of uses.

We can pick and choose what our blog needs, keeping the system lightweight and easier to maintain. If you want to receive comments on your blog, there are multiple Webmention libraries or platforms you can consider plugging in, or you can leave that functionality out altogether.

---- 

The more technical chapters in this book show examples of API web requests and responses. Web requests between a client and a server use HTTP, the hypertext transfer protocol. Web browsers like Safari and Firefox use HTTP, and API clients like Micro.blog also use HTTP.

There are 2 common HTTP methods:

* `GET`: downloading a web page, or requesting some JSON.
* `POST`: sending new data to a server.

In the code examples in this book, we'll include `GET` and `POST` as well as any additional required HTTP headers, each on their own line. To request an authorized resource and ask for a response in JSON, a request might look like this:

	GET /example/path
	Authorization: Bearer 12345
	Accept: application/json

The “Bearer” value is a token that represents the signed in user. The “Accept” type is the format that we'd like the response returned in.

To send data to a sever, we use a POST. Sometimes that is URL-encoded form data, like this:

	POST /example/path
	Authorization: Bearer 12345
	Content-Type: application/x-www-form-urlencoded
	
	content=Hello%20world.

And sometimes that is full JSON in the request, like this:

	POST /example/path
	Authorization: Bearer 12345
	Content-Type: application/json
	
	{
	  "content": "Hello world."
	}

The “Content-Type” header is to tell the server what format we are sending data in for POST requests.

[1]:	https://indieweb.org/Category:building-blocks
## Domain names

_“Postel walked in because he had a job for Mockapetris. He wanted him to find a compromise between five different proposals for improving the way the APRAnet dealt with names and addresses. Mockapetris took the job, but he pretty much ignored the five proposals and built his own system.” — Cade Metz writing about [how Paul Mockapetris created DNS][1]_

For me and for most blogs, it all started with a domain name. [Dan Gilmore wrote for the Guardian][2] in 2013 about encouraging his students to register a domain name to control their content, because a domain name is your identity, the one thing that doesn't change as social networks come and go:

> To the extent that they live public lives in any way – and like it or not, it's getting harder not to be public in some way – tomorrow's adults will need an online home that _they_ control. They need an online home, a place where they tell the world who they are and what they've done, where they post their own work, or at least some of it.

A personal domain name is the most fundamental requirement of indie microblogging. You can start with `username.wordpress.com` or `username.micro.blog`, but at some point to be truly independent, a personal domain name must be mapped to your web site.

Consider street addresses. Addresses on the web (URLs) are just like street addresses, right? You enter a web address in your browser to visit someone's web site, just as you would look up a street address to map directions to a physical location.

If you ever need to move to a new neighborhood, you can forward mail to another street address. This is a feature the postal service provides. But if your content is on someone else's web site — on someone else's domain name, whether that's `medium.com` or a new social network — then there is no mechanism on the internet to forward readers to a new site. Here the analogy to street addresses starts to fall apart, but we already have a layer of the internet that is responsible for fixing this even better than your local post office: DNS.

By using custom domain names as your web address — `yourname.com` instead of `medium.com/yourname` — you don't need to point your readers to a new location and have them resubscribe manually. The "forwarding" is a feature of how domain names work. When your identity on the web is a domain name, you have the flexibility to move content between web hosts and platforms without breaking links to old posts.

Your domain name contains multiple DNS records, each of which maps a hostname like `www.yourname.com` to a server that can serve your posts to your readers. There are generally just 2 records you need to be aware of:

* **A**: short for "address", this is used to map your root domain (`yourname.com` without the "www") to an IP address.
* **CNAME**: this is used to map a subdomain (`www.yourname.com` or `microblog.yourname.com`) to another "canonical" hostname, such as `yourname.micro.blog`.

A common set of DNS records to use Micro.blog servers for hosting would look like this:

| Type  | Hostname | Value               |
| ----- | -------- | ------------------- |
| A     |          | 104.200.22.214      |
| CNAME | www      | username.micro.blog |

Domain names are so important because they exist at a layer above any web hosting platforms. If you're no longer happy with your web host, or they go out of business, it's your domain name that allows you to move to another web host without breaking URLs, so that readers can still find your content. This level of indirection makes your content portable, which makes it your own.

[1]:	https://www.internethalloffame.org//blog/2012/07/23/why-does-net-still-work-christmas-paul-mockapetris
[2]:	https://www.theguardian.com/commentisfree/2013/mar/28/why-everyone-should-register-domain-name
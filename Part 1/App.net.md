## App.net

_“Perhaps you think that Twitter today is a really cool and powerful company. Well, it is. But that doesn’t mean that it couldn’t have been much, much more.” — [Dalton Caldwell][1]_

If the first wave of alternatives to Twitter was as Twitter was still growing, the second wave of alternatives to Twitter came later, as Twitter was using their dominance to restrict the early openness to developers, and struggling to deal with harassment and other community issues on the platform. That period is best represented by App.net.

App.net co-founder [Dalton Caldwell wrote an open letter to Mark Zuckerberg][2] in 2012. Dalton described a meeting he had at Facebook where executives made clear that what Dalton was building was similar to Facebook's App Center product. Facebook had to control it, in Dalton's view, because of ads:

> Mark, I don’t believe that the humans working at Facebook or Twitter want to do the wrong thing. The problem is, employees at Facebook and Twitter are watching your stock price fall, and that is causing them to freak out. Your company, and Twitter, have demonstrably proven that they are willing to screw with users and 3rd-party developer ecosystems, all in the name of ad-revenue. Once you start down the slippery-slope of messing with developers and users, I don’t have any confidence you will stop.

Facebook suggested they could compete with Dalton's product or buy his company. Dalton said he'd rather _reboot his company_ than be acquired. That reboot became App.net.

Even before App.net was fully funded, they released a prototype Twitter clone called "Alpha" as a test for their new API. The API was modern and well-designed. Some features that might be left to third-party developers to extend, like my Tweet Marker API for timeline syncing, were built in as core parts of the API.

App.net further embraced developers through in-person hack days and a developer fund that paid third-party developers based on usage in their apps. This lessoned the risk of jumping into a new platform, making sustainability more of a possibility for new apps like Netbot, a port of the popular Tweetbot to App.net.

---- 

You could add blog feeds to App.net for "automatic" posting to App.net, but fundamentally the service was not structured around integrating with external blogs. There were no domain names for your content.

[Dalton Caldwell wrote about App.net supporting open standards][3], without necessarily basing the API on those standards:

> Activitystrea.ms Atom & JSON feeds, as well as RSS feeds, of public posts for individual users, hashtags, etc. (Note that this is different from making them the foundation of our read/write API, which we have decided not to do)

There were minor differences to Twitter, such as a longer 256-character post length, but also deeper additions, such as annotation data, channels, and file storage. These API features enabled building new types of apps. Location check-in apps like Ohai by Steve Streza, which by using a common API could share data with other location-based apps, and chat apps like Whisper, which was spun off of the Riposte iOS client.

Streza blogged about these benefits [in a post about Ohai 1.0 in 2003][4]:

> This means other developers could build apps that recognize your journal. So, if the developer of your favorite camera app adds support for Ohai journals, they could save those photos into your journal. Then, the next time you open Ohai, those photos are available. Other developers could build journaling apps for other platforms like Android, or even write competitive apps for iPhone.

The API was so flexible that the types of apps grew beyond what we were expecting as a Twitter-like platform.

---- 

I believed at the time that the next great app for App.net would come from the community, the developers who were passionate about the API's potential, just as early developers like [Iconfactory][5] who took a risk on Twitter years ago are still having an impact on that service today. The next great app would come from the developers who see App.net as a way to build new things.

I was working on an app like that. It uses the App.net API, but not the timeline. It takes pictures, but isn’t really a photo app. It integrates with Ohai, but isn’t another location check-in app. It renders beautiful maps throughout, but isn’t about navigation. Some of the features I’m most proud of in the app wouldn’t be the same without App.net.

There’s no way to know what apps will resonate with the mainstream, and which will remain niche or failures. But to have any hope of success, you have to start. You might even have to take a risk on a new platform if you want to build something new.

The promise of App.net was bigger than one type of app. App.net wasn't just a blank slate; it was an amplifier. It was waiting to power the next new idea and help it grow into something big, but it could only wait so long.

---- 

Two years later the experiment was over. Dalton announced that subscription revenue was not enough to continue with a full-time staff, and App.net would be in maintenance-mode only. A few years after that, the service was completely shut down.

[In an article for Wired][6], written a year into the App.net launch when many people still had great hope for the platform, Mat Honan said something was missing from App.net:

> But there’s still something missing, that seems totally obvious: a game. App.net needs a Dots or a Candy Crush or a Words With Friends that plugs into its social sphere. Something that isn’t just useful, but fun. Something wonderful.

Something _was_ missing, but not a game. The App.net team got so much right — the early crowdfunding, the well-designed API, the developer story — that I didn't notice what they had left out until much later. All data lived at `app.net` URLs, and when the platform was gone, all the posts and data went with it. There was no way to own your content.

To learn from App.net, we should be inspired by its rich APIs, and especially it’s developer-friendly ecosystem. But it was too centralized.

[1]:	http://daltoncaldwell.com/what-twitter-could-have-been
[2]:	http://daltoncaldwell.com/dear-mark-zuckerberg
[3]:	http://daltoncaldwell.com/a-response-to-brennan-novak
[4]:	http://stevestreza.com/2013/07/16/ohai/
[5]:	https://iconfactory.com/
[6]:	http://www.wired.com/gadgetlab/2013/08/the-great-app-net-mistake/
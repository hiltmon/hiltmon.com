---
layout: post
title: "Slogger after 6 Months"
date: 2013-04-23 10:43
comments: true
categories: [ Slogger, Tips and Tricks ]
---

I have been using [Brett Terpstra's][brettterpstra] ([@ttscoff][twitter]) [Slogger][brettterpstra 2] for the last six months, and I think it's time to review it. Slogger is a script and a set of plugins that log your online activity each day into [Day One][linksynergy], the best journaling application for OS X, or in Markdown files if you prefer. It's a core part of my [Backing up your Online Life]({{ root_url}}/blog/2013/03/14/backup-your-online-life/) process.

*TL;DR: It's totally worth taking the time to set it up and get it going. The data captured is so useful and often hard to gain access to, especially as we operate across many services, and as these services come and go.*

<!--more-->

**Contents:**

* <a href="#my_day">My Day</a>, a sample day captured by Slogger
* <a href="#installing">Installing Slogger</a>
* <a href="#contributions">My Contributions</a>
* <a href="#why_slogger">Why Slogger</a>

## <a name="my_day"></a>My Day

Let us look at my Friday, April 19th, in [Day One][linksynergy], in order from top to bottom, [click the image for a full-size version]({{ root_url }}/images/slogger-review-1.jpg). It contains:

[{% img right /images/slogger-review-1.jpg 341 393 %}]({{ root_url }}/images/slogger-review-1.jpg)

* The Google Analytics statistics for this web site, almost 700 visitors, and the the same stats for my company site below it.
* Market closing prices
* All my [Tweets][twitter 2]
* All documents that I saved to [Instapaper][instapaper] that day (with links to them)
* My [Foursquare][foursquare] Check-ins
* All my [App.Net][app] posts
* A commit to the `skylark` project for a client
* A blog post, recorded by my blog creation scripts  <span class="light">(not Slogger)</span>

Not shown, since I did not use them that day, are any [Instagram][instagram] pictures I took, music I scrobbled to [Last.fm][last], sites I tagged in [Pinboard][pinboard], or pictures I posted to [Flickr][flickr]. And those are just the services I have set up and enabled. There are many in Slogger that I have not enabled, such as [Facebook][facebook], [OmniFocus][omnigroup] and RSS feeds.

Lets look at some of these entries in more detail. 

[{% img left /images/slogger-review-2.jpg 255 295 %}]({{ root_url }}/images/slogger-review-2.jpg)

If we choose the Google Analytics for hiltmon.com, we get the image on the left, [click for larger version]({{ root_url }}/images/slogger-review-2.jpg). For each day, I can see how many page views and visitors the site got, where those visitors came from, and the top 10 most popular articles on the site.

I like to have these stats to see how my site traffic is growing or shrinking, and to see what my audience likes. I helps me decide whether to create or publish new blog ideas.

[{% img right /images/slogger-review-3.jpg 255 295 %}]({{ root_url }}/images/slogger-review-3.jpg)

If we choose the tweets item, I see all the tweets I made on that day, [click for larger version]({{ root_url }}/images/slogger-review-3.jpg). Seems that I did not get any retweets or favorites on that day.

Slogger saves any links and any referenced images in tweets to [Day One][linksynergy] as well.

You can also see my market price data saved for the day at the bottom.

**In short, Slogger has recorded and backed up all my online social activity and key analytics for me without any effort on my part.**

## <a name="installing"></a>Installation

Installing [Slogger][brettterpstra 2] requires you to get your geek on. It takes a bit of time and effort to jump to each service and get the configuration details, but this is a once-off process.

I recommend installing it on a computer that you know will be on and running around midnight. I have it on my OS X home server.

Brett wrote some very excellent installation instructions [on the product page][brettterpstra 2] under **Configure** which I recommend you follow  <span class="light">(and so I have not duplicated them here)</span>. Don't forget to choose and move plugins from the `plugins_disabled` folder to add more features. Each plugin requires a separate configuration step, but I found them to be reasonably well documented and easy to set up.

**Tips:** Use the `-o` parameter to run only a single plugin at a time while setting up. And use the `-u` parameter to clean up after each test run until the plugin is stable.

I also recommend that you set up the daily `launchd` task so that it will run automatically for you. That way, once Slogger is fully configured, you can just forget about it. Run `install.rb` once to set up the nightly run.

When I originally set up Slogger, and had finished testing each plugin I wanted, I also ran it using the `-t` parameter to back fill history. Some services/plugins got a lot of data back, others were limited. But the result is that I have data going back many months before I started using Slogger.

## <a name="contributions"></a>My Contributions

I liked the product so much that I wrote two of the plugins for it:

* The [Google Analytics Logger for Slogger][hiltmon] which logs daily site statistics.
* The [Yahoo Finance Logger for Slogger][hiltmon 2] to log daily market prices.

Brett made creating your own plugin very easy. You can learn how to do this [on the product page][brettterpstra 2] under **Plugin Development**.

## <a name="why_slogger"></a>Why Slogger

Slogger is the best product I know of that will find, capture and save all my social activity and key daily data for me. It is a fire and forget product which has required no input or effort from me since I originally installed it. I am no longer afraid to lose my tweets or favorite Instagram pictures if these services or products go away. And I can search for and find all this activity easily on my own Mac.

As an alternative, web services like [IFTTT][ifttt]  <span class="light">(which I also use)</span> can perform some of the Slogger functions, like recording App.net posts, Facebook entries and and Foursquare checkins to text files on Dropbox. Unfortunately, they lost access to Twitter data a while back, whereas Slogger still works.

I just love having all my daily activities and key data recorded without effort from me in [Day One][linksynergy] by Slogger. I have over a year's worth of data there already. And since this [Day One][linksynergy] data is also just plain text files behind the scenes, I do not worry about gaining access to this data again in the future.

If you operate across many social network services in your daily Internet wanderings and social interactions, or you could use a log of daily statistics in anything you do, you owe it to yourself to use Slogger to log them automatically. Set it up once, and reap the ongoing benefits as I have. **Highly recommended.**

*Follow the author as [@hiltmon][twitter 2] on Twitter and [@hiltmon][app] on App.Net. Mute `#xpost` on one.*

[app]: http://alpha.app.net/hiltmon
[brettterpstra]: http://brettterpstra.com
[brettterpstra 2]: http://brettterpstra.com/projects/slogger/
[facebook]: https://www.facebook.com/hiltmoncom
[flickr]: http://www.flickr.com
[foursquare]: https://foursquare.com
[hiltmon]: https://hiltmon.com/blog/2012/11/14/google-analytics-logger-for-slogger/
[hiltmon 2]: https://hiltmon.com/blog/2012/12/01/yahoo-finance-logger-for-slogger/
[ifttt]: https://ifttt.com
[instagram]: http://instagram.com/hiltmon
[instapaper]: http://www.instapaper.com
[last]: http://www.last.fm
[linksynergy]: https://itunes.apple.com/us/app/day-one/id422304217?mt=12&uo=4&at=10l894
[omnigroup]: http://www.omnigroup.com/products/omnifocus/
[pinboard]: https://pinboard.in
[twitter]: http://twitter.com/ttscoff
[twitter 2]: http://https://twitter.com/hiltmon
---
layout: post
title: "SonicWall NetExtender for OS X Mavericks"
date: 2013-09-28 12:22
comments: true
categories: 
---

**UPDATE:** 10.9 or above users, use the [Sonicwall Mobile Connect](https://itunes.apple.com/us/app/sonicwall-mobile-connect/id822514576?mt=12&uo=4&at=10l894) app on the Mac App Store (or learn more at [Sonicwall Mobile Connect for OS X Mavericks](https://hiltmon.com/blog/2014/07/07/sonicwall-mobile-connect-for-os-x-mavericks/)).

*TL;DR: Download from [https://sslvpn.demo.sonicwall.com/cgi-bin/welcome](https://sslvpn.demo.sonicwall.com/cgi-bin/welcome). Follow the admin login instructions, then look for NetExtender / Client Downloads.*

**UPDATE:** Saved a copy of the DMG at <a href="https://hiltmon.com/files/NetExtender-7.5.757.dmg">https://hiltmon.com/files/NetExtender-7.5.757.dmg</a> as the normal login seems to be disabled. (WARNING: Link will eventually get stale).

**UPDATE 2:** Your company can also register and get the latest versions from [MySonicwall.com](https://www.mysonicwall.com).

Many of us corporate drones need SonicWall's NetExtender for remote access to our company networks. And the way we get it is to go to the company IP address IT gives us and download it. <span class="light">And then install the Java plugin. And then install the java runtime.</span>

Unfortunately, the version provided by most of these sites is out-of-date as most SonicWall VPN devices never get updated.

In my case, the version of NetExtender for Mac, 6.0.719, on my company SonicWall works on 10.8 Mountain Lion, but fails on OS X 10.9 Mavericks.

One solution is to upgrade all the company SonicWalls. *I may as well pack my snowboard for a lovely eternity riding the frozen volcanoes in hell.* <span class="light">Yes, and I am the CTO! Still not going to do it.</span>

The solution that *works* is to somehow install the *latest* copy of the NetExtender application without upgrading the SonicWall and I finally found a place that actually allows you to download it.

Their demo site.

{% img right /images/sonicwall-dropdown.jpg 300 235 %}

Just go to [https://sslvpn.demo.sonicwall.com/cgi-bin/welcome](https://sslvpn.demo.sonicwall.com/cgi-bin/welcome) and log in using the provided demo password. Then click the big NetExtender button to install the latest client version, just like you did on your IT provided site. I got 7.0.752. Which works on OS X Mavericks.

Be aware though that once that is installed and running, you will find yourself connected to the *demo site*, not your company network. Simply disconnect, hit the dropdown arrow to choose your old NetExtender settings and connect happily/slavishly to your company network.

Back to work.

*Follow the author as [@hiltmon](https://twitter.com/hiltmon) on Twitter and [@hiltmon](http://alpha.app.net/hiltmon) on App.Net. Mute `#xpost` on one.*
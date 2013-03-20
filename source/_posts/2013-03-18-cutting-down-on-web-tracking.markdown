---
layout: post
title: "Cutting down on Web Tracking"
date: 2013-03-18 10:46
comments: true
categories: 
---

You may not know it, but lots of web sites use a variety of tricks to track you across the Internet, not just on the site you are currently browsing. These all depend on your browser talking to the tracker's server without your knowledge or consent. These trackers use huge numbers of servers with different names and IP addresses to make it more difficult to stop them.

If you use a single browser *all* the time, plugins like [Ghostery](http://www.ghostery.com) work very well. But if you, like me, use lots of browsers and scripts, something else is needed.

Dan Pollock has a solution at [Using a Hosts File To Make The Internet Not Suck (as much)](http://someonewhocares.org/hosts/). He provides a massive and frequently updated `hosts` file that redirects all requests for these sites back to your own computer. Since your browser and scripts never send the request to the tracker, you don't get tracked. And since these requests are local, browsing should be quicker.

To install  <span class="light">(OS X instructions, others in the file)</span>, browse to the [text version](http://someonewhocares.org/hosts/hosts) and *append* it to your `/etc/hosts` file using your favorite text editor. Then come back every once in a while and replace with updates.

*Update:* Before saving the updated file, perform a search for `apple` and comment out any lines with `appleglobal` and `applestoreus` in them, they break Apple.com. If you find other sites breaking, just look for them in `/etc/hosts`, comment them out and email Dan at [hosts@someonewhocares.org](mailto:hosts@someonewhocares.org).

I can't *prove* that this works for *all* sites, and it does not feel as if browsing is much faster (because I am running a local web server<a href="#fn:1" id="fnref:1"><sup>[1]</sup></a>), but it does seem to work against the most common tracking sites. So much so that I have disabled [Ghostery](http://www.ghostery.com) and rely on this to cut down on being tracked.

*Follow the author as [@hiltmon](http://twitter.com/hiltmon) on Twitter and [@hiltmon](http://alpha.app.net/hiltmon) on App.Net. Mute `#xpost` on one.*

---
<div class="footnotes">
    <ol>
        <li id="fn:1">Beware if you, like me, are running a local web server on port 80 or <a href="http://pow.cx">POW</a>, your computer will start accepting these web hits and start sending 404 errors (which you will start to see in a surprising number of sites). You <em>may</em> need to keep your logs clean if your primary drive is small.<a href="#fnref:1" title="Back to Post"><sup>&#160;&#8617;</sup></a></li>
    </ol>
</div>
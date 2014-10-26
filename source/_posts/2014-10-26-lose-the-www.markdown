---
layout: post
title: "Lose the WWW"
date: 2014-10-26 17:22:46 -0400
comments: true
categories: 
---

I have finally removed the `www` from `hiltmon.com`. The 1990's have passed and `www` no longer makes sense in URL's. *Maybe it's time you did the same to your site too.*

What triggered this change was that, as of 14 October 2014, Google Analytics started throwing an error if you had links to `www.yoursite.com` and `yoursite.com`. This is because it treated links with `www` and without as different.

Removing the `www` was easy. I used Global Search and Replace (**⇧⌘F** in [TextMate 2](http://blog.macromates.com)) to find `//www.hiltmon` and replace it with `//hiltmon`. Then regenerated the site.

But we are still faced with the problem that remote links to the site may still include the `www` in their URL's. The solution is a 301 redirect. Setting that up depends on your hosting provider. For [Dreamhost](http://www.dreamhost.com/r.cgi?25899)[^1], it required clicking one radio button:

{% img /images/lose-the-www.png 819 145 %}

Welcome to [hiltmon.com](http://hiltmon.com).

*Follow the author as [@hiltmon](http://twitter.com/hiltmon) on Twitter.*

[^1]:	Warning: Affiliate link.
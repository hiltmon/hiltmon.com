---
layout: post
title: "Get to read quicker"
date: 2012-03-14 19:43
comments: true
categories: 
---

People come to [hiltmon.com](http://www.hiltmon.com) to read, and occasionally to comment on the writing found here. Statistics show that no-one uses the social icons to tweet, Facebook or Google+ the articles.

The average page loads in 2.53 seconds and makes 84 requests. Thats a long time for readers to wait, and a lot of requests. So I decided to check out what is going on.

The basic page requires 29 requests and takes ~800ms to load (when the cache is clear). That's pretty good when you consider Google Analytics and recent tweets come in. So where is the rest of the time going?

It turns out that [Disqus](http://disqus.com), the commenting system I use, adds 32 requests and ~800ms to the load time.  But I want to keep comments, I've been getting some great ones. So that stays.

My recent tweets is only 2 requests and ~50ms, so it stays too.

The remaining 23 requests and 1.05 seconds came from the tweet button, Google+ button and Facebook like button. *Which no-one ever used!* So, as of today, they're gone from the site. I am sure you all know how to tweet, Facebook and Google+ an article, because you have been doing it all along without the buttons anyway.

So now, the average page loads with 61 requests and 1.48 seconds. That's over a second quicker to get my readers to reading the article. Much better. Now if only Disqus would be faster.

Hat tip to James Hague's article [Solving the Wrong Problem](http://prog21.dadgum.com/130.html) that made me look into this.

---
layout: post
title: "Upgrading Octopress to Jekyll 2.0"
date: 2014-06-21 16:28:04 -0400
comments: true
categories: 
---

So this happened today:

<blockquote class="twitter-tweet" lang="en"><p>Octopress 2 is now using the latest and greatest Jekyll 2.0.3.&#10;&#10;Now, back to work on Octopress 3. Happy blogging!</p>&mdash; Octopress (@octopress) <a href="https://twitter.com/octopress/statuses/480424836175757312">June 21, 2014</a></blockquote>
<script async src="//platform.twitter.com/widgets.js" charset="utf-8"></script>

I've been waiting for this. Now that it has, I decided to finally upgrade this site.

It was easy. As per [Updating Octopress](http://octopress.org/docs/updating/), I just ran:

	git pull octopress master

Then, to ensure all gems were up to date, I ran

	bundle update

Finally, I got ready

	rake clean
	rake generate
	
**And it failed.**

One thing went wrong and it was because of a old change in [Jekyll](http://jekyllrb.com). You see, before the upgrade I was using the positively ancient [Jekyll](http://jekyllrb.com) 0.12. Since 1.11, [Jekyll](http://jekyllrb.com) has added `excerpts`, where it takes the first markdown paragraph in a post and generates that as the excerpt, which it then runs through [Liquid](http://liquidmarkup.org). However, I often start a post with the [blockquote](http://octopress.org/docs/plugins/blockquote/) tag and many of these quotes have multiple paragraphs. The result:

```
Hiltmon@Dauntless:HiltmonDotCom (master *) $ rake generate
## Generating Site with Jekyll
identical source/stylesheets/screen.css
Configuration file: /Users/Hiltmon/Projects/Spikes/HiltmonDotCom/_config.yml
            Source: source
       Destination: public
      Generating...
  Liquid Exception: blockquote tag was never closed in _posts/2012-01-26-where-the-light-is-better.markdown/#excerpt
```

**The post had the closing tag, but the excerpt did not.**

To correct this problem, I added the following line in my `_config.yml` to disable excerpts:

	excerpt_separator: "" # Workaround for http://blog.slaks.net/2013-08-09/jekyll-tag-was-never-closed
	
*Huge thanks to Schabse Laks at http://slaks.net for figuring this out.*

The site now generates just fine.

<span class="light">Once again, my utmost respect and thanks to [Brandon Mathis](http://brandonmathis.com) for creating and maintaining this lovely [Octopress](http://octopress.org) blog wrapper on top of the excellent work by [Tom Preston Werner](http://tom.preston-werner.com) and the team who create and maintain [Jekyll](http://jekyllrb.com).</span>

*Follow the author as [@hiltmon](http://twitter.com/hiltmon) on Twitter and [@hiltmon](http://alpha.app.net/hiltmon) on App.Net. Mute `#xpost` on one.*

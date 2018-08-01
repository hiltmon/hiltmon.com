---
layout: post
title: "Browser Windows on all Desktops"
date: 2013-01-19 14:05
comments: true
categories: 
- Productivity
---

In [Being Productive With Virtual Desktops](https://hiltmon.com/blog/2013/01/17/being-productive-with-virtual-desktops/), I talked about how I pin certain applications to certain Mission Control virtual desktops to create context specific environments.

*Reader “zharmany” asked what I did with the web browser, since it is needed on many of these desktops for different reasons.*

My needs are to have separate browser windows on *Desktop 1 / Work* for previews, on *Desktop 3 / Mail* for mail links and on *Desktop 4 / Social* for looking at tweeted links, so I do not pin Safari. Instead, I open new, blank Safari windows on each of these desktops.

What I *used to do* is I use the **New Window** menu item off the Safari dock icon to launch a blank Safari window in the current space.

{% img /images/safari-new-window.jpg 495 303 %}

OS X (or maybe Safari) is smart enough that if there is an open Safari window on the current desktop, then it opens all clicked links in that window as new tabs. It does not jump desktops. Note that I have “Open paths in tabs instead of windows:” set to **Automatically** in Safari **Preferences** / **Tabs**.

What I use now is a [Keyboard Maestro](http://www.keyboardmaestro.com/main/) macro triggered by `⌃⌥⌘B` that creates a new Safari window on the current desktop.  I habitually hit `⌃⌥⌘B` when I move to a desktop that I wish to browse on. The macro looks like this:

{% img /images/new-safari-window.jpg 487 396 %}

You can setup the same script in [Alfred](https://itunes.apple.com/us/app/alfred/id405843582?mt=12&uo=4&at=10l894) or other launcher, the code is simply:

```
tell application "Safari"
	make new document
	tell application "Safari" to activate
end tell
```

I usually just leave blank Safari windows open on each Desktop, and as I work and context switch, so the tabs on each desktop fill up with that Desktop’s links. 

The main benefit is that a context switch back to work means that the browser on *Desktop 1 / Work* is not cluttered with mail or social tabs, and remains displaying the last page browsed for work.

*Follow the author as [@hiltmon](https://twitter.com/hiltmon) on Twitter or [@hiltmon](http://alpha.app.net/hiltmon) on App.Net.*
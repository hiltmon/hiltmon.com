---
layout: post
title: "Being Productive with Virtual Desktops"
date: 2013-01-17 10:16
comments: true
categories: Productivity
---

There are a bunch of applications I always want running on my computer, such as [Mail.app](http://www.apple.com/osx/apps/#mail), [OmniFocus](https://itunes.apple.com/us/app/omnifocus/id402835630?mt=12&uo=4&at=10l894), [Billings Pro](https://itunes.apple.com/us/app/billings-pro/id434514810?mt=12&uo=4&at=10l894) and [Tweetbot](https://itunes.apple.com/us/app/tweetbot-for-twitter/id557168941?mt=12&uo=4&at=10l894), but I also do not want to be distracted by them. One option is to hide them using `⌘H` on the Mac, the other way is to use virtual desktops. 

My goal is to create context-aware desktops where I can stay focussed on the task at hand without distractions, and to be able to switch and restore contexts instantly and predictably, that is most productive.

{% img /images/desktops-all.jpg 750 110 %}

After much experimentation, I have settled on a five virtual desktop setup in Mission Control, where each serves a specific purpose:

* **Desktop 1: My current workspace**, for whatever I am currently doing. All my current working windows are opened here. For example, when programming Kifu, I have [BBEdit](https://itunes.apple.com/us/app/bbedit/id404009241?mt=12&uo=4&at=10l894) open for notes, [VoodooPad](https://itunes.apple.com/us/app/voodoopad-5/id514489722?mt=12&uo=4&at=10l894) open for project information, [TextMate 2](https://github.com/textmate/textmate) open for coding, several terminal sessions and several browser tabs open on this desktop. For blogging, as now, I have [Byword](https://itunes.apple.com/us/app/byword/id420212497?mt=12&uo=4&at=10l894) open for writing, a terminal for managing [Octopress](http://octopress.org) and a browser window open for preview.
* **Desktop 2: Supporting the current workspace**, software and files that are open that *support* the current task but are not part of it. For example, here I run [Acorn](https://itunes.apple.com/us/app/acorn-4-image-editor-for-humans/id634108295?mt=12&uo=4&at=10l894) or [Photoshop](http://www.adobe.com/products/photoshop.html) for images when developing or blogging.
* **Desktop 3: Mail**. I run OS X’s [Mail.app](http://www.apple.com/osx/apps/#mail) here, not in full screen mode so I can have multiple messages open at once.
* **Desktop 4: News and social applications**, like [Reeder](http://reederapp.com/mac/) for RSS, [Tweetbot](https://itunes.apple.com/us/app/tweetbot-for-twitter/id557168941?mt=12&uo=4&at=10l894) for Twitter and [Wedge](http://wedge.natestedman.com) for App.Net.
* **Desktop 5: Out of the way applications**, like [OmniFocus](https://itunes.apple.com/us/app/omnifocus/id402835630?mt=12&uo=4&at=10l894) and [Billings Pro](https://itunes.apple.com/us/app/billings-pro/id434514810?mt=12&uo=4&at=10l894). I want these to be always running, a keystroke away, and available to view at a glance, just not *in the way*.

To enhance productivity, I also set up two things: keyboard shortcuts and pinning.

### 1. Desktop Keyboard Shortcuts

I can get to any desktop with a single keystroke. `⌃1` to the current workspace, `⌃2` to the alternate, `⌃3` for mail, etc. So, when I have a break working and want to check my mail, I just press `⌃3` and the mail desktop slides in. It is a lot faster than using `⌥⇥` (Option/Alt - Tab) a bunch of times to select mail.app and then wait for the windows to come forward. The best thing is, to get back to work after checking email, `⌃1`, the first desktop appears, just as I left it.

{% img /images/desktops-transitions.jpg 750 125 %}

To enable this on your Mac, first create each virtual desktop. You do this by launching Mission Control by pressing the `F3` key or using four fingers to swipe up. Then move your mouse cursor to the top-right of your screen and click to create new virtual desktops.

I strong recommend opening **System Preferences**, choosing **Mission Control** and unchecking “Automatically rearrange spaces based on most recent use” because it causes the desktops to shuffle around annoyingly. See image below right.

You also need to enable the keyboard shortcuts to give you the ability to  jump to a virtual desktop in a single keystroke. Open **System Preferences**, choose **Keyboard** then **Keyboard Shortcuts** tab and click on **Mission Control**. If you scroll down to the right, you should see shortcuts to switch to each created desktop. Make sure they correspond to `Control-N` where N is the desktop number and they are checked. See image below left.

{% img /images/desktops-preferences.jpg 750 336 %}

### 2. Application Pinning

For the applications that I want to *always* run on specific desktops, like Mail on Desktop 3, I pin that application to the preferred desktop. The next time that the application launches, it will launch on the pinned desktop and not the current one.

To pin an application to a virtual desktop, make sure the application is not running. Switch to the preferred desktop using the shortcut key, then launch the application. Once the application is running, right-click on it’s icon in the dock, and choose **Options / Assign To / This Desktop**. Next time this application is launched, it will open its windows on this desktop. Which means all you need to remember is *which desktop* to switch to for that application.

{% img /images/desktops-pin-application.jpg 434 354 %}

I do not recommend pinning all applications, for example Finder or Browser windows can and should appear on all desktops. Ideally, Apple will change it so that un-pinned applications will create new windows on desktops where they have none if activated.

### The good and the bad

The good of this setup is:

* I can switch contexts quickly with a single keystroke, to go from work to email, or work to social by just switching desktops.
* When working in a specific desktop, I am not distracted by non-contextual applications. For example, when processing mail, I do not get distracted by twitter.
* I can switch back to work without losing my place. `⌃1` back to my work and all windows and applications and cursor positions are exactly as I left them.

The only real bad of this setup depends on your choice in “When switching to an application, switch to a space with open windows for that application” setting in Mission Control preferences. If it is checked then the screen occasionally jumps to another desktop when you quit an application, and OS X jumps you to the frontmost window of the next application on the stack. On the other hand, if it is not checked, then `⌥⇥` becomes quite painful as you switch to an application and nothing appears. Pick your poison, I have it checked and deal with the annoying switches.

*I know I have written about this before, but have changed the setup and felt it was better to create a new article than update the old. This truly is one of the best productivity tips, especially since it helps maintain context when switching back to work mode.*

See Also: [Browser Windows on All Desktops](https://hiltmon.com/blog/2013/01/19/browser-windows-on-all-desktops/).

*Follow the author as [@hiltmon](http://https://twitter.com/hiltmon) on Twitter or [@hiltmon](http://alpha.app.net/hiltmon) on App.Net.*

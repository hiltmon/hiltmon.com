---
layout: post
title: "Using Mission Control Desktops"
date: 2012-06-03 10:01
comments: true
categories: [Productivity]
---

In order to reduce distractions while I am working, yet still have the benefit of having these applications running, I use multiple [Mission Control](http://www.apple.com/macosx/whats-new/mission-control.html) desktops on my Macintosh computers. In short, I work, with focus, on Desktop 1; respond to email on Desktop 2; IM and Tweet from Desktop 3; and manage my time and activity on Desktop 4.

{% img /images/all-desktops.png 640 83 %}

Here's why and how it works.

## Each desktop has a purpose

Desktop 1 is my *work* desktop. I only want the applications I need to perform the current task running on this desktop. So I use my [Application Context Pack](https://hiltmon.com/blog/2012/04/26/application-context-packs/) macros to launch and terminate the application packs I need for the task that I am performing.

For example, right now, since I am writing a blog article, Desktop 1 is running:

* [Byword](http://bywordapp.com/) - to write in
* [MindNode Pro](http://mindnode.com/) - what I used to structure the article
* [Terminal](http://www.apple.com/macosx/apps/all.html#terminal) - to manage Octopress
* [Safari](http://www.apple.com/safari/) - to preview the site
* [Pixelmator](http://www.pixelmator.com/) - to crop and export any article images

A little later today, I'm going to be doing some [Ruby on Rails](https://rubyonrails.org/) programming, so I'll switch to the *Rails Context* pack, closing everything on Desktop 1 and opening [TextMate](http://macromates.com/), [BBEdit](http://www.barebones.com/products/bbedit/index.html) and a Terminal for that *on this desktop*.

The most common activity I perform when *not* directly working is checking on and responding to email. So that goes on Desktop 2. On the laptop, Desktop 2 is just full-screen email. To check email, I use either `⌃→` or `⌘2` and viola, my work goes away and my email comes into view as Desktop 2 slides in. Check, read, respond, then `⌃←` or `⌘1` and Desktop 1, my work, slides back in ready to continue.

Desktop 3 is for stuff I want open, but do not want to look at very often. I used to have these application on a second monitor, but found I would interrupt work all the time to monitor these. So I moved them to another desktop, and switched to a single monitor workflow. This is where I usually leave [Reeder](http://reederapp.com/) for RSS news, [Messages](http://www.apple.com/macosx/mountain-lion/messages-beta/) for IM and [Twitterrific](http://iconfactory.com/software/twitterrific) for twitter, just hanging out collecting stuff until I have the time, or take a break, and look at it. If an IM comes in, or I have an inspired tweet, I can switch easily by pressing `⌃→` twice or `⌘3` once. Check, respond, read, and return to work via `⌘1`.

Desktop 4 is my time and activity management desktop. It always has [OmniFocus](http://www.omnigroup.com/products/omnifocus/) and [Billings](http://www.marketcircle.com/billings/) running. I like having OmniFocus running so I can use the `⌃⌥Space` combo to capture a new task, yet keep it hidden so I do not have to stare at the due list. And I use Billings to capture my time for consulting work, it's got to be running somewhere. I often leave [nvAlt](http://brettterpstra.com/project/nvalt/) running on this desktop too, so I can switch to it when a call comes in and take notes.

Finally, I use the Dashboard as a quick glance screen. There, I run clocks and weather for New York, Tokyo and Sydney (the family locations), Stocks so I can see how badly or well AAPL shares are doing and instances of [GAget](http://www.zoltanhosszu.com/gaget/) to monitor activity on my web sites.

## How to set it up

The first thing you want to do it create all the desktops. Launch **Mission Control** by either clicking the icon or pressing `F3`. Then click the add button at the top-right to create the desktops.

*Tip 1*: I like to set a different desktop picture for each desktop so I can, at a glance, know which one I am on. To set the picture for a desktop, *switch to that desktop first*, then open **System Preferences**, choose **Desktop & Screensaver** and choose the picture. *Close* **System Preferences**, switch to the next and repeat.

*Tip 2*: I also like to use keyboard shortcuts to switch between desktops. To do so, *after you have created the desktops*, launch **System Preferences**, the choose **Keyboard**, then **Keyboard Shortcuts**. Click on **Mission Control** and enable the shortcuts for each desktop.

{% img /images/keyboard-shortcuts-mc.png 640 574 %}

The next thing you want to do is set it up that each application launches only on the desktop you want. This is a little more tricky:

* Make sure the application is *not* running
* Switch to the desktop you want it to launch on
* Launch the application and wait for it to start up
* Right-click on the running application icon to bring up the context menu
* Choose **Options**, then click **This Desktop**

{% img /images/assign-to-desktop.png 340 261 %}

From now on, whenever you launch this application, OS X will switch you to this desktop and launch the application. Now switch to the next desktop, and do the same. Only do this for applications that you want pinned to specific desktops.

Even better, if you use Lion's auto-resume feature, when you reboot, these applications will relaunch on the right desktop.

## The workflow

My workflow is pretty straight forward now. On boot, I launch all my regular applications using a single [Keyboard Maestro](http://www.keyboardmaestro.com/main/) macro (I do not use auto-resume). All these applications open on their respective desktops, and I am left facing a blank Desktop 1.  I usually check email on Desktop 2, then choose the Application Context Pack I want and start working on Desktop 1.

During the day, I switch context packs as I switch tasks, switch to Desktop 2 occasionally to check email and to Desktop 3 or 4 as needed.

This way, I gain the benefit of a distraction-free work environment with fast access to necessary applications.

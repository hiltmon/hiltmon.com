---
layout: post
title: "Syncing the Desktop and the Laptop"
date: 2012-06-29 16:05
comments: true
categories: 
---

For the past few years, I have been working about 5&frac12; days a week on the desktop and 1&frac12; days a week on the laptop. The desktop is a monster 8-core Mac Pro with loads of RAM and my good old [23" Cinema HD Display](http://hiltmon.com/blog/2012/05/16/apple-cinema-hd-display-circa-2003/), which makes it perfect for compiling, graphics work and the usual day-to-day work stuff. The laptop is a mid-2009 MacBook Pro 15", perfect for on-site work and demos.

When I started working in this dual environment, one of my critical needs was to have all the latest files I work with to be available on *both* the laptop and the desktop. Which means I needed a way to synchronize the two computers.

Dropbox was not a viable option, the three folders that I need to be on both machines, *Documents*, *Projects* and *Pictures*, exceed the maximum Dropbox size, and I do not need them to sync in real time.

Having a server is not a viable option because my home IP connection is residential so my server is not readily accessible. I did try [DynDNS](http://dyn.com/dns/) for a while, and *Back to My Mac* too, but the connections were unreliable and slow. And I would need a network connection which is not always available when demoing.

So instead, I purchased [ChronoSync](http://www.econtechnologies.com/pages/cs/chrono_overview.html) ages ago and set up synchronizers for each of these folders. And it has worked beautifully for years.

Just before I leave the office with the Laptop, I boot it up, open ChronoSync and run a `sync-volatiles` container process which runs synchronizations for my *documents*, *projects* and *pictures* folders. This process is quite quick as ChronoSync only moves new or changed files between computers. When I return to my desk to continue working, I run the same process again to sync any laptop updates to the desktop.

The lovely benefits of this process are:

* I get what I want, all the same documents on both devices. I never have a situation where a key document I need is not directly available on my current device.
* I have an up-to-date backup of all my key working files on two machines, so I'm not worried if one dies.
* Even though I use `git` without fail for all my source code, I also sometimes have feature branches lying around, which I do not commit to [GitHub](https://github.com). This sync process ensures that these feature branches are available on both devices. I can stop working on one computer, and continue on the other without missing a beat

But the hassle is that I have to run this process *manually*. And I am an [automate or die](http://hiltmon.com/blog/2011/12/04/hiltmonism-automate-or-die/) fan. What I really want is for ChronoSync to detect *when* the desktop is on the same network and sync, without me doing anything. And I do *not* want it trying to sync when I am on another network or doing a demo.

I tried scripting this with `rsync` but the startup and read time for these large folders was too slow, and the network detection code I wrote was horrible.

Then I found the [ChronoSync Agent](http://www.econtechnologies.com/pages/ca/agent_overview.html), a $10.00 additional component that allows you to install an agent on one computer that talks to ChronoSync on another. It speeds up the already fast sync because the agent does its scanning locally instead of the remote having to scan over the network.

But the biggest win comes in the ChronoSync scheduler. I can now schedule a sync to happen when *an agent becomes available*. Which means that whenever my laptop *wakes up* on my home network and sees the agent running on my desktop, it does a fast sync. Every time. All I have to do is flip up the screen, and it just works.

I had seen the agent advertised on the ChronoSync website before, but only now realize how awesome it really is, and how much effort it saves me. My desktop and my laptop remain in sync automatically. Thank you, [@JoeJapes](https://twitter.com/JoeJapes) and the gang at [@econriver](https://twitter.com/econriver).

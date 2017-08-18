---
layout: post
title: "An Xcode C++ Client-Server Development Trick"
date: 2014-07-30 19:57:01 -0400
comments: true
categories: [ c++ ]
---

I'm working on a C++ product that has a series of client executables that need to talk to a server executable. And they all share a lot of common code.

{% img right /images/xcode-trick-0.png 256 142 %}

The traditional approach to build and debug this pattern is to create a library of the common code in one project, a separate server project and another client project, then jump between windows to edit and compile where needed.

**But I am often coding on my trusty 13" MacBook Air screen and it's just too tiny to have all these Xcode windows open with their console windows visible.** I even prefer this on the 27" Display where I can see documentation and other windows nearby.

{% img left /images/xcode-trick-1.png 443 235 %}

It turns out that Xcode *does* support running multiple targets simultaneously, and you can get away without the additional library compile.

Take this [spike](https://hiltmon.com/blog/2012/04/06/spike-solutions/) I am working with. It has two targets, `szp-server` and `szp-client` representing the server and client components.

{% img right /images/xcode-trick-2.png 131 82 %}

The common code is in the common folder. Each file in the common folder is assigned to both targets (in the **File Inspector Panel**) so they get caught by both project compiles.

{% img left /images/xcode-trick-3.png 233 132 %}

Each target also has a scheme, so each can be run as normal.

{% img right /images/xcode-trick-4.png 266 334 %}

The simple trick is that I can switch to the `szp-server` scheme and launch it (regular run or instruments), causing the `szp-server` to start and display its output in the console window. I can then leave it running while working on the `szp-client`.

I can select the `szp-client` scheme, edit, compile and run it as well. **Xcode treats the *second* run the same as another thread.** You can see its CPU and memory use, run one or the other in instruments and even switch console logs, *all in the same Xcode window*.

And the best part. One window, easy on the small screen and no switching windows.

*Follow the author as [@hiltmon](http://twitter.com/hiltmon) on Twitter and [@hiltmon](http://alpha.app.net/hiltmon) on App.Net. Mute `#xpost` on one.*

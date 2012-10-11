---
layout: post
title: "Sandboxing and Productivity Utilities"
date: 2012-06-11 09:02
comments: true
categories: [Productivity]
---

Apple's recent requirement for all App Store applications to be sandboxed has led to a problem for us pro users, many of our magical productivity utilities will no longer work. And if you think that's a problem for us, imagine how the developers feel.

## Er, Sandboxing?

Sandboxing is a computer security term for separating running programs so that they can only access a limited set of files and resources on your computer and not interfere with other programs and files. The idea is that each program requests access to only those things it needs to do, and the operating system ensures that the program cannot access anything else. So a sandboxed application may not have access to the network, or it can only access it's own files.

If a sandboxed app gets hacked, you, the user are safe. The worst a hacked sandboxed app can do is access its own stuff, leaving the rest of your computer and data safe.

## Sounds good, so what's the problem?

The key problems with Apple's implementation of Sandboxing are the lack of any option to enable interconnect with other applications, and a ban on cross application scripting.

Lets look at each.

I use [Moom](http://manytricks.com/moom/) to help manage and arrange my windows because I am still a spatial user. Moom works by adding a menu to the green "traffic light" button on each window, offering the user a menu to resize the window. But Moom also allows me to press a key combination, and rearrange a set of windows. In order to work, Moom needs to integrate with all running windows to move and resize them. This behavior is not allowed by sandboxing, nor is there any 'permission' available to get this to work. Moom cannot be sandboxed.

In the case of scripting, well, I use a combination of [Keyboard Maestro](http://www.keyboardmaestro.com/main/) macros and [Alfred](http://www.alfredapp.com/) scripts to automate many common actions that save me a lot of time every day. Since sandboxed applications cannot script the behavior of other applications, neither of these can be sandboxed either.

## From App Store to direct

This does not mean that Moom, Keyboard Maestro and Alfred are going away, just that their App Store versions may. The problem is, how does one convert from an App Store version of an application to a direct version, without having to pay for the application again?

The ManyTricks team have come up with a very elegant solution for Moom 3. If you have Moom 2 from the App Store, just directly download and install Moom 3 and it detects that you used to have the App Store version, and licenses itself. What a brilliant idea. And if anyone in the future buys the old version on the App Store, on first launch, it tells you how to upgrade. The only negative is that these App Store users remain anonymous. I just went and bought another license directly, because I want them to know I am a happy customer.

Alfred takes a different tack. The core product, available on the App Store, can work under sandboxing for search and opening files. But the scripting support is unavailable. They offer a powerpack which requires a direct download, and replaces the App Store version. Since this is a direct copy, it's not sandboxed and scripting works.

## How bad is it

It's not that bad. For the majority of users, especially non-pro users, sandboxing is a good thing.  Apps cannot get malicious on them. And they do not really use these productivity tools anyway.

For us pro's, we can get what we need directly, so that's not an issue. The only thing we miss out on at the moment is iCloud synching (but Dropbox does a good enough job). Who knows what we may miss out on in the future though.

But right now, I commend the makers of my favorite productivity utilities for their ingenious solutions to finding ways to migrate anonymous App Store users into direct users without paying again.

---
layout: post
title: "Day One iCloud Sync Fail"
date: 2012-11-17 14:08
comments: true
categories: 
---

I use the [Day One](http://dayoneapp.com) journalling program a lot, especially to log commits and all social activity using [Slogger](http://ttscoff.github.com/Slogger/). But today I noticed that the Journals on all my devices were out of sync, and new entries created were not passed on to other devices. Somehow, sync was jammed up.

I have Day One on

* My home server where Slogger runs
* My laptop, where I work
* My iPad, where I chill
* My iPhone, where everything needs to be available

And they are all kept in sync via iCloud. Until 2 days ago. Then  it stopped.

On investigation, it seems there were 29 files inside the iCloud  folder for Day One that were grayed out and displaying the OS X progress bar next to them. From what I could tell, these files were supposed to be downloading from iCloud but did not come in.  For 2 days they dod not download. A check on my iOS devices and the same thing was happening, 29 files were in downloading status and never came down.

I tried:

* Rebooting all devices, even the server, no change
* Deleting the pending files, and they came back, but remained in downloading state
* Copying them from another system, and they showed up in Day One, but syncing was still busted
* I started to see `sandboxd: ([1674]) Day One(1674) deny forbidden-link-priv` errors in console, coincidentally, 29 times, for these files

Short version, iCloud was saying there were 29 updates, and *never* finished delivering them. And there seems to be nothing you can do to reset or force these to unstick. And I don't think there is anything the developer of Day One can do about it!

So, I finally gave up. I disabled iCloud syncing on Day One and enabled [Dropbox](http://www.dropbox.com) sync instead. The laptop and server switched over OK (once I manually replaced the in-progress files) and creating an entry in one appears in the other.

On iOS though, things get hairier. These pending updates prevented Day One from accessing its own files, so iCloud sync could not complete disablement. It got to 98% and then just sat there. I had to uninstall the app, turn iCloud Documents and Data sync off in iOS Settings to delete *all* my iCloud data on the device, then reinstall the app and set it up to use Dropbox instead. Oh, and then re-enable iCloud documents for everything else.

The restores are in progress, and there are the odd Day One crashes as it restores, but the missing entries have already synced.

In short, the black-box nature of iCloud sucks when trying to troubleshoot or fix sync errors. The developer of Day One does not pick sides between iCloud and Dropbox sync. I for one, do recommend you sync your Day One data using Dropbox.

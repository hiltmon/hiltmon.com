---
layout: post
title: "Gist.tmbundle Updates"
date: 2013-03-11 16:59
comments: true
categories: [ TextMate ]
---

I just pushed a few small updates to my [Gists bundle](https://github.com/hiltmon/Gist.tmbundle) for TextMate 2. These include:

* Adding progress bars for network access (Thanks for the suggestion and tip from [Allan Odgaard](https://github.com/sorbits)).
* **New: Add file to Gist** command to add the current file to an existing Gist to create multi-file Gists. For example, use this to gist the header and implementation code files in the same gist. This gets cached so you can blindly update any of the files in a multi-file gist without remembering the gist ID.
* **New: Gist from Selection** command to create a new gist with the selected text. This command, like all the others, leaves the URL of the gist on the clipboard so it's easy to create a gist from selection, then paste the URL into a blog post or email. **Note** that gists from selections are *not* cached as they have no file names.

This Gists bundle is now part of the standard TextMate Bundle distribution. You can find this bundle in **TextMate → Preferences → Bundles → Gist** where it can be enabled.

*Follow the author as [@hiltmon](http://https://twitter.com/hiltmon) on Twitter and [@hiltmon](http://alpha.app.net/hiltmon) on App.Net. Mute `#xpost` on one.*
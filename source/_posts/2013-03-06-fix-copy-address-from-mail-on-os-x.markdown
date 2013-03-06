---
layout: post
title: "Fix Copy Address from Mail on OS X"
date: 2013-03-06 12:03
comments: true
categories: [ OS X ]
---

In Apple's Mail.app, when you right click on an email address and choose "Copy Address", Apple decided that you would inexplicably also want the name part, so the string copied looks like this:

	Hilton Lipschitz <me@hiltmon.com>

I have yet to find a single occasion when I wanted anything but the email address part.

To correct this issue, jump into a terminal session and use:

	defaults write com.apple.mail AddressesIncludeNameOnPasteboard -bool NO

Quit and restart Mail.app. Copy an email address and you get an email address:

	me@hiltmon.com

This is one of those simple annoyances on OS X that I wish Apple would just change the default by default.

*Follow the author as [@hiltmon](http://twitter.com/hiltmon) on Twitter and [@hiltmon](http://alpha.app.net/hiltmon) on App.Net. Mute `#xpost` on one.*
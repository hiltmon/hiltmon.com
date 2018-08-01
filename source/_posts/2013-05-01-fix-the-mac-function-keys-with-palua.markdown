---
layout: post
title: "Fix the Mac Function Keys with Palua"
date: 2013-05-01 13:04
comments: true
categories: [ Productivity, Reviews ]
---

{% img right /images/keyboard-f1.jpg 269 187 %}

By default, the function keys on Apple keyboards are mapped to the *Apple* functions on them, like brightness, volume and Mission Control. To access them as F1 - F12 requires you to hit the `fn` key as well. You could always reverse this in **Preferences** / **Keyboard** by checking **Use all F1, F2, etc. keys as standard function keys**.

But this change is *system-wide*. What if you want the default *Apple* behavior *most of the time*, but *Function* key behavior in certain applications, for example, in virtual machines?

{% img left /images/Palua.png 128 128 %}

[Palua][linksynergy] is a simple menu-bar applet that allows the user to easily switch between *Apple* and *Function* key behavior using a keyboard shortcut. Tap the shortcut and the mode changes.

But I don't use it that way.

{% img right /images/palua-smart-mode.jpg 301 237 %}

[Palua][linksynergy]'s true power comes when you enable **Smart Mode** in its **Preferences**. Here, you can set which keyboard mode to use for which application, and [Palua][linksynergy] makes the switch for you *automatically*. Brilliant!

In my case, I have *Function* mode enabled for [VMWare Fusion][vmware] so hosted VM's see the `F?` keys, and for Apple's Mail.app so that I can use the Function keys directly for [Mail Act-On][indev] behaviors. At the moment, I use *Apple* mode for the rest.

[Palua][linksynergy] is a lovely little utility that does *one thing well*, and then does it smartly: It automatically switches my keyboard mode based on the currently active app. I have it running all the time and managed by [MacBartender][macbartender].

Available on the [App Store][linksynergy] for 99c (US) as of writing.

*Follow the author as [@hiltmon][twitter] on Twitter and [@hiltmon][app] on App.Net. Mute `#xpost` on one.*

[app]: http://alpha.app.net/hiltmon
[indev]: http://www.indev.ca/MailActOn.html
[linksynergy]: https://itunes.apple.com/us/app/palua/id431494195?mt=12&uo=4&at=10l894
[macbartender]: http://www.macbartender.com
[twitter]: https://twitter.com/hiltmon
[vmware]: http://www.vmware.com/products/fusion/overview.html

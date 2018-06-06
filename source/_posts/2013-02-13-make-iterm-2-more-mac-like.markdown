---
layout: post
title: "Make iTerm 2 more Mac-like"
date: 2013-02-13 12:08
comments: true
categories: [ Macintosh ]
---

I just switched from using Apple’s built-in Terminal.app to the free [iTerm 2](http://www.iterm2.com/#/section/home) on a recommendation from [Brett Terpstra](http://brettterpstra.com). I’m already loving the hot-key profiles to launch uniquely colored remote sessions, the split panes, and the brilliant hotkey window (useful to run a single command and get rid of it).

But there are a few things that needed some work. Some of the usual Mac editing keys did not work, I got rid of a few annoyances and added a few lovely preferences, and I needed the ability to create a new terminal window on the *current* space as part of my [being productive with virtual desktops](https://hiltmon.com/blog/2013/01/17/being-productive-with-virtual-desktops/) flow (Just like [Browser Windows on All Desktops](https://hiltmon.com/blog/2013/01/19/browser-windows-on-all-desktops/)).

### Mac-like keys

Since I’m not a `vi` or `emacs` pianist, I prefer standard Apple Cocoa Text bindings when editing the command line, so I set them up in iTerm 2’s **Global Shortcut Keys** in **Preferences** / **Keys**.

{% img /images/iterm2-keys.png 527 438 %}

The changes and settings are:

* ⌥←: Go left one word (Send Escape Sequence | b)
* ⌥→: Go right one word (Send Escape Sequence | f)
* ⌘←: Go to start of line (Send Hex Code | 0x01)
* ⌘→: Go to end of line (Send Hex Code | 0x05)
* ⇧⌘↑: Up one page
* ⇧⌘↓: Down one page
* ⌃⌘↓: Down to bottom *(not standard Cocoa, but I find it very useful when perusing real time rails logs)*

Thanks to [Brett Terpstra](http://brettterpstra.com) for sharing some of these in his [Option-arrow navigation in iTerm2](http://brettterpstra.com/2011/08/12/option-arrow-navigation-in-iterm2/) and Twitter. *Note: I do **not** set the Left Option and Right Option keys in profiles to `+ESC`, I leave them as `Normal` (as per Scott Lee’s response in the comments).*

### Annoyances and Preferences

I don’t need to confirm quitting (**Preferences** / **General**):

{% img /images/iterm-1.png 299 108 %}

I *love* copy on select, it’s one less keystroke and I usually select with the mouse (**Preferences** / **General**):

{% img /images/iterm-2.png 282 74 %}

The red tabs were annoying, gone (**Preferences** / **Appearance**):

{% img /images/iterm-3.png 305 170 %}

Added the border around frames, I *like* this because my terminal background and screen backgrounds are both dark (**Preferences** / **Appearance**):

{% img /images/iterm-4.png 386 90 %}

And got rid of the bell icon and Growl notifications in all profiles (**Preferences** / **Profiles** / ****** / **Terminal**):

{% img /images/iterm-5.png 511 76 %}

And lowered the line spacing to match Apple’s (**Preferences** / **Profiles** / ****** / **Text** / `Change Font`) - just move the vertical back 1 notch:

{% img /images/iterm-6.png 459 508 %}

### New iTerm 2 in Current Space

While it’s nice to have the hotkey window, I often find myself working on Desktop 1 (Work) and need to jump to Desktop 2 (Alternate) to do some other stuff *and leave a terminal running there*. Like now, for example, I have a database migration running on Desktop 1 for [Kifu](http://www,kifuapp.com) and am blogging on Desktop 2, both of which require running iTerm 2 windows.

If you hit ‘⌘N’ on iTerm 2 (or any other OS X app), OS X switches you to the app’s desktop, *then* creates a new window *over there*, not what I want. If you right-click on the dock and request a new window, it creates it on the *current* desktop. But I leave my dock hidden.

I used to have `⌃⌘T` mapped to do this for Terminal.app, so I created a [Keyboard Maestro](http://www.keyboardmaestro.com/main/) macro to do this for [iTerm 2](http://www.iterm2.com/#/section/home) instead:

{% img /images/iterm2-macro.png 559 411 %}

The first step, the AppleScript code, launches a new “Default” terminal, and it does so on the *current* space:

``` applescript
tell application "System Events"
    set mycount to count (every process whose name is "iTerm")
end tell

tell application "iTerm"
    -- Nuke the default new terminal on first launch
    -- And ignore other terminals otherwise
    if mycount = 0 then
        activate
        terminate the first session of the first terminal
    end if
    
    tell (make new terminal)
        launch session "Default"
    end tell
    activate
end tell
```

The second step resizes the window so that it is 100 x 42 lines, my personally preferred terminal window size.

So far, I am really enjoying the small touches that make [iTerm 2](http://www.iterm2.com/#/section/home) that much better than Terminal.app.

Related Reading: [Fast SSH Windows With iTerm 2](https://hiltmon.com/blog/2013/07/18/fast-ssh-windows-with-iterm-2/)

*Follow the author as [@hiltmon](http://https://twitter.com/hiltmon) on Twitter or [@hiltmon](http://alpha.app.net/hiltmon) on App.Net.*

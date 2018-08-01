---
layout: post
title: "Using Mac Navigation Keys in Visual Studio"
date: 2013-10-10 12:32
comments: true
categories: 
---

As a developer, sometimes I am forced to use Visual Studio to code for Windows. Just like a lot of Mac developers, I therefore run Visual Studio in a [VMWare Fusion](http://www.vmware.com/products/fusion/) VM. And it works great.

Except it drives me nuts that keyboard navigation in the Visual Studio editor does not use the same keys as on the Mac. Which means I am constantly seeing the window move around when I am trying to get to a line end. And even if I did remap my brain to Visual Studio's keys, it assumes I have a `Home` and an `End` key to use, which the Mac mini wireless keyboard and laptops do not have.

I tried changing keys in **Tools / Options / Environment / Keyboard** but Visual Studio studiously *ignores* any shortcuts which use the `Windows` key which *just happens* to be the `Command` key on the Mac keyboard which *just happens* to be a commonly used shortcut for navigation on the Mac.

The solution I found is to install [AutoHotKey](http://www.autohotkey.com) on the VM and remap the Visual Studio keys you need. Here is my AutoHotKey script file so far:

	; AutoHotKey Script

	SetTitleMatchMode, 2  ; Move this line to the top of your script

	#IfWinActive, Microsoft Visual Studio
	#Right::End
	#Left::!Left
	#Up::^Home
	#Down::^End
	!Right::^Right
	!Left::^Left
    #b::^B
    #K::^M
	#/::!/

	#IfWinActive

I have set this up so the changes only apply to Visual Studio. All other Windows applications will remain unaffected. The `SetTitleMatchMode` is needed to make it so that the matcher sees the right title.

The `#IfWinActive, Microsoft Visual Studio` line means that all changes that follow until the next `#IfWinActive` apply only to Visual Studio windows.

My mapping changes are as follows:

* ⌘→: **Edit.LineEnd** (Default windows key `End`, original behavior: Snap window to right of screen)
* ⌘←: **Edit.LineStart** (Default windows key `Home`, original behavior: Snap window to left of screen) *but I had to map this to `ALT-←` and change the mapping in Visual Studio* (see below). This is because Windows 8 intercepts the `Home` key, minimizes all other windows and does not pass it on to Visual Studio.
* ⌘↑: **Edit.DocumentStart** (Default windows key `CTRL+HOME`)
* ⌘↓: **Edit.DocumentEnd** (Default windows key `CTRL+END`)
* ⌘/: **Edit.CommentSelection** (Visual Studio `CTRL+K,CTRL+C`) mapped to `ALT+/` and remapped in Visual Studio.
* ⌥→: **Edit.WordNext** (Default windows key `CTRL+RIGHT`) but somehow this combination does not work on my system natively or adjusted.
* ⌥←: **Edit.WordPrevious** (Default Windows key `CTRL+LEFT`) also not working.
* ⌘b: **Build.BuildSolution** (Visual Studio `CTRL-SHIFT-B`) to match Xcode.
* ⌘K: **Build.CleanSolution** (No key) Manually mapped to `CTRL-SHIFT-M`.

Some of these mappings require you to change the Visual Studio keys. To do so, go to **Tools / Options / Environment / Keyboard**.

{% img /images/vs_keyboard.jpg 785 469 %}

First, find the key mapping you would like to change (See 1). In this case, I am remapping `Edit.LineStart`. You should see `Home (Text Editor)` under **Shortcuts for selected command:** (I have already changed mine).

To set the new shortcut, see 2:

- Make sure that `Text Editor` is chosen under **Use new shortcut in:**
- Press the shortcut key in the blank space and make sure that it gets shown correctly.
- Click **Assign** to save it.


I have only just started using this solution, but already its 100% easier for me to navigate around my Visual Studio code files (and the window no longer jumps around).

*If you try this out and find any other tricks, let me know in the comments and I'll add the best ones here.*

Back to coding in Visual Studio on a Mac!

*Follow the author as [@hiltmon](https://twitter.com/hiltmon) on Twitter and [@hiltmon](http://alpha.app.net/hiltmon) on App.Net. Mute `#xpost` on one.*

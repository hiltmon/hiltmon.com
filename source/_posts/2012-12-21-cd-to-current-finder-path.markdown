---
layout: post
title: "CD to Current Finder Path"
date: 2012-12-21 08:29
comments: true
categories: Productivity
---

To open a *new* terminal in the current Finder path in OS X, you can use the built-in service (See below on how to enable). But if you are *already* in a Terminal session, you need to leave the keyboard, mouse to Finder and drag and drop the path back. Here’s a trick that gets you to the frontmost Finder path without leaving the Terminal or keyboard.

Add the following to your `.bash_profile`:

``` sh
## Get the frontmost finder path
fp () {
	osascript << EOT

	tell application "Finder"
		if (${1-1} <= (count Finder windows)) then
			get POSIX path of (target of window ${1-1} as alias)
		else
			get POSIX path of (desktop as alias)
		end if
	end tell

	EOT
}

## alias to cd to the frontmost finder path
alias cdf='cd "`fp`"'
## alias to copy it to the clipboard
alias cfp='fp | pbcopy'
```

In a *new* Terminal (or reload the current), you now have the following commands available:

* `cdf` which will `cd` you to the frontmost finder path
* `cfp` which will copy the frontmost finder path onto the pasteboard

I usually leave my current working folder visible in Finder so I can see the files available while working in Terminal. To get back to that folder, a quick `cdf` and I’m there.

---

### **OR: Enable the Service**

To open a new terminal window at the current Finder path from Finder, you need the `New Terminal at Folder` service enabled. Make sure it’s checked in **System Preferences** / **Keyboard** / **Keyboard Shortcuts** / **Services** under **Files and Folders**.

Once enabled, you can right click on any folder in Finder, choose **Services** / **New Terminal at Folder** to open a new Terminal at that location.

{% img /images/new-terminal-at-folder.jpg 568 287 %}

*Follow the author as [@hiltmon](http://twitter.com/hiltmon) on Twitter or [@hiltmon](http://alpha.app.net/hiltmon) on App.Net.*
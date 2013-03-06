---
layout: post
title: "Fixing Open With in OS X"
date: 2012-10-13 12:11
comments: true
categories: [ OS X ]
---

If you use the **Open With...** contextual menu on OS X (right-click on a file in Finder), you may find a lot of applications get duplicated or are just plain wrong. This is how you reset this menu.

In my case I had this for Markdown files:

{% img /images/open-with-before.jpeg 576 603 %}

What a mess. Open a Terminal session from **Applications/Utilities** and type the following command:

```
/System/Library/Frameworks/CoreServices.framework/Versions/A/Frameworks/LaunchServices.framework/Versions/A/Support/lsregister -kill -r -domain local -domain system -domain user
```

Make sure the whole thing is on a single line and wait for it to finish.

Then restart Finder. Hold the control key and the option key and right-click on the Finder icon in the dock to bring up the menu:

{% img /images/open-with-relaunch.jpeg 220 335 %}

Click on **Relaunch** to restart the Finder.

Now, when you use **Open With...**, you get a much better list:

{% img /images/open-with-after.jpeg 576 337 %}

*Note: Tested only on Mountain Lion, should work on older versions.*

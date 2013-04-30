---
layout: post
title: "Top Pages in Status Board"
date: 2013-04-10 16:06
comments: true
categories: [ Status Board ]
---

Following up this morning's [Google Analytics for Status Board](http://www.hiltmon.com/blog/2013/04/10/google-analytics-for-status-board/) graph on [Status Board](http://click.linksynergy.com/fs-bin/stat?id=V41G*FiMqjc&offerid=146261&type=3&subid=0&tmpid=1826&RD_PARM1=https%253A%252F%252Fitunes.apple.com%252Fus%252Fapp%252Fstatus-board%252Fid449955536%253Fmt%253D8%2526uo%253D4%2526partnerId%253D30), I also wanted a **top pages for today** view for Hiltmon.com.

<span class="light">See also [Hourly Stats](http://www.hiltmon.com/blog/2013/04/15/hourly-analytics-for-status-board/) and [OS and Browser Stats](http://www.hiltmon.com/blog/2013/04/17/add-ga-os-and-browser-to-status-board/).</span>

{% img /images/status-board-pages.jpg 640 480 %}

The steps are all the same as [Google Analytics for Status Board](http://www.hiltmon.com/blog/2013/04/10/google-analytics-for-status-board/), so follow along, only replace those script and the launcher files with these.

The script code is:

{% gist 5358000 status_board_pages.rb %}

Once again, edit the script to change:

* The **email** and **password** you use to access Google Analytics.
* The **title**, **file_name** and **dropbox_path** to save the data on your computer and dropbox.
* The home title at line 60: replace ` - The Hiltmon` with your own tagline.

The launcher code is:

{% gist 5358005 com.hiltmon.status_board_pages.plist %}

Update it too for your paths and names, the copy and load it.

**Add it to Status Board**

Follow the instructions in [Table Tutorial (PDF)](http://www.panic.com/statusboard/docs/table_tutorial.pdf):

* Share the CSV file on your DropBox
* Mail that link to yourself
* Tap the link in the email on your iPad to open it in Safari
* Copy the link from Safari (minus the bit after the `?`)
* Add a new **table** to your Status Board and paste in the link (it offers to do this by default).

Enjoy.

*Update: All the scripts can be downloaded from Github at [https://github.com/hiltmon/status-board-ga](https://github.com/hiltmon/status-board-ga).*

*Follow the author as [@hiltmon](http://twitter.com/hiltmon) on Twitter and [@hiltmon](http://alpha.app.net/hiltmon) on App.Net. Mute `#xpost` on one.*



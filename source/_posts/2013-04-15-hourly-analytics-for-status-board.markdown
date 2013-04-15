---
layout: post
title: "Hourly Analytics for Status Board"
date: 2013-04-15 10:23
comments: true
categories: [ Status Board ]
---

Following up last week's [Google Analytics for Status Board](http://www.hiltmon.com/blog/2013/04/10/google-analytics-for-status-board/) graph and [Top Pages](http://www.hiltmon.com/blog/2013/04/10/top-pages-in-status-board/) table on [Status Board](http://click.linksynergy.com/fs-bin/stat?id=V41G*FiMqjc&offerid=146261&type=3&subid=0&tmpid=1826&RD_PARM1=https%253A%252F%252Fitunes.apple.com%252Fus%252Fapp%252Fstatus-board%252Fid449955536%253Fmt%253D8%2526uo%253D4%2526partnerId%253D30), a reader asked for **hourly stats** instead of daily, so I created it (see the bottom-right graph).

<span class="light">See also [Top Pages in Status Board](http://www.hiltmon.com/blog/2013/04/10/top-pages-in-status-board/) and [Daily Stats](http://www.hiltmon.com/blog/2013/04/10/google-analytics-for-status-board/).</span>

{% img /images/status-board-hourly.jpg 640 480 %}

The script creates a 24-hour rotating window of stats using your local time-zone for reference. *Note that I have only tested this in US EST, but it should work elsewhere.*

The steps are all the same as [Google Analytics for Status Board](http://www.hiltmon.com/blog/2013/04/10/google-analytics-for-status-board/), so follow along, only replace that script and the launcher files with these.

* Install the `json` and `gattica` gems
* Configure the script with your own parameters (and optionally change the Google Analytics account using the script at [https://gist.github.com/hiltmon/5373934](https://gist.github.com/hiltmon/5373934)  to get the index and uncomment line 45 to set it).
* Schedule the script to run by modifying the `.plist` file below to reflect your path to the script, then copying it to `~/Library/LaunchAgents` and loading it with `launchctl`

The script code is:

{% gist 5388421 status_board_hourly.rb %}

Once again, edit the script to change:

* The **email** and **password** you use to access Google Analytics.
* The **title**, **file_name** and **dropbox_path** to save the data on your computer and dropbox.

The launcher code is:

{% gist 5388453 com.hiltmon.status_board_hourly.plist %}

Update it too for your paths and names, the copy and load it.

**Add it to Status Board**

Follow the instructions in [Graph Tutorial (PDF)](http://www.panic.com/statusboard/docs/graph_tutorial.pdf):

* Share the JSON file on your DropBox
* Mail that link to yourself
* Tap the link in the email on your iPad to open it in Safari
* Copy the link from Safari (minus the bit after the `?`)
* Add a new **graph** to your Status Board and paste in the link (it offers to do this by default).

Enjoy.

*Follow the author as [@hiltmon](http://twitter.com/hiltmon) on Twitter and [@hiltmon](http://alpha.app.net/hiltmon) on App.Net. Mute `#xpost` on one.*
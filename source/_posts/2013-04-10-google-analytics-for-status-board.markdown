---
layout: post
title: "Google Analytics for Status Board"
date: 2013-04-10 12:15
comments: true
categories: 
---

I wanted to see the 7-day Hiltmon.com web stats from Google Analytics on Panic's new [Status Board app](http://click.linksynergy.com/fs-bin/stat?id=V41G*FiMqjc&offerid=146261&type=3&subid=0&tmpid=1826&RD_PARM1=https%253A%252F%252Fitunes.apple.com%252Fus%252Fapp%252Fstatus-board%252Fid449955536%253Fmt%253D8%2526uo%253D4%2526partnerId%253D30). Here is how I got it to work.

 <span class="light">Update: Also added a script for [Top Pages in Status Board](http://www.hiltmon.com/blog/2013/04/10/top-pages-in-status-board/).</span>

**Warning: Very geeky. Use at your own peril. Only tested in my environment.**

{% img /images/status-board-ga.jpg 640 480 %}

### Step 1: Install the Gems

In order to make this work, you need Ruby, the `json` gem and the `gattica` gem. I am running this using the default Ruby on OS X (1.8.7).

Installing the `json` gem is easy:

	$ sudo gem install json

However the `gattica` gem requires a build because the posted one is too old:

	$ git clone git://github.com/chrisle/gattica.git
	$ cd gattica/
	$ gem build gattica.gemspec
	$ sudo gem install gattica-0.6.2.gem
	
*Note: You may need to install the default `gattica` gem and then do the build (happened on my test machine) in order to get dependencies.*

### Step 2: Configure the Script

Download the script from [this gist](https://gist.github.com/5356145) or copy and paste it from here:

{% gist 5356145 status_board_ga.rb %}

Edit the script to change:

* The **email** and **password** you use to access Google Analytics.
* The **title**, **file_name** and **dropbox_path** to save the data on your computer and dropbox.

Run the script to see if both the CSV and JSON get created in the required dropbox folder.

### Step 3: Schedule it to Run

We're going to run this script every 5 minutes. *Note: These are the OS X instructions, use a `crontab` entry on Linux systems.*

Create the following file `com.hiltmon.status_board_ga.plist` (modified for your path of course):

{% gist 5357965 com.hiltmon.status_board_ga.plist %}

Then copy it (you may need to create the folder) and start it:

	$ cp com.hiltmon.status_board_ga.plist ~/Library/LaunchAgents
	$ launchctl load -w ~/Library/LaunchAgents/com.hiltmon.status_board_ga.plist

### Step 4: Add it to Status Board

Follow the instructions in [Graph Tutorial (PDF)](http://www.panic.com/statusboard/docs/graph_tutorial.pdf):

* Share the JSON file on your DropBox
* Mail that link to yourself
* Tap the link in the email on your iPad to open it in Safari
* Copy the link from Safari (minus the bit after the `?`)
* Add a new graph to your Status Board and paste in the link (it offers to do this by default).

Enjoy.

Thanks to [Panic](http://www.panic.com) for creating such a lovely tool.

*Follow the author as [@hiltmon](http://twitter.com/hiltmon) on Twitter and [@hiltmon](http://alpha.app.net/hiltmon) on App.Net. Mute `#xpost` on one.*





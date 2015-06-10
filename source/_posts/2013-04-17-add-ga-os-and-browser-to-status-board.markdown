---
layout: post
title: "Add GA OS and Browser to Status Board"
date: 2013-04-17 11:02
comments: true
categories: [ Status Board ]
---

<span class="light">Google has finally deprecated their GAPI interface which this used to talk to Google Analytics, sorry folks, it will no longer work. See the [New Google Analytics for Status Board Server Edition]({{ root_url }}/blog/2015/06/07/new-google-analytics-for-status-board-server-edition/) for an updated version. </span>

Reader Brandon Cozart ([@brandoncozart](http://twitter.com/brandoncozart)) asked if it were possible to add **Browser** and **OS** statistics to the [Google Analytics for Status Board]({{ root_url }}/blog/2013/04/10/google-analytics-for-status-board/) scripts. So I gave it a shot.

<span class="light">Update: Download again if you use these scripts, a null value bug and sorting bugs have been fixed.</span>

{% img /images/status-board-browser.jpg 640 480 %}

**Note:** The installation instructions below assume you have already gotten one of my [Google Analytics for Status Board]({{ root_url }}/blog/2013/04/10/google-analytics-for-status-board/) scripts to install and work, so this only shows the changes that need to be made to setup these. If not, follow the instructions in [Google Analytics for Status Board]({{ root_url }}/blog/2013/04/10/google-analytics-for-status-board/) replacing the script and `.plist` files with these below.

All the source code for these scripts and `launchd` files is in the Github Repo at [https://github.com/hiltmon/status-board-ga](https://github.com/hiltmon/status-board-ga). I recommend cloning this repo **and then copying** the files to where you need them on your local system, or you can copy and paste the file contents directly from Github into your own editor. *You need to modify these scripts and files to make them work for you.*

### Browsers

The big issue was that there are too many browsers that can be reported. So I picked a few, and lumped the remainder in an **Other** category. Also, some browsers have multiple names, so I merged those manually in the script.

The script to generate the browser file is at [https://raw.github.com/hiltmon/status-board-ga/master/status_board_browsers.rb](https://raw.github.com/hiltmon/status-board-ga/master/status_board_browsers.rb). Copy and paste it into your own `status_board_browsers.rb` file and `chmod +x` it to make it executable.
file
Then, edit the file to change the configuration, changing **email**, **password**, **title**, **file_name** and **dropbox_path**. Test run the script to see that it creates the `JSON` file you need. Then share it from Dropbox, email it to yourself, open the link and add it to Status Board as per previous scripts.

The `.plist` to make this run automatically is at [https://raw.github.com/hiltmon/status-board-ga/master/com.hiltmon.status_board_browsers.plist](https://raw.github.com/hiltmon/status-board-ga/master/com.hiltmon.status_board_browsers.plist). Copy, paste, edit it with the right path, and `launchd load -w ...` it.

## Operating Systems

In this case I just picked the ones I was interested in and are popular on my site: Mac, iOS, Windows, Linux and Android. All others I ignore. You can, of course, edit the script to change the set I use, but make sure that they match *exactly* the names that get picked up in the `the_os` variable at line 61.

The script to generate the browser file is at [https://raw.github.com/hiltmon/status-board-ga/master/status_board_os.rb](https://raw.github.com/hiltmon/status-board-ga/master/status_board_os.rb). It's matching `.plist` is at [https://raw.github.com/hiltmon/status-board-ga/master/com.hiltmon.status_board_ga.plist](https://raw.github.com/hiltmon/status-board-ga/master/com.hiltmon.status_board_ga.plist).

Enjoy.

*Follow the author as [@hiltmon](http://twitter.com/hiltmon) on Twitter and [@hiltmon](http://alpha.app.net/hiltmon) on App.Net. Mute `#xpost` on one.*



---
layout: post
title: "Google Analytics for Status Board"
date: 2013-04-10 12:15
comments: true
categories: [ Status Board ]
---

<span class="light">Google has finally deprecated their GAPI interface which this used to talk to Google Analytics, sorry folks, it will no longer work. See the [New Google Analytics for Status Board Server Edition]({{ root_url }}/blog/2015/06/07/new-google-analytics-for-status-board-server-edition/) for an updated version. </span>

I wanted to see the 7-day Hiltmon.com web stats from Google Analytics on Panic's new [Status Board app](https://itunes.apple.com/us/app/status-board/id449955536?mt=8&uo=4&at=10l894). Here is how I got it to work.

**Update: For a far simpler install that runs on your web server using PHP, see [Google Analytics for Status Board Server Edition]({{ root_url}}/blog/2013/05/30/google-analytics-for-status-board-server-edition/).**

<span class="light">Update: Also added a script for [Top Pages in Status Board](https://hiltmon.com/blog/2013/04/10/top-pages-in-status-board/), for [Hourly Stats](https://hiltmon.com/blog/2013/04/15/hourly-analytics-for-status-board/) and for [OS and Browser Stats](https://hiltmon.com/blog/2013/04/17/add-ga-os-and-browser-to-status-board/).</span>

**Warning: Very geeky. Use at your own peril. Only tested in my environment.**

{% img /images/status-board-ga.jpg 640 480 %}

### Step 1: Install the Gems

In order to make this work, you need Ruby, the `json` gem and the `gattica` gem. I am running this using the default Ruby on OS X (1.8.7).

Installing the `json` gem is easy:

	$ sudo gem install json

However the `gattica` gem requires a build because the posted one is too old:

	$ git clone git://github.com/chrisle/gattica.git
	$ cd gattica/
	$ bundle install
	$ gem build gattica.gemspec
	$ sudo gem install gattica-0.6.2.gem
	
*Update: Added the `bundle install` step to install dependencies. No need to install the old gem first as per old instructions and comments below. You may need to `sudo bundle install` on a production box.*

### Step 2: Configure the Script

Download the script from [this gist](https://gist.github.com/hiltmon/5356145) or copy and paste it from here:

``` ruby
#!/usr/bin/env ruby

# status_board_ga.rb
# Hilton Lipschitz 
# Twitter/ADN: @hiltmon 
# Web: https://hiltmon.com
# Use and modify freely, attribution appreciated
#
# Script to generate @panic status board files for Google Analytics web stats.
#
# Run this regularly to update status board
#
# For how to set up, see https://hiltmon.com/blog/2013/04/10/google-analytics-for-status-board/

# Include the gems needed
require 'rubygems'
require 'gattica'
require 'date'
require 'json'

# Your Settings
google_email   = 'hiltmon@gmail.com'  # Your google login
google_pwd     = 'I_aint_sayin'   # Must be a single use password if 2 factor is set up
the_title      = "Hiltmon.Com Stats"  # The title of the Graph
file_name      = "hiltmondotcom"      # The file name to use (.CSV and .JSON)
dropbox_folder = "/Users/Hiltmon/Dropbox/Data" # The path to a folder on your local DropBox

# Configuration 
metrics = ['pageviews', 'visitors', 'newVisits']
colors = ['red', 'green', 'blue']
days_to_get = 7

# Login
ga = Gattica.new({ 
    :email => google_email, 
    :password => google_pwd
})

# Get a list of accounts
accounts = ga.accounts

# Choose the first account
ga.profile_id = accounts.first.profile_id
# ga.profile_id = accounts[1].profile_id # OR second account

# Get the data
data = ga.get({ 
    :start_date   => (Date.today - days_to_get).to_s.split('T')[0],
    :end_date     => Date.today.to_s.split('T')[0],
    :dimensions   => ['date'],
    :metrics      => metrics,
})

# Make the CSV file
File.open("#{dropbox_folder}/#{file_name}.csv", "w") do |f|
  f.write "#{the_title},#{metrics.join(',')}\n"
  data.to_h['points'].each do |point|
    the_date = Date.parse(point.to_h["dimensions"].first[:date]).to_s.split('T')[0]
    the_data = point.to_h["metrics"].map { |e| e.values.first }
    f.write the_date + "," + the_data.join(',') + "\n"
  end
end

# Make the JSON file
graph = Hash.new
graph[:title] = the_title
graph[:type] = 'bar'
index = 0
graph[:datasequences] = Array.new

metrics.each do |element|
  sequence = Hash.new
  sequence[:title] = element
  sequence_data = Array.new
  data.to_h['points'].each do |point|
    the_title = Date.parse(point.to_h["dimensions"].first[:date]).to_s.split('T')[0]
    the_value = point.to_h["metrics"][index][element.to_sym]
    sequence_data << { :title => the_title, :value => the_value }
  end
  sequence[:datapoints] = sequence_data
  sequence[:color] = colors[index]
  index += 1
  graph[:datasequences] << sequence
end

File.open("#{dropbox_folder}/#{file_name}.json", "w") do |f|
  wrapper = Hash.new
  wrapper[:graph] = graph
  f.write wrapper.to_json
end
```

Edit the script to change:

* The **email** and **password** you use to access Google Analytics.
* The **title**, **file_name** and **dropbox_path** to save the data on your computer and dropbox.

***Note:** This script uses the **first** account. If you want to use a different account, comment out line 43 and uncomment line 44, replacing the `1` with the index of the account you want to use. Download, modify and run the script from [https://gist.github.com/hiltmon/5373934](https://gist.github.com/hiltmon/5373934) to see what indexes are available.*

Run the modified script to see if both the CSV and JSON get created in the required dropbox folder.

### Step 3: Schedule it to Run

We're going to run this script every 5 minutes. *Note: These are the OS X instructions, use a `crontab` entry on Linux systems.*

Create the following file `com.hiltmon.status_board_ga.plist` (modified for your path of course):

```
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE plist PUBLIC "-//Apple//DTD PLIST 1.0//EN" "http://www.apple.com/DTDs/PropertyList-1.0.dtd">
<plist version="1.0">
<dict>
    <key>Label</key>
    <string>com.hiltmon.status_board_ga</string>
    <key>ProgramArguments</key>
    <array>
        <string>/Users/Hiltmon/Dropbox/Scripts/status_board_ga.rb</string>
    </array>
    <key>StartInterval</key>
    <integer>300</integer>
</dict>
</plist>
```

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

*Update: All the scripts can be downloaded from Github at [https://github.com/hiltmon/status-board-ga](https://github.com/hiltmon/status-board-ga).*

*Follow the author as [@hiltmon](http://https://twitter.com/hiltmon) on Twitter and [@hiltmon](http://alpha.app.net/hiltmon) on App.Net. Mute `#xpost` on one.*





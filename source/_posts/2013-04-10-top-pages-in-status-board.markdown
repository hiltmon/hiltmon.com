---
layout: post
title: "Top Pages in Status Board"
date: 2013-04-10 16:06
comments: true
categories: [ Status Board ]
---

<span class="light">Google has finally deprecated their GAPI interface which this used to talk to Google Analytics, sorry folks, it will no longer work. See the [New Google Analytics for Status Board Server Edition]({{ root_url }}/blog/2015/06/07/new-google-analytics-for-status-board-server-edition/) for an updated version. </span>

Following up this morning's [Google Analytics for Status Board](http://hiltmon.com/blog/2013/04/10/google-analytics-for-status-board/) graph on [Status Board](https://itunes.apple.com/us/app/status-board/id449955536?mt=8&uo=4&at=10l894), I also wanted a **top pages for today** view for Hiltmon.com.

<span class="light">See also [Hourly Stats](http://hiltmon.com/blog/2013/04/15/hourly-analytics-for-status-board/) and [OS and Browser Stats](http://hiltmon.com/blog/2013/04/17/add-ga-os-and-browser-to-status-board/).</span>

{% img /images/status-board-pages.jpg 640 480 %}

The steps are all the same as [Google Analytics for Status Board](http://hiltmon.com/blog/2013/04/10/google-analytics-for-status-board/), so follow along, only replace those script and the launcher files with these.

The script code is in `status_board_pages.rb`:

``` ruby
#!/usr/bin/env ruby

# status_board_pages.rb
# Hilton Lipschitz
# Twitter/ADN: @hiltmon 
# Web: http://hiltmon.com
# Use and modify freely, attribution appreciated
#
# Script to generate @panic status board files for Google Analytics web stats
#
# Run this regularly to update status board
#
# For how to set up, see http://hiltmon.com/blog/2013/04/10/top-pages-in-status-board/

# Include the gem
require 'rubygems'
require 'gattica'
require 'date'
require 'json'

# Your Settings
google_email   = 'hiltmon@gmail.com'  # Your google login
google_pwd     = 'I_aint_sayin'   # Must be a single use password if 2 factor is set up
the_title      = "Hiltmon.Com Top Pages Today"
file_name      = "hiltmonpages"       # The file name to use (Assumes .CSV)
dropbox_folder = "/Users/Hiltmon/Dropbox/Data" # The path to a folder on your local DropBox

# Configuration
metrics = ['pageviews'] #, 'uniquePageviews', 'newVisits']
colors = ['red', 'green', 'blue']

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
    :start_date   => Date.today.to_s.split('T')[0],
    :end_date     => Date.today.to_s.split('T')[0],
    :dimensions   => ['pageTitle'],
    :metrics      => metrics,
    :sort         => ['-pageviews']
})

# # Make the CSV file
File.open("#{dropbox_folder}/#{file_name}.csv", "w") do |f|
  f.write "15%, 85%\n"
  count = 0
  data.to_h['points'].each do |point|
    the_page = point.to_h["dimensions"].first[:pageTitle].gsub(',', '').gsub(' - The Hiltmon', '')
    the_data = point.to_h["metrics"].map { |e| e.values.first }
    f.write the_data.join(',') + "," + the_page + "\n"
    count += 1
    break if count >= 20
  end
end
```

Once again, edit the script to change:

* The **email** and **password** you use to access Google Analytics.
* The **title**, **file_name** and **dropbox_path** to save the data on your computer and dropbox.
* The home title at line 60: replace ` - The Hiltmon` with your own tagline.

The launcher code is in `com.hiltmon.status_board_pages.plist`:

```
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE plist PUBLIC "-//Apple//DTD PLIST 1.0//EN" "http://www.apple.com/DTDs/PropertyList-1.0.dtd">
<plist version="1.0">
<dict>
    <key>Label</key>
    <string>com.hiltmon.status_board_pages</string>
    <key>ProgramArguments</key>
    <array>
        <string>/Users/Hiltmon/Dropbox/Scripts/status_board_pages.rb</string>
    </array>
    <key>StartInterval</key>
    <integer>300</integer>
</dict>
</plist>
```

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



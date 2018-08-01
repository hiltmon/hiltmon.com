---
layout: post
title: "Merge Asana Projects into OmniFocus (Updated)"
date: 2015-03-01 18:18:59 -0500
comments: true
categories: 
---

{% img right /images/asana_to_omnifocus.png 363 130 %}

A long long time ago in a galaxy far far away, I wrote a script to import Asana tasks into Omnifocus. If you ran it again, it would update the tasks in OmniFocus. See [Merge Asana Projects Into OmniFocus](https://hiltmon.com/blog/2013/11/03/merge-asana-projects-into-omnifocus/).

I recently updated the script to work a smidge better with Asana and Omnifocus 2. The main changes are:

* Date formats can be changed (for those of us not in the USA)
* The Non-Project tasks now load

### Setup

First, follow the instructions from the [original post](https://hiltmon.com/blog/2013/11/03/merge-asana-projects-into-omnifocus/) to set up Omnifocus and get your API keys.

Download the updated script from [https://gist.github.com/hiltmon/d1f79e95dd11252ce6ca](https://gist.github.com/hiltmon/d1f79e95dd11252ce6ca).

Open it in a text editor and insert Your API Key and Profile Name in the slots provided. You can also change the date format to suit.

```
class MergeAsanaIntoOmnifocus
  
  API_KEY = '<YOUR KEY HERE>'
  ASIGNEE_NAME = '<YOUR PROFILE NAME HERE>'
  SUBTASKS = true
  DATE_FORMAT = '%A %B %d, %Y at %H:%M:%S' # (Try http://strftimer.com to build your own)
 ```
 
 Make sure the prerequisites are in-place from the old post and then run it
 
	 $ ruby merge_asana_into_omnifocus.rb

<span class="light">Warning: This is just my script, it may or may not work for you. **Backup your OmniFocus before running it the first time.** And use at your own peril. *Inelegant, alpha-level, probably quite buggy, my first AppleScripts, you get the drift.*</span>

But if you do use it, let me know in the comments or via Twitter. And if you have any ideas for changes or enhancements, let me know.

*Follow the author as [@hiltmon](https://twitter.com/hiltmon) on Twitter.*
 
 
---
layout: post
title: "Merge Asana Projects into OmniFocus"
date: 2013-11-03 17:51
comments: true
categories: 
---

{% img right /images/asana_to_omnifocus.png 363 130 %}

**Note: Updated the script, see [Merge Asana Projects Into OmniFocus Updated](http://hiltmon.com/blog/2015/03/01/merge-asana-projects-into-omnifocus-updated/).**

I use [OmniFocus](https://itunes.apple.com/us/app/omnifocus/id402835630?mt=12&uo=4&at=10l894) to manage my personal tasks and activities, but my company uses [Asana](https://asana.com/) to manage Project tasks and activities amongst the team. I am so used to using OmniFocus that I often forget to check or update Asana, and thus miss tasks assigned to me or progress by the team.

Wouldn't it be nice if the projects and tasks in Asana also appeared in OmniFocus? And were updated when they changed in Asana?

So I wrote a script to import Asana Projects and Tasks, and then to update them as they change in Asana.

**Download**: [<del>Gist 9786291</del>Gist "merge_asana_into_omnifocus.rb"](https://gist.github.com/hiltmon/d1f79e95dd11252ce6ca) <span class="light">Read below on how to set it up and run it. Warning: Alpha!</span>

What the [script](https://gist.github.com/hiltmon/d1f79e95dd11252ce6ca) does is: 

1. Scans Asana for all projects and creates an OmniFocus project in the folder **Asana**. It also ignores archived projects in Asana as you do not need to see those.
2. Scans each project for tasks and creates an OmniFocus task for it. It also captures the notes and due date for the task. If the task is subsequently completed in Asana, it will complete the task in OmniFocus. If the task does not exist in OmniFocus and is already completed, it will not create it.
3. If you are *not* the assignee (the person the task is associated with), it creates a context under **People** for the assignee (so you can see who the task is for - and leaves the context blank for yourself). This is necessary as the Asana API returns all tasks for a project no matter the assignee.
4. If there are sub-tasks to the task, the script will create those as well (with notes, due dates, completion status and context). You can turn this off in the script if you do not use sub-tasks to speed up merges.
5. You can run the [script](https://gist.github.com/hiltmon/d1f79e95dd11252ce6ca) again and again. If a project or task exists, it will be updated *and overwritten* with the changes in Asana.

The [script](https://gist.github.com/hiltmon/d1f79e95dd11252ce6ca) **does not**:

1. *The script does not* sync data back to Asana. This is a one way *merge-in*. I have no way to track Asana id's and keep things in sync. **You still have to maintain and complete tasks in Asana**
2. The script screws up if the task or project name changes. It uses these names to match OmniFocus, not ID's. Since *most of the time* we never change the project or task name, this works.
3. *The script does not* track any tasks that are *not* part of a project. My needs were for the team tasks in projects to be visible to me in OmniFocus and I do not use the Asana Inbox for anything, its all in OmniFocus. <span class="light">If you have the skill, you may be able to use the Asana workspace call to get these too.</span>
4. The script also ignores all comments, history and attachments, that's what Asana is good for.
5. *The script does not* do your tasks for you.

### Prerequisites

Make sure you have the following set up in OmniFocus:

{% img left /images/asana_asana.png 212 103 %}

{% img right /images/asana_context.png 212 104 %}

* A Project Folder called **Asana** in Library.
* A context called **People** under all Contexts.

### Setup

Log into Asana and go into your account (It's at the bottom left just above the **Help** link).

Make a note of your Profile Name, you'll need it in the script.

{% img /images/asana_profile.png 543 222 %}

Click on **Apps** to get your API Key. Click on the **API Key...** link to see it. Note that down too.

{% img /images/asana_api_key.png 533 341 %}

Open the [script](https://gist.github.com/hiltmon/d1f79e95dd11252ce6ca) in a text editor and insert your API key and Profile Name at the top.

	...
	class MergeAsanaIntoOmnifocus
  
	  API_KEY = '<YOUR KEY HERE>'
	  ASIGNEE_NAME = '<YOUR PROFILE NAME HERE>'
	  SUBTASKS = true

	  def get_json_data(url_string)
	  ...

Download: [<del>Gist 9786291</del>Gist "merge_asana_into_omnifocus.rb"](https://gist.github.com/hiltmon/d1f79e95dd11252ce6ca)

### Running It

Make sure that the prerequisites are set up in OmniFocus and Asana.

Then just run it from the command line:

	$ ruby merge_asana_into_omnifocus.rb
	
It will display each project as it finds it, and each task as it searches for subtasks so you can see progress.

The script is not very quick. It has to run a bunch of AppleScripts to talk to OmniFocus, so please be patient.

To update with the latest data from Asana, just run it again.

### Tips

* Make sure you run the script before you archive Asana projects so that their tasks are marked as completed in OmniFocus first.
* I prefer to use short project names because they fit the sidebar in OmniFocus. You may want to clean up your Asana before running this the first time.
* Since Asana and OmniFocus treat subtasks differently, I have chosen to use the assignee from the task on sub-tasks unless they are overridden. OmniFocus ignores context on parent tasks.

<span class="light">Warning: This is just my script, it may or may not work for you. **Backup your OmniFocus before running it the first time.** And use at your own peril. *Inelegant, alpha-level, probably quite buggy, my first AppleScripts, you get the drift.*</span>

But if you do use it, let me know in the comments or via Twitter. And if you have any ideas for changes or enhancements, let me know.

Download: [<del>Gist 9786291</del>Gist "merge_asana_into_omnifocus.rb"](https://gist.github.com/hiltmon/d1f79e95dd11252ce6ca)

*Follow the author as [@hiltmon](http://twitter.com/hiltmon) on Twitter and [@hiltmon](http://alpha.app.net/hiltmon) on App.Net. Mute `#xpost` on one.*

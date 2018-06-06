---
layout: post
title: "Rebooting OmniFocus"
date: 2014-03-29 15:08:47 -0400
comments: true
categories: 
---

{% img right /images/omnifocus.png 256 256 %}

I've been using [OmniFocus](https://www.omnigroup.com/omnifocus) forever to record and track my personal and professional actionable to-dos and ideas. But over the past year, I have been using it less and less, getting less and less tracked and done, and it's all my fault.

You see, I started to experiment with what *could* be done with OmniFocus and messed up the whole concept of *actually getting things done*.

My primary experiment was to create scripts to automatically load actions in from my project files and to merge the company-wide [Asana](https://app.asana.com). The big idea was that I could save time and effort by automating task entry and assignment, and let the meat-bag (that's me) process and review these tasks. If I could spend less time *creating* tasks and more time *performing* tasks, I would be more productive.

What a disaster.

The automation dutifully created more tasks than I could handle. The Asana merge, which only imported projects and tasks assigned to me, created even more tasks. Before I knew it, my OmniFocus database was loaded full with too many tasks for me to get ahead of. And that was off-putting.

And these tasks were not *mine*. The imported tasks from Asana felt were created by *other* people, because they were. Sure, they needed to be done, and needed to be tracked in Asana. All good. But they did not feel like *my* tasks.

{% pullquote %}
And these tasks also created *more* work for me because the Asana projects and contexts did not match how I work and the task descriptions were confusing. {" It's a huge difference between how you write tasks for yourself and how others write tasks for you."} And then there are the tasks that are tagged in Asana as assigned to me but are really like the Carbon Copy (cc) in email, just for my information, yet they too came into OmniFocus as tasks for me to do. And that made me want to use OmniFocus less.
{% endpullquote %}

I no longer felt I *owned* my own task list.

Time for a reboot.

Here's what I did:

1. **Backed Up the Old Database**: I backed up the old database using **File / Back Up Database...** just in case I messed things up.
2. **Export the Old Database**: Since I wanted to see what was in the old database and decide which tasks to copy over, I needed it in another format. So I exported the old database using **File / Export...** and selected **Plain Text (TaskPaper)**. I then opened this file in [BBEdit](http://www.barebones.com/products/bbedit/).
3. **Nuke the Old Database**: I exited OmniFocus and deleted the **omnifocus.ofocus** file in **~/Library/Application Support/OmniFocus**.
4. **Restart and Reset Sync**: When I relaunched OmniFocus, it created a new database and wanted to download my old database from the OmniSync server. I hit **cancel** on that dialog and clicked **File / Replace Server Database...** to reset sync. Kudos to the Omni developer who created that dialog, the explanation on what do do if I wanted to reset was very clear.
5. **Re-created the Projects my way**: I recreated my personal and business folders, my personal and business single actions and my bills action that integrates with [Hazel](http://www.noodlesoft.com/hazel). I then re-created the projects in each folder the way I think about them.
6. **Selected and recreated tasks my way**: I then went through the massive [TaskPaper](http://www.hogbaysoftware.com/products/taskpaper) formatted file in BBEdit and either rewrote or pasted in *my* tasks *my* way. In this way, I got rid of the duplicates, the copies and the confusing ones, and only added back the ones I want to and need to do in *a way I will want to do them* in the projects they belong to.

It took a rainy Saturday morning to manually reboot my OmniFocus. But now I have clean and tidy, works-my-way projects, contexts and tasks in my OmniFocus database.

I *own* my own tasks again.

As for the tasks in Asana, well, I get an email whenever a task is assigned to me. And that I can process using OmniFocus's quick entry if the task is a real one. But this time, it will be mine.

I foresee a very productive week ahead.

Next task: Sign up for the [OmniFocus 2 Beta](http://www.omnigroup.com/test/omnifocus/).

*Follow the author as [@hiltmon](http://https://twitter.com/hiltmon) on Twitter and [@hiltmon](http://alpha.app.net/hiltmon) on App.Net. Mute `#xpost` on one.*

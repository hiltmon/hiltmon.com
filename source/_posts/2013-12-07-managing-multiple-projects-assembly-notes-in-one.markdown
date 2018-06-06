---
layout: post
title: "Managing Multiple Project's Assembly Notes in One"
date: 2013-12-07 13:50
comments: true
categories: 
---

The problem I have is that I regularly need to open a specific set of [Markdown](https://hiltmon.com/blog/2012/02/20/the-markdown-mindset/) documents scattered all over my file system while I work and have them available at my fingertips. But I need  a *different* set open when working at home and available the same way. The best solution I have found is to use [BBEdit](https://itunes.apple.com/us/app/bbedit/id404009241?mt=12&uo=4&at=10l894) projects to manage these document sets. Here's why and how to do it.

## The Scenario

I work across several projects during the day at work and across a different set of projects at night. I would like to have all their [Assembly Notes](https://hiltmon.com/blog/2013/01/03/assembly-notes/) and TODO documents together in one application for reference and update.

But each project I work on follows my preferred [Project Folder Layout](https://hiltmon.com/blog/2012/06/30/project-folder-layout/) in the file system which means these files are scattered all over the place.  Each project has an [Assembly Notes](https://hiltmon.com/blog/2013/01/03/assembly-notes/) document and a TODO document stored in its `documents` folder but I want to work with them in one place.

The pain point comes in when I switch projects and need to update the assembly notes or TODO for that project, then get back to another project. Finding, opening and closing these scattered files all day is not optimal.

Also, storing these files in a central location does not work for me as these are all for different clients and are stored in different repositories. I want the documentation to remain part of each project so its easy to zip, back up, copy, sync, commit and share.

## The Solution

Since all these files are plain text Markdown files and I usually have them open in BBEdit, I use BBEdit projects to manage each set that I need.  During the day I open the *work* project in BBEdit that contains references to all my *work* project assembly notes and TODO documents no matter where they are. At night, I open the *Noverse* BBEdit project which contains references to all current *Noverse* project assembly notes and TODOS.

{% img right /images/bbedit-projects.jpg 413 273 %}

And the best part is that BBEdit has a separate section in **File / Open Recent** for just these project files, so its very quick to switch sets.

To set this up, create a new Project File in BBEdit from the **File / New** menu. Then drag and drop the assembly notes files and TODO files into the project area at the top left of BBEdit from all the various project folders. Then do the same for the next set.

At the start of the work day, open the *work* BBEdit project and all your project assembly notes will be available in BBEdit at your fingertips. At the end of the day, close that project window and open the *evening* Project file and all *those* files will be now be available in the same manner.

In my case, BBEdit is always running, with one window containing the current set of assembly notes and the other being used as my hammer tool for file and data processing.

*Follow the author as [@hiltmon](http://https://twitter.com/hiltmon) on Twitter and [@hiltmon](http://alpha.app.net/hiltmon) on App.Net. Mute `#xpost` on one.*


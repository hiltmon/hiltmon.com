---
layout: post
title: "Mischief Managed: Archiving"
date: 2012-08-06 12:12
comments: true
categories: Mischief-Managed
---

***Mischief Managed** is a series of posts on tasks and technologies I use to maintain my computing environment. It’s part of what I do between projects. Try it out.*

When a project or engagement is completed, support is over, and you’re on to the next thing (or taking a break), it’s best to move these files and tasks out of your current folders and into archive folders.

Here are some of the things I do:

## Move to Old Projects

I move the entire project tree from my `~/Projects` folder to my `Old Projects` folder on the slow drive. It’s still on the laptop (I have a SSD and an HDD), so I can access it and restore it if necessary, but it’s no longer available in my current projects folder where I will see it every day. Less clutter.

I also update my [TextExpander](http://smilesoftware.com/TextExpander/) shortcut that takes me to the code of that project in case I need to open it quickly in an editor. For example, the `;cdxx` macro that was `cd /Users/Hiltmon/Projects/XX/code/XX/` macro becomes `cd /Volumes/Callisto/Old Projects/XX/code/XX/`.

## Archive OmniFocus

This is really a task that you should perform regularly, but I don’t seem to remember. In [OmniFocus](http://www.omnigroup.com/products/omnifocus/), click on **File** / **Move Old Data to Archive...**. You’ll be prompted for a date, and then OmniFocus will move all completed tasks before that date to an archive file. It puts that into a file in `~/Library/Application Support/OmniFocus` so make sure you always archive from the same computer, and include this folder in backups.

The main benefit of this is that it reduces OmniFocus sync time as all the old completed tasks from your projects are no longer there.

## Move old Mails

Clean up your inbox so all the email for the project is safely in its client folder, see my [Mischief Managed: Clean Inbox](http://hiltmon.com/blog/2012/08/06/mischief-managed-clean-inbox/) post.

## (OLD) Clean Up Documents

Since I moved to a standard [Project Folder Layout](http://hiltmon.com/blog/2012/06/30/project-folder-layout/), I no longer need to do this, but I’m documenting it just in case.

I used to have client files, art files, contracts and other documents relating to the project littering my `~/Documents` tree until I started using my standard [Project Folder Layout](http://hiltmon.com/blog/2012/06/30/project-folder-layout/). At the end of each project, I would have to go through all the folders in `~/Documents` and move the required documents to an `Old Documents` folder on the slow drive.

## Archive Notes

The only documents I keep outside the project folder these days are any generic client notes in [nvAlt](http://brettterpstra.com/project/nvalt/). But now that I use [VoodooPad](http://flyingmeat.com/voodoopad/) for all key project info (see [Project Specific Data](http://hiltmon.com/blog/2012/05/27/project-specific-data/)), that too is changing.

I use a mixture of [OpenMeta](http://code.google.com/p/openmeta/) tags and [Hazel](http://www.noodlesoft.com/hazel.php) rules to tag old notes as `archive` and Hazel moves them out of the Notational Velocity folder and into an archive folder.  I then drag and drop them into the Project Folder in `Old Projects`.
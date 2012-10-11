---
layout: post
title: "Project Folder Layout"
date: 2012-06-30 12:32
comments: true
categories: [Productivity]
---

We all work on multiple projects. And we're creating new ones all the time, whether for new engagements, new personal projects or spikes. I personally like to have all my project files properly organized, every component of the project has its place, so I have been using my own standard project folder layout for years.

Until now. The old one was no longer working.

So I rearranged my standard project folder layout. *This time* I automated the creation of these folders. *This time* I made a single tree. *This time* I think I got it right.

In this post I present the new **Hiltmon Standard Project Folder Structure** &trade;, and describe what goes where and why. [Download the folder creation script and VoodooPad document here](http://cl.ly/2b0N1H27433P0T1Y1u3C).

## The structure

Each project has a project [VoodooPad](http://flyingmeat.com/voodoopad/) document in the root of it's folder. This document contains all the key project information that's usually spread all over the place such as:

* *Client contact* information
* *User accounts* that we need to login to the project in production
* *System Services* to document any encryption key files, config files and other stuff needed to work on the project
* *Names and IPs* for the addresses, logins and passwords to access the project servers, databases, networks, routers, VPN's, etc.

I always have this file open when working on a project, and it's great to come back to a project later and have all this information at your fingertips.

{% img right /images/project-layout.png 395 685 %}

And then there are the project folders themselves:

* **archive**: As I iterate on a project, or create new versions of a product, I move old code, designs, artwork in here. When I work on other people's products, I keep a copy of the original in here in case I mess things up.
* **artwork**: All project artwork goes in here, especially Photoshop and Illustrator master files. The idea is that anyone should be able to recreate all project image assets using the files in here. I often subdivide this folder with subfolders for the **product** master files, the **media** master files and **other** related master files.
* **code**: All source code goes in here. Since most projects contain more than one deliverable, there is a subfolder for each in here. I also create [TextExpander](http://smilesoftware.com/TextExpander/) snippets to help me `cd` to each subfolder quickly, e.g. the snippet `;cdhi` expands to `cd /Users/Hiltmon/Projects/HiltmonDotCom/code/hiltmon.com/` which is where this site's Octopress source resides.
* **data**: A lot of projects involve client supplied data, which is saved here. I also save project system logs and data backups here so I can recreate issues or configure my development environment to match production.
* **design**: All design work happens in this folder. This almost always contains a **research** subfolder where all technical and competitive research goes. I also have a **pre-sales** subfolder for any design notes created as part of the project planning phase. Then I save all designs, wireframes and design notes in versioned subfolders here so I have a record of all design decisions.
* **documents**: This is the "catch-all" folder for documents that have no regular place in the structure. I mostly use it for the creation of knowledge-base documents, news articles, and as a place to store any other files related to the project.
* **management**: Here we have copies of the contract, the statements of work, estimates, scheduling and planning documents, letters and correspondence, project reports, invoices and all other project management files.
* **marketing**: I really should call this the "success", "feel-good" or "shipped" folder. In here I save any PR statements we send out (hence marketing folder) but also archives of any web articles on the project, any tweet mentions, any ranking screenshots, basically anything that is publicly said about the project. If we ever need a feel good moment, or a reality check, this folder has it all.
* **media**: Here we store all **presentations**, **brochures**, **screencasts**, **videos** and other media created to market or support the product. I often find it useful to create screencasts while making the project and sending them to clients so they can see the product as it grows.
* **notes**: I create a weekly markdown file where I log all the work I did on the project. It's an old habit but a goodie. All meeting notes, call notes, procedure notes and other ramblings are stored in markdown files in this folder. I always have BBEdit running with the latest assembly note open to jot down all that I do.
* **partners**: Many of our projects involve third parties, whether they be software vendors, designers or wordsmiths. Save all their deliverables and documents here so we have the originals. We can then create the project assets and masters from these files.
* **support**: If we make it, we have to support it. All support notes (that eventually become knowledge-base documents), bug reports, and templates go here.
* **tools**: Some projects rely on third party libraries, open source tools, or other products that may be needed to make it work. They go here.

## The location

My **Projects** folder is in the root of my home folder (in my case `/Users/Hiltmon`). I have added it to the sidebar in Finder so I can navigate to it quickly from everywhere. It contains all *current* projects. There is an **Old Projects** folder inside my **Documents** folder where I drag old or completed projects.

*Aside:* In my previous folder layout, I used to only keep only code in the **Projects** folder (like most people do), and used to run a separate **Products** tree for each engagement containing all the *project* documentation and a separate **Clients** tree for *client* information. This worked for a while, but the client files would get mixed up between projects and I found myself navigating between **Projects** and **Products** a lot while working. So I consolidated all three into one, one tree per project, easy.

## The tools

*Note: I store all my personal scripts and utilities in `~/Scripts` and I'm lazy in that I generally hardcode this path.*

[Download a ZIP file with the script and blank VoodooPad document](http://cl.ly/2b0N1H27433P0T1Y1u3C).

The `new_project.sh` script creates the folder tree and and VoodooPad document for a new project. The script uses the first parameter as the project name, e.g. 

```
$ ~/Scripts/new_project NewProjectName
```

*Note that I always use single-word project names* because I hate spaces in paths, and because I am graybeard enough to remember tools that used to fail when there were spaces in paths. The script will *not* work for projects names with spaces in them.

``` sh new_project.sh
#! /bin/bash

# new_project.sh
# Hilton Lipschitz (http://www.hiltmon.com)
# Use and modify freely, attribution appreciated
#
# Script to create a new project tree with all the folders I need.
#
# Requirements:
# - Set the PROJECT_ROOT to your projects folder
# - Set the BLANK_VPDOC_PATH to your blank VoodooPad file
#
# Usage: new_project.sh <ProjectName>

# Set these first
PROJECT_ROOT="$HOME/Projects"
BLANK_VPDOC_PATH="$HOME/Scripts/BlankProject.vpdoc"

PROJECT_NAME=$1
PROJECT_PATH="$PROJECT_ROOT/$PROJECT_NAME"

echo "Creating $PROJECT_PATH..."

if [ -e $PROJECT_PATH ]; then
    echo "$PROJECT_NAME already exists!"
    exit
fi

mkdir $PROJECT_PATH
for folder in 'archive' 'artwork' 'code' 'data' 'design' 'documents' 'management' 'notes' 'media' 'marketing' 'support' 'partners' 'tools'; do
    mkdir "$PROJECT_PATH/$folder"
done

cp -R $BLANK_VPDOC_PATH "$PROJECT_PATH/$PROJECT_NAME.vpdoc"

echo "Tree for $PROJECT_NAME created at $PROJECT_PATH"

```

## The result

So, right now I have 9 active projects in my **Projects** folder. All of them are using this folder structure. It's new, and it seems to be working well.

How do you structure your project folders, product files and client files? I'd love to know, and improve on this structure. Send me a link in the discussion below or catch me on twitter [@hiltmon](https://twitter.com/hiltmon).

 

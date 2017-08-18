---
layout: post
title: "A Yosemite Markdown Spotlight importer"
date: 2015-11-17 12:26:13 -0500
comments: true
categories: Markdown
---

All my text and writing is in [Markdown](https://hiltmon.com/blog/categories/markdown/) formatted files and I would like to search them using Spotlight. The editors I use do not have an importer (they have Quicklook only), so this is not available directly.

Changing the `RichText` Spotlight importer trick worked in previous versions of OS X (see how in [A Simple Markdown Spotlight Importer](https://hiltmon.com/blog/2015/06/27/a-simple-markdown-spotlight-importer/)), but since System Integrity Protection in OS X El Capitan, this no longer works.

Never fear, there is another way.

The great [Brett Terpstra](http://brettterpstra.com) to the rescue, again! Read about it at [Fixing Spotlight indexing of Markdown content](http://brettterpstra.com/2011/10/18/fixing-spotlight-indexing-of-markdown-content/) on his amazing site.

What I did was the following:

* Downloaded this Zip file from [his site](http://cdn3.brettterpstra.com/downloads/Markdown.mdimporter.zip) and uncompressed it
* Moved the `Markdown.mdimporter` file to `~/Library/Spotlight`. I had to create the folder under my User's Library folder. To find this folder in Finder, hold the Option key when pressing the Go menu to see the Library folder option.
* Started a `terminal` shell

In the command prompt, I executed the following to activate the importer:

	mdimport -r ~/Library/Spotlight/Markdown.mdimporter

And then, *when nothing seemed to have happened*, I recreated the entire Spotlight index on my computer.

There are two ways to do this.

The GUI way is to open **System Preferences**, select **Spotlight** and the **Privacy** tab. Drag and drop your `Macintosh HD` onto the big open space. Wait 20 seconds or so, then click the `minus` sign to delete it. OS X will start to recreate your Spotlight index.

Or use the following command:

	sudo mdutil -E /
	
To see if this is working, run

	mdimport -L
	 
I get

	2015-11-17 12:40:40.400 mdimport[53046:588670] Paths: id(501) (
    	"/Users/Hiltmon/Library/Spotlight/Markdown.mdimporter",
    	"/Library/Spotlight/iBooksAuthor.mdimporter",
    	"/Library/Spotlight/iWork.mdimporter",
    	...

After a long while, all my Markdown files were once again searchable in Spotlight. Thanks Brett!

*Follow the author as [@hiltmon](http://twitter.com/hiltmon) on Twitter.*

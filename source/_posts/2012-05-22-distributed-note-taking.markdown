---
layout: post
title: "Distributed Note Taking"
date: 2012-05-22 09:39
comments: true
categories: [Productivity]
---

I have switched over to and finally locked in on a new distributed note taking process, using [Elements](http://www.secondgearsoftware.com/elements/) on the iPad, [Dropbox](http://www.dropbox.com) synching, [TextExpander](http://smilesoftware.com/TextExpander/) file naming and [nvAlt](http://brettterpstra.com/project/nvalt/) on the Mac. Here's how I got to this point, and how it works.

## Going electronic, the old way

Since I switched over to the iPad from a paper notepad about two years ago, I used [Penultimate](http://www.cocoabox.com/penultimate) and a stylus to scribble notes. I thought this would be a great process. I can scribble quite quickly, I can draw pictures (I have a visual mind) and I can save the PDF's of these notes and refer back to them. Something like this:

{% img /images/penultimate-notes.png 640 419 %}

But it was not working for me. The notes are often quite illegible, they are certainly unsearchable, and I had to manually move them over to the Mac. Truly, a better way was needed.

## The requirements

Since I am a programmer, I started with requirements. My new note taking workflow needed to have the following characteristics:

* It must be quick to launch and start taking notes
* The notes must be searchable
* The notes must sync seamlessly across all devices, start on one, finish on another
* I'd love to use markdown
* It's got to be simple

Things I do *not* want in my notes process:

* Lock into a single product or infrastructure, so [Evernote](http://evernote.com/) and [SimpleNote](http://simplenoteapp.com/) are out. (Update: with the recent [Simperium](https://simperium.com/) release, SimpleNote may work for you).
* Notes be stored in a proprietary format that may not be future-proof.

## The setup

So, over the past few months, I have been tuning in and then stabilizing on the following setup.

First, I reconfigured nvAlt to save everything as plain text files using the `.markdown` extension in a 'Notational Data' folder which happens to be in the root of my Dropbox. Result: All notes are automatically synced using Dropbox to all devices. It just works.

{% img /images/nvalt-storage.png 640 512 %}

I then added to the series of snippets in TextExander to help me name the different kinds of files and notes that I take (see [My Blog Writing Workflow](https://hiltmon.com/blog/2012/03/15/my-blog-writing-workflow/)). I have TextExpander installed on all devices too, and set to sync via Dropbox as well, so these are also available everywhere.

{% img /images/textexpander-notex.png 640 429 %}

On the iPad, I have installed both TextExpander Touch and Elements. Elements has been configured to use the same 'Notational Data' folder on Dropbox and the same `markdown` file extension. I also have [Byword](http://bywordapp.com/) and [iAWriter](http://www.iawriter.com/) on the iPad with the same folder settings, but it seems I go to Elements the most often.

## The flow

*To **start** a note on the **Mac***, I switch to nvAlt and type `;notex`. TextExpander kicks in and expands it to `Notex - | - 2012-05-22`, leaving the cursor where the `|` character is. I generally type in the client name, followed by a hyphen, followed by a subject. For example, a meeting on Kifu, I would start with `;meetx` (a meeting note) which expands to `Meetingx - | - 2012-05-22` and I change it to `Meetingx - Kifu - Board Meeting - 2012-05-22`. Press tab, and I can start typing the notes.

*To **start** taking a note on the **iPad***, I launch Elements, hit the add button which leaves the cursor in the file name field, type in the same shortcut `;notex` which gets expanded, update the file name, and tap the body to start typing.

*To **find** a note on the **Mac***, I switch to nvAlt and just start typing in words. Or I use Spotlight. Both work to quickly help me find notes.

*To **find** a note on the **iPad***, I launch Elements, swipe down to reveal the search bar and type what I am looking for.

With this flow, and some Dropbox magic, all my notes are available on the iPad in Elements and on the Mac in nvAlt, and any new notes automatically appear automatically on both. My typing speed on the iPad is fast enough to take notes, and since they are just plain old markdown files, I can search and find them anytime.

What do you use for notes?

---
layout: post
title: "Text Notes - Going Electronic"
date: 2012-04-15 13:45
comments: true
categories: [Productivity]
---

One of the big changes I made in the last year is how I take and store text notes. By text notes, I mean meeting notes, book lists, blog ideas, thoughts, even project estimates. I've finally gone paperless.

tl;dr (too long; didn't read): I write notes in [Markdown](http://hiltmon.com/blog/2012/02/20/the-markdown-mindset/), in files named using [TextExpander](http://smilesoftware.com/TextExpander/) macros, using [nvALT](http://brettterpstra.com/project/nvalt/) with [Dropbox](https://www.dropbox.com/) sync on the Mac and [Elements](http://www.secondgearsoftware.com/elements/) or [Byword](http://bywordapp.com/) on iOS sharing the same Dropbox folder. I still keep project development logs in separate Markdown files within each product's folder because I format and deliver them. I don't use [Evernote](http://www.evernote.com/) because I cannot stand it.

<!--more-->

## Notes Before

In the good old days, I used a notepad, one of those large, cheap, usually wire-bound books with lined paper. Each day, I'd open to a new page, put the date in the top right, and leave the book opened to that page to the right of my computer with a pencil lying crosswise atop it. Whenever I was not programming, I'd rest my hand on the pencil in case a note needed to be written.

I'd fill books and books of notes. Reminders, phone numbers, meeting notes, design ideas, lots of diagrams because I think visually, anything that needed to be noted got added to the book.  Once a week, I'd go back through the scribbles and cross out all the completed tasks, called numbers and old notes; and transcribe a new weekly todo on a new page. After that, I'd rarely go back.

The system worked, but rather badly. Different kinds of notes were intermixed, my handwriting varied from awful to chicken scratch, and finding old notes was impossible, especially when changing to a new notebook. But nothing beat a pencil and paper for a quick note.

Until I found post-it notes. With these, I had a place for 'throw-away notes'. The jotted down phone number, the quick reminder, the diagram to explain my point. I'd use them and lose them. The book remained for longer term notes, or, just as likely, a place to stick the post-it.

But I needed a better way.

## The Search

Being a tech, I set some goals

* Must be electronic
* Must be searchable
* Must be available on the Mac and iPad (iPhone a bonus, but I'm rarely away from my iPad; and I only want Web access as the last-resort-house-burned-down option)
* Must be Markdown based so I can integrate it into my Markdown workflow
* Must be maintenance free (I don't want to manually sync, copy or send files, it should just work)

## The Candidates

[Yojimbo](http://www.barebones.com/products/yojimbo/) is a product I had, love and was using to store all my core documents, like passport scans, bank details, statements and other stuff. When I first got it, I did try to use it for notes, and loved the search. But the early versions did not have a mobile version, and even now, the sync requires both desktop and iOS to be running. Several really famous bloggers use it and love it. It still works for me as a scanned document store, but not for text notes.

[Evernote](http://www.evernote.com/) is the big elephant in the room, and everybody I know has an account. So I tried it. The client is OK, it was available on all my platforms and on the web, and it synched (no maintenance). I really tried to love it. But I couldn't. I don't know if it was the busyness of the interface, the limits of the free version, or the ads, I just found it cumbersome, and the more I tried to like and use it, the more I hated it. I just felt that *my* notes were no longer *mine* in Evernote. So I cancelled my account. And a few months later, when the new GUI came out, I created a new account to try again. And I still could not like it. Too busy, too much. For text notes.

[SimpleNote](http://simplenoteapp.com/) was my next candidate, and I thought this would be the one. Text notes, searchable using their client or my Spotlight, no maintenance, and on all my platforms. Maybe I was just one of the unlucky ones, but after a few weeks of working it started to go flaky. The client crashed, and the synching became unreliable. I now know that they were just having teething problems, and it's all good, but it bit me.

Since Dropbox sync was, and still is, bulletproof reliable, I decided to try going back to basics, using plain Markdown files in Dropbox as my next candidate. I'd write my note using [BBEdit](http://www.barebones.com/products/bbedit/index.html?utm_source=thedeck&utm_medium=banner&utm_campaign=bbedit) (because it's always running) in Markdown and save it to Dropbox, or use one of the Dropbox editors on iOS to do the same. I found myself fighting to name files and search was hit or miss, usually miss.

## My Solution

All the above attempts had led to add a few new tools in my arsenal. The most important of which is that I had created TextExpander macros to name the different kinds of note files. I had also added [Hazel](http://www.noodlesoft.com/hazel.php) to automatically manage and maintain my files, [Keyboard Maestro](http://www.keyboardmaestro.com/main/) to help automate tasks, and my trust in DropBox knows no bounds. But I needed a better search than Spotlight. My ideal note-taking tool should actually integrate search and note creation, and be Markdown aware.

And that led me to find [Notational Velocity](http://notational.net/). Search and note creation in the same action, Markdown aware, and happy to save to Dropbox where all my iOS editors can get to it. I just felt it was missing stuff, I just could not get to liking it. Until I found the [nvALT](http://brettterpstra.com/project/nvalt/) fork, all the cool of NV with all the missing stuff.

So here is how I do notes now.

nvALT is always running on the Mac, in its own space. Whenever I break or the phone rings, I switch to that space and leave it running. Creating a new note is as easy as `⌘L` and type in the abbreviation I need - `;meetx`, `;notex`, `;todox`, `;blogx`, etc. TextExpander expands these to file names with dates (e.g. `;meetx` becomes `Meetingx - | - 2012-04-15`) and leaves the cursor where I can type in a project code, person name and title. Press `enter`and I am in the body of the note, ready to write in Markdown. nvALT handles the saving as Markdown files, Dropbox takes care of the synching. Just switch in, make a note, switch out.

When not near the Mac, I have both Elements and Byword on the iPad set up to use the same Dropbox folder as nvALT. Tap the app, type in the same TextExpander abbreviation to create a new note file, and off I go, banging away in Markdown. When I come back to the Mac, the new note is just there.

Once every few weeks, I go through the notes in nvALT, and tag the old ones with an `archive` tag. Hazel picks up these tagged notes and moves them to an archive folder on my Mac, taking them out of Dropbox.

For text notes, this flow just works. For me. My text notes are easy to find, easy to create and are always accessible. Old notes are archived, out of the way, but easy to get back. Just what I need.

---

I did not invent this process. Instead, as with all good artists, I stole ideas from others, and put them together in a way that works for me. Here are some of the references that I looked at that helped me setup my text notes process:

* [Using Notational Velocity](http://www.jasonheppler.org/using-notational-velocity.html) by Jason Heppler, which led me to
* [MPU 046: Workflows with Merlin Mann II](http://macpowerusers.com/2011/03/mpu-046-workflows-with-merlin-mann-ii/)(Audio podcast link) where I gained the file naming idea.
* [NVAlt Note Archiving with Hazel](http://www.macdrifter.com/2012/02/nvalt-note-archiving-with-hazel/) by MacDrifter to keep the notes pile clean

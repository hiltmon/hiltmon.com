---
layout: post
title: "My Blog Writing Workflow"
date: 2012-03-15 14:52
comments: true
categories: Markdown
---

With the release of [Byword for iOS](http://itunes.apple.com/us/app/byword/id482063361?mt=8) (iTunes app store link), my blog writing workflow has come full circle.

All posts start as ideas and notes jotted down in [nvAlt](http://brettterpstra.com/project/nvalt/), Brett Terpstra's fork of [Notational Velocity](http://notational.net/). I like this product because the *search* and *use* of notes is fully integrated, and it supports markdown.  I have set it up so that all notes are stored as markdown files in a [Dropbox](http://www.dropbox.com) folder and [Byword](http://bywordapp.com/) has been set up as the external editor.

This has allowed me to have full access to my notes on the iPad using [Elements](http://www.secondgearsoftware.com/elements/), by pointing it to the same Dropbox folder as nvAlt.

Following a similar process to [Merlin Mann](http://macpowerusers.com/2011/03/mpu-046-workflows-with-merlin-mann-ii/) (podcast link), I name all notes (and therefore their files) using a common prefix (BlogIdeax, Notex, Linksx), a title and a date. I use [TextExpander](http://smilesoftware.com/TextExpander/) expansions on both the Mac and the iPad to create these common pattern note file names.

The main benefit of this flow is that I can be on the Mac or iPad anywhere, anytime, and either capture a new idea, or work on fleshing out a topic in progress, Mac or iPad. Dropbox takes care of keeping it all in sync.

When the idea is fleshed out, or I just have the time, I write the post using [Byword](http://bywordapp.com/) on the Mac. Since this blog is an [Octopress](http://octopress.org/) blog, all I need to do is run a rake command to kick off the process:

```
rake new_post["My Blog Writing Workflow"]
```

My *modified* rake script creates the post markdown file, records the new post in [DayOne](http://dayoneapp.com/) and launches it in Byword for writing.  I then paste in the markdown from nvAlt and off I go.

The release of Byword for iOS means that I can move from Elements to Byword on the iPad in my flow (I have already done so). The feel of Byword on the iPad is sufficiently similar to that on the Mac, the new M+ C font looks great, and I actually like how the chrome goes away while writing.

I agree with Frederico Viticci in his [Byword for iOS Review](http://www.macstories.net/reviews/byword-for-ios-review/):

{% blockquote %}
Byword for iOS is a fine app. In fact, if you are looking for a Markdown editor with exporting options that has native iCloud and Dropbox support across Mac and iOS, this may be your best choice right now.
{% endblockquote %}

So thank you, dear [MetaClassy](http://metaclassy.com/) team for Byword.

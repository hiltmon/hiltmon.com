---
layout: post
title: "A simple Markdown Spotlight importer"
date: 2015-06-27 14:33:43 -0400
comments: true
categories: Markdown
---

**Note: This is for Yosemite or before, for El Capitan or later, see [A Yosemite Markdown Spotlight Importer](https://hiltmon.com/blog/2015/11/17/a-yosemite-markdown-spotlight-importer/).**

I noticed recently that Spotlight on Yosemite was no longer indexing my [Markdown](https://hiltmon.com/blog/categories/markdown/) files. Since all my notes are in Markdown format, and Spotlight is how I find my notes, this was a big problem. Reinstalling my current set of Markdown editors did not help.

This did. *Huge thanks to Gereon Sommer for the idea in [Mac OS X Spotlight Enhancement](https://gist.github.com/gereon/3150445).*

The idea is to use a built-in importer, in this case RichText, to do all the work for you. <span class="light">Note that this will probably need to be repeated on each Operating System install or upgrade.</span>

Edit `/System/Library/Spotlight/RichText.mdimporter/Contents/Info.plist` and add `<string>net.daringfireball.markdown</string>` under `LSItemContentTypes`:

	...
    <key>LSItemContentTypes</key>
    <array>
        <string>public.rtf</string>
        <string>public.html</string>
        <string>public.xml</string>
        <string>public.plain-text</string>
        <string>com.apple.traditional-mac-plain-text</string>
        <string>com.apple.rtfd</string>
        <string>com.apple.webarchive</string>
        <string>org.oasis-open.opendocument.text</string>
        <string>org.openxmlformats.wordprocessingml.document</string>
    	<string>net.daringfireball.markdown</string>
    </array>
	...		

<span class="light">You will need an admin password to save the changes.</span>

Restart the Rich Text importer

	mdimport -r /System/Library/Spotlight/RichText.mdimporter
	
And force a Spotlight re-index

	sudo mdutil -E /
	
To test this I created a new Markdown file in [BBEdit](http://www.barebones.com/products/bbedit/) and added the word `wagga` to it. After a few minutes of re-indexing, Spotlight found this file in a `wagga` search.

Good to go.

*Follow the author as [@hiltmon](http://twitter.com/hiltmon) on Twitter.*


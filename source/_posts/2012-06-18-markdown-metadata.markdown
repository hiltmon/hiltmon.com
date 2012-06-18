---
layout: post
title: "Markdown Metadata"
date: 2012-06-18 13:31
comments: true
categories: 
---

As you all know, I write everything in [Markdown](http://daringfireball.net/projects/markdown/), see my [The Markdown Mindset](http://hiltmon.com/blog/2012/02/20/the-markdown-mindset/). It would be nice, though, to also save metadata - information *about* the document - in the document, to make it searchable, but not to have it appear in the final output.

Turns out, [MultiMarkdown](https://github.com/fletcher/MultiMarkdown) (and other new Markdown processors) do support this. It's easy.

Simply add the metadata to the top of a markdown file as follows:

{% codeblock My Document Metadata lang:text %}
Title:       |  
Subtitle:    |  
Project:     |  
Author:      Hilton Lipschitz  
Affiliation: Noverse LLC  
Web:         http://www.noverse.com  
Date:        June 18, 2012  

Your first paragraph starts here
{% endcodeblock %}

The metadata is just a set of key-value pairs, where the key is before the `:` and the value after. The keys can be anything you want them to be, although Fletcher Penney, creator of MultiMarkdown, has recommended some standard ones [here](https://github.com/fletcher/MultiMarkdown/wiki/MultiMarkdown-Syntax-Guide). From what I can tell, adding your own makes no difference. So I do.

Also:

* It is recommended to end each line of the metadata with two spaces before the newline, so that older Markdown processors do not turn the metadata into a single line.
* The metadata block ends with the first blank line.
* You can have more than one value for a key on a new line, e.g. in my Call Note metadata header:

{% codeblock My Call Metadata lang:text %}
Called:         Donald  
In Conference:  Huey
                Duey
                Louis  
Project:        Fake Disney App
Author:         Hilton Lipschitz  
Affiliation:    Noverse LLC  
Web:            http://www.noverse.com  
Date:           June 11, 2012 16:48

Call notes start here
{% endcodeblock %}

A search for `called donald huey` will find this document easily, even if Huey was quiet for the whole call and does not appear in the notes. Yet if I format this document for HTML or PDF using [Marked](http://markedapp.com), the metadata disappears. Just the way I want it.

{% img /images/marked-no-metadata.png 579 276 %}

I use this so much, I have [TextExpander](http://smilesoftware.com/TextExpander/) snippets that generate metadata block, fill in the dates for me, and place the cursor at the title line. Just **New Document**, type `;mmt` (for MultiMarkdown Title) or `;mmc` (for MultiMarkdown Call) and I have a new markdown document with the metadata block all set up and ready to go.  

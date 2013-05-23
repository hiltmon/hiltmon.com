---
layout: post
title: "Letterhead - Markdown Style"
date: 2013-05-23 8:47
comments: true
categories: [ Markdown ]
---

So I get this request yesterday to send a document on [letterhead][letterhead]. You all may remember letterheads from back in the day when companies had professional printers print their fancy logos on fancy paper that you then ran through the "good" laser printer that then went into matching fancy envelopes and someone stuck stamps on and mailed them.

{% img /images/letterhead.jpg 500 153 %}

I thought that letterheads went the way of the dodo about the same time [fax machines][fax] and [US Mail][usps] both died out. *I was wrong*. It turns out, sometimes to make something "official" <span class="light">(whatever the heck that means)</span> you need it on letterhead. And since its 2013, a PDF version is acceptable.

Now I could have just dragged a logo into a [Pages][pages] document, added the letterhead text, written the document, manually formatted it, PDF'd it and emailed it. But since I am probably going to do more of these, I decided to integrate letterheads into my regular [Markdown][markdown] process.

For this to work, I needed a markdown file for the document, a logo image and a stylesheet. I already have a logo and a CSS stylesheet for rendering Markdown in [Marked][marked], which I use to generate business documentation from Markdown source in my preferred business style for all my client engagements. Look and feel, covered.

So the only difference between a letterhead version of a document and a regular document is the logo, a  silly header and a silly footer.

No problem, I created these with Markdown using a smidgen of HTML code and plonked them at the top and bottom of my document. I then saved them as [TextExpander][textexpander] snippets for when I need them again.

Preview in [Marked][marked]. Print to PDF. Sent. Easy as Pie.

The letterhead document source in Markdown looks like this. Note that it contains my standard [Markdown Metadata][metadata] headers as well.

{% codeblock lang:text %}
Title:          Sample Letterhead Document  
Subtitle:         
Project:        hiltmon.com   
Author:         Hilton Lipschitz  
Affiliation:    Noverse LLC  
Web:            http://www.noverse.com  
Date:           May 22, 2013  

![](noverse-logo-160-40.png)  
**Noverse LLC**  <span class="light">A New York Company</span>

# Sample Letterhead Document22 May 2013  **Client Company Name**  Client Street Address  New York NY 10019  ## RE: You need a letterhead?

Yadda yadda yadda.

More yadda yadda yadda.

<br/>
<br/>
<br/>
<br/>

**Hilton Lipschitz**  Noverse LLC
<span class="light"> **&middot;** +1 (917) 555-1234 **&middot;** www.noverse.com **&middot;** contact@noverse.com **&middot;** @noversellc</span>  
<span class="light">--- My Office Street, City, State, Zip ---</span>
{% endcodeblock %}

Notes on the markdown source:

* There are two spaces after each line in the address and in the name block at the bottom. That way Markdown places them on different lines without creating paragraph gaps.
* The `<br/>` lines are needed to create space for a signature which you used to use an instrument called a pen to scrawl your name in that space. For PDF letterheads, you can upload a signature image. But in this case, the recipient did not need the signature. "Official" but unsigned was weirdly fine too.
* I like putting a subject at the top of things, such as in this case `Sample Letterhead Document`. In the 19th century, you used to put the title where the `RE: You need a letterhead?` is.

And the result, an "official" looking document while remaining in the [Markdown Mindset][mindset]. Sweet!

{% img /images/markdown-letterhead.png 588 470 %}

*Follow the author as [@hiltmon](http://twitter.com/hiltmon) on Twitter and [@hiltmon](http://alpha.app.net/hiltmon) on App.Net. Mute `#xpost` on one.*

[letterhead]: http://en.wikipedia.org/wiki/Letterhead
[fax]: http://en.wikipedia.org/wiki/Fax
[usps]: http://en.wikipedia.org/wiki/United_States_Postal_Service
[pages]: http://click.linksynergy.com/fs-bin/stat?id=V41G*FiMqjc&offerid=146261&type=3&subid=0&tmpid=1826&RD_PARM1=https%253A%252F%252Fitunes.apple.com%252Fus%252Fapp%252Fpages%252Fid409201541%253Fmt%253D12%2526uo%253D4%2526partnerId%253D30
[markdown]: http://daringfireball.net/projects/markdown/
[marked]: http://click.linksynergy.com/fs-bin/stat?id=V41G*FiMqjc&offerid=146261&type=3&subid=0&tmpid=1826&RD_PARM1=https%253A%252F%252Fitunes.apple.com%252Fus%252Fapp%252Fmarked%252Fid448925439%253Fmt%253D12%2526uo%253D4%2526partnerId%253D30
[textexpander]: http://click.linksynergy.com/fs-bin/stat?id=V41G*FiMqjc&offerid=146261&type=3&subid=0&tmpid=1826&RD_PARM1=https%253A%252F%252Fitunes.apple.com%252Fus%252Fapp%252Ftextexpander-for-mac%252Fid405274824%253Fmt%253D12%2526uo%253D4%2526partnerId%253D30
[metadata]: http://hiltmon.com/blog/2012/06/18/markdown-metadata/
[mindset]: http://hiltmon.com/blog/2012/02/20/the-markdown-mindset/

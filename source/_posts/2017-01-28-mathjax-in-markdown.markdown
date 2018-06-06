---
layout: post
title: "MathJax in Markdown"
date: 2017-01-28 14:39:08 -0500
comments: true
categories: 
---

Adding mathematical formulae to HTML pages is easy these days using [MathJax](https://www.mathjax.org). But I create all my documents in [Markdown](https://hiltmon.com/blog/categories/markdown/) format on my Mac. This post shows how to add mathematical formulae to your Markdown documents on the Mac and have them preview and export to PDF correctly.

### MathJax in Markdown

Adding mathematical formulae to a markdown document simply requires you to use the MathJax delimiters to start and end each formula as follows:

- For centered formulae, use `\\[` and `\\]`.
- For inline formulae, use `\\(` and `\\)`.

For example, the formula:

    \\[ x = {-b \pm \sqrt{b^2-4ac} \over 2a} \\]

Renders like this from markdown:

<div>$$ x = {-b \pm \sqrt{b^2-4ac} \over 2a} $$</div>

Or we can go inline where the code `\\( ax^2 + \sqrt{bx} + c = 0 \\)` renders as <span>\\(ax\^2 + \sqrt{bx} + c = 0 \\)</span>.

### Preview: iA Writer, Byword, Ulysses

Most Markdown Editors have a Preview function, but do not include MathJax by default. To add MathJax rendering in [iA Writer](https://ia.net/writer), [Byword](https://www.bywordapp.com), [Ulysses](https://ulyssesapp.com) and most others, you need to create a custom template to render the document (I assume you have done this already - see [Letterhead - Markdown Style]https://hiltmon.com/blog/2013/05/23/letterhead-markdown-style/) for an example).

For iA Writer, for example, go to **Preferences**, select the **Templates** tab and click the plus below **Custom Templates**, and choose **Open Documentation** to learn how to create your own template. Or copy an existing one and rename it.

In the main html file, called `document.html` in the iA template, add the MathJax javascript header line:

    <script type="text/javascript" src="http://cdn.mathjax.org/mathjax/latest/MathJax.js?config=TeX-AMS-MML_HTMLorMML"></script>

My template file is very simple:

    <!doctype html>
    <html>
    <head>
    	<meta charset="UTF-8">
        <link rel="stylesheet" media="all" href="normalize.css">
        <link rel="stylesheet" media="all" href="core.css">
    	<link rel="stylesheet" media="all" href="style.css">
    	<script type="text/javascript" src="http://cdn.mathjax.org/mathjax/latest/MathJax.js?config=TeX-AMS-MML_HTMLorMML"></script>
    </head>
    <body data-document>&nbsp;</body>
    </html>

Next time iA Writer, Byword or Ulysses loads its preview pane and renders the page, the javascript will run and render the MathJax as mathematical formulae. For example, in iA Writer:

{% img /images/mathjax-1.jpeg 640 379 %}

{% img right /images/mathjax-2.jpeg 340 123 %}

**Note**: Occasionally the preview will fail to render the MathJax, either because the MathJax is invalid or the refresh fails to reload the Javascript. If you see something like the image on the right, just right-click on the preview-pane and click `Reload`. That forces the preview pane to reload both the rendering template and the page.

{% img right /images/mathjax-3.jpeg 340 332 %}

### Preview: Marked 2

On the other hand, if you use the magnificent [Marked 2](http://marked2app.com) program to render your HTML, well, it has MathJax support built-in. Under **Preferences**, choose the **Style** tab and check **Enable MathJax**. 

**Note**: Marked 2 does *not* have the intermittent problem of failing to render MathJax properly while you are editing the document.

---
<br/>
So there it is, simply add the MathJax using delimiters to your Markdown file and update the previewer to render it.

*Follow the author as [@hiltmon](http://https://twitter.com/hiltmon) on Twitter.*

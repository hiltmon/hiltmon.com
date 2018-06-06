---
layout: post
title: "Add Web Clip Icons to Octopress"
date: 2013-02-10 13:57
comments: true
categories: [ web, Octopress ]
---

The default [Octopress](http://octopress.org) setup includes a `favicon.png` which enables you to place your own tiny icon to the left of the URL in most browsers. You should see a small blue cog there now.

Both Apple and Android phones also support saving a link to a site (called a web clip) on your phone as an icon. Over the past few days, it seems quite a few viewers of this site have added it as a web clip, but I had not provided good iconage.

Here’s how to add a web clip on the iPhone:

{% img /images/web-clip-banner.jpg 718 272 %}

In order to customize this experience, you need to provide up to four image files for download and to add some code to the `head` in your site.

Create a set of `.png` files containing the icon in the following sizes (you can use any file names, these are common):

* **57x57** for iPhones (apple-touch-icon.png)
* **114x114** for retina iPhones (apple-touch-icon-114x114.png)
* **72x72** for iPads (apple-touch-icon-72x72.png)
* **144x144** for retina iPads (apple-touch-icon-144x144.png)

There is no need to round the corners or add the shine, the phone will do this for you.

Then add this code to the `head.html` file in **source/_includes/custom/head.html**. If you’re not using Octopress, just place this code within your `<head></head>` tags.

``` html
<link rel="apple-touch-icon" href="apple-touch-icon.png" /> 
<link rel="apple-touch-icon" sizes="72x72" href="apple-touch-icon-72x72.png" /> 
<link rel="apple-touch-icon" sizes="114x114" href="apple-touch-icon-114x114.png" />
<link rel="apple-touch-icon" sizes="144x144" href="apple-touch-icon-144x144.png" />
```

Make sure the image files are in the root of your site (same place as the favicon) then generate and deploy the site.

The next time a user adds your site as a web clip, the phone will download the appropriate image file, add the shine, round the corners and make that the custom icon.

*Follow the author as [@hiltmon](http://https://twitter.com/hiltmon) on Twitter or [@hiltmon](http://alpha.app.net/hiltmon) on App.Net.*
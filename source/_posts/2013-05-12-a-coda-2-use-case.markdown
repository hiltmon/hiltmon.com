---
layout: post
title: "A Coda 2 Use Case"
date: 2013-05-12 11:20
comments: true
categories: [ Tools, Web, Design ]
---

{% img right /images/coda2.png 128 128 %}

I upgraded to [Panic's][panic] [Coda 2][coda] when it came out, *and never used it*. Unless it was to trigger a software update.

That was until last week.

Last week I was working on an *odd* project to create a set of web pages that would be hosted on a payment processor's site, but must look and feel like they are running on the actual site. This was for some non-profits to enable them to accept credit-card donations and electronic payment of member fees. Think of it as a customized set of Paypal pages that run on Paypal's servers, yet are customized to the look and feel of the parent. Without Paypal, of course.

Since our payment processor's servers could only handle plain-old HTML and CSS files, this looked like a job for my trusty hammer tool, [BBEdit][bbedit]. Which is what I started with. [BBEdit][bbedit]'s handling of HTML and CSS is excellent. So, my plan was to mock up the pages as plain old HTML and use [BBEdit][bbedit]'s live preview window to check that it looked right. I would then copy the final pages to a new [BBEdit][bbedit] project where I could then insert the payment processor's *funky* markup to make it work. And then iterate. As you do.

But that led to a problem, one of navigation. I needed one [BBEdit][bbedit] project window open for the mockup HTML (bottom left), another project window open for the processor's templates (top left) and *one preview window open for each page being mocked up.* This is because [BBEdit][bbedit]'s preview window is tied to the editor frame that is current when opening it, and it does not switch when you change to another editor frame containing a different file.

{% img /images/bbedit-multi-preview.jpg 700 438 %}

I tiled the preview windows to help, but got confused as to which preview window to look at when I made a change to a HTML file. I tried just using one preview window, but that meant I had to close and open a preview each time I switched pages. This process was slowing me down.

I think I wore out my `⌘-~` (switch window) key jumping around. The problem was that my muscle memory kept on making me hit `⌘-⇥` (switch app) when moving between mockup-pages and the templates *even though they were in the same application*. My brain was seeing these as two separate products.

So, in personal OCD frustration, I decided to use another product for some of the work.

And remembered I had [Coda 2][coda] which contains integrated previews. So I opened the mockups folder as a site in [Coda 2][coda] and used its split panes feature to add a preview window for *each* mockup, and then created a tab for each mockup page. And it worked brilliantly.

{% img /images/coda-single-preview.jpg 700 446 %}

I could focus on a single mockup page in [Coda 2][coda], see its changes live in the split-pane preview window, and jump tabs to work on different mockup pages with their *own* previews. Which suited my mindset. And then use `⌘-⇥` to jump back to [BBEdit][bbedit] to modify the templates, which suited my muscle-memory. And which kept me sane.

*I then found out you could even add the CSS file as an additional pane in [Coda 2][coda], which made testing and customizing these mockup pages exceptionally easy and pleasurable.*

The result is that I got to create and test these mockups quickly and easily in [Coda 2][coda], run and post the marked-up templates from [BBEdit][bbedit], iterate as necessary, and got the job done on time without further frustration. I don't know of any other product that has live *integrated* pane previews for static HTML sites like [Coda 2][coda] does. Thank you, [Panic][panic], for this use case.

*Follow the author as [@hiltmon][twitter] on Twitter and [@hiltmon][app] on App.Net. Mute `#xpost` on one.*

[app]: http://alpha.app.net/hiltmon
[panic]: http://www.panic.com
[coda]: https://itunes.apple.com/us/app/coda-2/id499340368?mt=12&uo=4&at=10l894
[bbedit]: https://itunes.apple.com/us/app/bbedit/id404009241?mt=12&uo=4&at=10l894
[twitter]: http://https://twitter.com/hiltmon
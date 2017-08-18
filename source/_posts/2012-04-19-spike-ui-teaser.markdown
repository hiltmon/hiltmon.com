---
layout: post
title: "Spike UI Teaser"
date: 2012-04-19 18:49
comments: true
categories: [Software]
---

Following on to last week's [Spike Solutions](https://hiltmon.com/blog/2012/04/06/spike-solutions/) piece, I did some work on the second spike, to see if I could use CoreGraphics to render some of the UI components I want for the new product. Wow, worked out great, one less known unknown to deal with. Turns out, CoreGraphics does a lot of what you can do in PhotoShop, just in real time and on the GPU.

The following snaps were generated on the fly, quickly, using code, no image or artwork required, and the values change and update dynamically. The best part, I can skin them later once I pick the theme and design for the product (or just use these as is).

{% img /images/spike-ui-number-panels.png 205 326 %}

Note the subtle gradient in the large numbers, the glow around the panel titles, and the strong gradient in the pie slice.

{% img /images/spike-ui-graph-panel.png 455 288 %}

The graph scales as the data is added, there are no escapee pixels on the line joints, and the points are correctly positioned.

I have not yet decided whether to share this spike's code like I did the last one, let me know if you would like to see it. Remember, it's spike code, to be thrown away, so it may work, but it certainly stinks. One more spike to go.

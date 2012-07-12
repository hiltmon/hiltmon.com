---
layout: post
title: "Layer Cake Photoshop Artwork"
date: 2012-07-11 21:50
comments: true
categories: 
---

I have been using the same process to export application artwork using [Adobe Photoshop](http://www.adobe.com/products/photoshop.html) *forever*. Most Mac, iOS and Web applications have large numbers of small image files that are used everywhere. They need to be sliced up, scaled and exported into the files and formats needed by the application. Exporting multiple art items in multiple resolutions has been a tedious and time consuming task, a task that had to be repeated manually every time the artwork changed. Until now.

## The Old Process

*Even to read about it is slow and tedious, and you probably do it the same way. Feel free to skip the next few paragraphs and jump to the new process to stave off boredom.*

The first thing I do with all artwork is create a set of Photoshop master files for each major element, such as the splash screen and icon. I then create additional master files for all buttons, another for all icons and more for any additional image elements needed. Since retina came along, my masters are all retina sized.

Then, to create the `.png` files that I use in the application, I would manually use Photoshop's `Save for Web...` dialog to save the retina version, then run it again to to scale it down and save the regular version. That's fine for one file with one element. But with icon sets or button sets it gets worse. 

Say I have five buttons in my button set, each having a standard and pushed version. I'd have a shape layer for the regular state, a shape layer for the pushed state and text layers and image layers for each button variant. I would then create ten layer comps, one for each combination of button layers to reflect each button state image desired. It looks like this:

{% img /images/photoshop-with-layer-comps.png 366 369 %}

This works great, all I have to do is change 1 layer and all my buttons get updated. But to export, I would have to have to run `Save for Web...` twenty times to get the 20 `.png` files needed, twice for each layer comp (retina and regular). Make one change, 20 more `Save for Web...` runs. Manual. Slow. Tedious.

I tried using the built-in scripts. Photoshop does have a `Layer Comps to Files...` script which will dump all comps as `.png` files. I'd then have to rename all the files, and then open each one in [Acorn](http://flyingmeat.com/acorn/) and resize it for regular size. Hassle factor high, and the quality starts to diminish (not Acorn's fault, I'm using a bitmap to make another bitmap).

## The Layer Cake way

This week, I needed image buttons for a [Cocos2d](http://www.cocos2d-iphone.org) game I am writing, one button for each of the 9 game levels, with a regular and pushed state. That's 18 regular images and another 18 retina images (I chose not to create a disabled state as that would increase it from 18 to 27 regular and 27 retina images). I spent less than an hour creating the button regular background layer, pushed state background layer and each button's face. I then spent another three hours manually exporting 36 images each time, copying them into the application, running it, finding fault, changing one thing in Photoshop, exporting 36 images again by hand, screwing up the file names, and iterating again and again. Ouch.

**Aside: In-Game Compositing***. I am aware that I could have just created the button background and button pushed state background images and used code to composite the buttons in real time in the game code. Unfortunately, the fonts I need are not licensed for distribution with games, so I needed to create static images here.*

{% blockquote Me, Now %}
When one gets sufficiently frustrated with a process, eventually one goes out and looks for a better solution.
{% endblockquote %}


And the good people at [MacRabbit](http://macrabbit.com) had just the thing. I have been using their excellent [CSSEdit](http://macrabbit.com/espresso/) product for years (now merged with Espresso). The product is called [Layer Cake](http://macrabbit.com/layercake/), the idea is simple and the execution is wonderful.

In Photoshop, create layer groups for each element in the file, *and name the group with the file name you want it exported as.* Like this: 

{% img /images/photoshop-layer-cake.png 640 683 %}

When you want to export the images, drag and drop the `.psd` file onto Layer Cake and it creates the images for you. Like magic.

But there's more. If you name the layer group (file) with the iOS standard `@2x` syntax, Layer Cake exports both the retina and regular file versions and names them correctly. Better magic. This is it:

{% img /images/layer-cake-results.png 612 433 %}

And there is more. Layer Cake *remembers* what you did, which means you can *repeat* the process anytime. And it can create multi-resolution `.icns` files.

So, from now on, I'll use layer styles instead of layer comps for each artwork component in Photoshop, label each layer group with the export file name and use Layer Cake to export all the many artwork files needed in the application automatically with a simple drag-and-drop or repeat.

I'll save a ton of time and tedium recreating artwork files.

And I'll ask my graphics designers to make Layer Cake compatible files from now on, too.

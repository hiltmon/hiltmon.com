---
layout: post
title: "Solve Tab Hell with Fluid and ChoosyOSX"
date: 2014-05-23 15:49:52 -0400
comments: true
categories: 
---

More and more of our data, applications, communications, reading and work happens via a browser tab on the internet. I don't know about you but I often have several browser windows open on several virtual desktops all with multiple tabs open.

And I can never find a thing.

So I open a new tab. And start again. Tab hell.

{% img /images/tab-hell-1.png 600 172 %}

Now this is fine for reading or browsing - you just walk the tabs to see what you were looking at. But for work, when you need to go to a specific web application that *you just know you have open somewhere*, it becomes a bother. You have to go to each browser window, walk the tabs, switch desktops, walk more. It's too slow and unproductive.

Wouldn't it be nice if you could use COMMAND-TAB (⌘⇥) or [Alfred](http://www.alfredapp.com) or Spotlight to get to that work tab quickly?

The solution I have found is to use *Site Specific Browsers* for each work web application, and software to ensure that all links clicked go to the right *Site Specific Browser*. In other words, lets say I want to separate Facebook tabs out. I create a Facebook *Site Specific Browser* and set it such that any links that contain `facebook.com` should open in that *Site Specific Browser*. I can then COMMAND-TAB or Alfred or Spotlight to Facebook without having to look through all my browser tabs.

{% img /images/tab-hell-2.png 600 115 %}

Can you tell which applications are native and which are *Site Specific Browsers*? <span class="light">Solution: Google Analytics, Facebook, Asana and Bitbucket are *Site Specific Browsers*.</span>

Here's how to set it up.

### Site Specific Browsers

A *Site Specific Browser* is an application that presents the web pages of a single site as it it were a native application. It's really just a wrapper around your regular browser. To the operating system it looks like yet another native application, which means all the native switching you can do just works.

For example, my Facebook *Site Specific Browser* looks like this:

{% img /images/tab-hell-3.png 600 87 %}

Not that there seems to be no browser chrome or address bars, just a regular window frame called Facebook.

I use [Fluid](http://fluidapp.com) for these. You can download it [here](http://fluidapp.com).

To set up a new *Site Specific Browser*, launch [Fluid](http://fluidapp.com) and paste in the URL for the site into the form. Hit `create` and it will create a *Site Specific Browser* by that name in your **Applications** folder. You can customize the icon to make it look better too.

{% img /images/tab-hell-4.png 600 261 %}

To access Facebook now, you can launch it like any other application. It appears on your dock, application switcher and spotlight like a native application.

<span class="light">Aside: If you get the paid version of [Fluid](http://fluidapp.com) (which I highly recommend), you can add scripts to badge *Site Specific Browsers* and can separate the cookies so vendors cannot track you, for example if you want to keep your Gmail activity separate from your searching activity.</span>

### Directing Links

The problem remains if someone sends a link to a Facebook page in an email or message, then that link will open in your usual browser, not the Facebook *Site Specific Browser*. Which means that tab hell is still probable.

But there is a solution for that too.

[ChoosyOSX](http://www.choosyosx.com) is an application that allows you to choose which browser a link will open in. You can use it to redirect all links to the correct *Site Specific Browser*. ChoosyOSX can be downloaded it from [here](http://www.choosyosx.com).

To enable the redirect, go to **Choosy Settings... / Advanced** and create a new rule for each *Site Specific Browser*. In this case, I am redirecting all `facebook.com` URL's to the Facebook *Site Specific Browser*.

{% img /images/tab-hell-5.png 600 623 %}

From now on, any Facebook link in any app (or on the web) will open in my Facebook *Site Specific Browser*.

### No more tab hell

And that's all there is to it. My work web applications are all in their own *Site Specific Browsers* and any links to them open in the right browser. All other web links open my usual web browser. I can launch and switch between my work web applications as easily as launching a regular application (or clicking a link). And still browse the web as usual otherwise.

<span class="light">At the time of writing, [Fluid](http://fluidapp.com) is $5 and [ChoosyOSX](http://www.choosyosx.com) is just $12, the massive time savings are certainly worth a measly $17.</span>

*Follow the author as [@hiltmon](http://https://twitter.com/hiltmon) on Twitter and [@hiltmon](http://alpha.app.net/hiltmon) on App.Net. Mute `#xpost` on one.*
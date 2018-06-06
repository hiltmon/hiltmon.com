---
layout: post
title: "Spotlight Only - Nine Months Later"
date: 2016-04-10 11:20:22 -0400
comments: true
categories: Productivity
---

<span class="light">I think one should review one's productivity tool load-out every once in a while. Operating system updates, other productivity tool updates and your own work practices change over time. Your tool load-out should too. Changing the muscle-memory, it turns out, is surprisingly simple, quick and easy. And your productivity usually increases.</span>

I am a huge fan of keyboard launcher/productivity applications like [LaunchBar](https://www.obdev.at/products/launchbar/index.html), [Alfred](https://www.alfredapp.com), and back-in-the-day [QuickSilver](https://qsapp.com). They were amongst the first applications installed on any new system, and I believed I could not work productively without them.

Nine months ago I rebuilt my 15" MacBook Pro for some forgotten reason and decided to see if I could operate productively with Apple's built-in Spotlight only for the *core* features that LaunchBar and Alfred provided.

<span class="light">To make it clear though, my use-cases for these products were basic, mostly using them as shortcut launchers. I never used the advanced scripting features, rarely added plugins, forgot about the additional actions on results and never touched the clipboard histories provided. Mostly because I had [Keyboard Maestro](http://www.keyboardmaestro.com/main/) juiced up to take care of those functions and more.</span>

Its been nine months, and I am just as happy and productive as ever. Apple did a great job with the Yosemite Spotlight power-up, and the El-Capitan update made it just that much better.

So here's a core set of Spotlight features — it's a short list — and how it compares with Alfred or LaunchBar:

### Application Launcher

Spotlight launches applications just as well as the others, including with abbreviations. For example, to launch Navicat Premium Essentials, a Spotlight of `npe` puts it at the top as expected.

<span class="light">**Result**: Just as good and quick.</span>
	
### Text/File Finder

Type a few words and it finds matching files and their contents very quickly. Unlike the commercial applications, Spotlight returns far fewer results in the HUD screen, but you rarely need more than the top four to find the file you want. Also, since El-Capitan, it now searches on partial strings. Note that I also needed to add a [Markdown Plugin](https://hiltmon.com/blog/2015/11/17/a-yosemite-markdown-spotlight-importer/) to make it work perfectly for me.

<span class="light">**Result**: Mostly the same, a longer and customizable result list would be nicer. I know you can resize the Spotlight screen, but I want more results per category, not a larger screen showing more categories.</span>
	
### Contacts

Type the first few letters of a person's name and Spotlight shows their contact card. Move the mouse over an email or phone to get a click-through icon to send a message, etc. The commercial applications are much better here, allowing you to keep your hands on the keyboard and select an action from the card.

<span class="light">**Result**: Not as good, but enough for me to see the phone number I need to punch in.</span>
	
### Web Search

Spotlight does have the ability to search the web via Bing (shudder). I do not use this. If Spotlight could use Google or DuckDuckGo it would be a different story. Instead I have a keyboard shortcut in Keyboard Maestro that launches Safari and allows me to search DuckDuckGo in one keypress. So I turned this off on Day 1, Bing search is rubbish.

<span class="light">**Result**: The third party applications do this way better.</span>
	
### Actions on Results

One thing Spotlight does *not* do is provide more actions once a result is found. You cannot do anything more with a found result except open an application, you cannot even select the application to use or run a macro on it. Since I never used that feature, I don't miss it.

<span class="light">**Result**: If this is your primary way of using Alfred or LaunchBar, and I suspect thats how most of you use them, this missing feature is a showstopper.</span>
	
### Other

I rarely use Spotlight to search for a stock price, weather, sports score or local movie time, these things are all far more conveniently available on my iPhone (and I have notifications set up for the important stuff).

<span class="light">**Result**: Same, same.</span>

I am sure there is a lot of functionality that I could be missing out on, but since I am pretty much all-in on Keyboard Maestro, Apple's built-in Spotlight works just fine for my launching and searching needs. Anything more complex gets a keystroke macro in Keyboard Maestro.

*Follow the author as [@hiltmon](http://https://twitter.com/hiltmon) on Twitter.*
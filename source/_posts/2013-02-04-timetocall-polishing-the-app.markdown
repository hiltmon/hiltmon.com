---
layout: post
title: "TimeToCall - Polishing the App"
date: 2013-02-04 09:34
comments: true
categories: [ TimeToCall ]
---

*[TimeToCall]({{ root_url }}/timetocall/) is a simple, universal iOS application I developed to help people choose the best time to call when calling internationally. This is [**part 7** in a series of posts]({{ root_url }}/blog/categories/timetocall/) about the thinking and work done. My goal is to share just how much effort it really does take to craft an iPhone app and ship it. I hope this series helps you to understand why it costs so much and takes so long to create beautiful software. [Back to part 6]({{ root_url }}/blog/2013/02/03/timetocall-sweating-the-details/) or [start at part 1 first]({{ root_url }}/blog/2013/01/29/timetocall-the-effort-and-the-return/).*

## Polishing the App

An application is *not* finished and ready to ship when the screens work and it does not crash. An application is *not* finished when the animations and art are completed and the details sweated. It still needs to be polished. There still needs to be some serious work done.

[Sweating the Details]({{ root_url }}/blog/2013/02/03/timetocall-sweating-the-details/) is all about making it *work* right. Polish is all about the invisibles, making it *feel* right and *be useable by everyone*. **Polish makes the application be the way users expect it to be**.

## VoiceOver for Unsighted Users

Not all users of iOS applications have perfect vision. iOS enables them to use the iPhone using [VoiceOver](http://www.apple.com/accessibility/voiceover/) whereby the device *says* what the person is touching. They can then double-tap to activate that function.

Try it. Go to **Settings / General / Accessibility** and turn on **VoiceOver**. I have it set as a triple-click on my home button. Then try to use your iPhone (and close your eyes).

A good app supports VoiceOver. I needed to add the *speakables* to each element of the app so unsighted people can use it.

## Internationalization away from English

And not all users of iOS apps are native English speakers either, so apps need to be translated into the local language for each market. The process is called localization and requires the developer to pull out all the strings in the app and get them translated.

Actually, Apple makes this really easy in Xcode, you just create a `.strings` file and then add languages to your app. Xcode creates the language versions of each for you.

For [TimeToCall]({{ root_url }}/timetocall/) version 1.0, the only language I *can* localize it to is Japanese, so I did that.

But internationalization is not just a straightforward word for word Google translate. If you do that, you app will look terrible, and your users will notice it. **You also need to take into account the nuances and conventions of each language and its culture**. In [TimeToCall]({{ root_url }}/timetocall/), the terms used in the Japanese translation are *not* the same terms as per the English original, but are far more recognizable by Japanese users than the English translations.

## Fonts and Sizes

The thing is, when you internationalize an app, the size of fields changes. Words that are short in one language may be long in another, and Kanji (or Chinese) characters are usually rendered larger than English capital letters. Which means that a label that looks right in one language may get truncated or cropped in another.

iOS has an *autolayout* feature that helps, but it’s new and confusing and only works on iOS 6. For [TimeToCall]({{ root_url }}/timetocall/), I wanted it to run on iOS 5.1 so I could not use *autolayout*. Instead, I polished the app by changing a field sizes and font choices by language to make sure the Japanese text was just as readable as the English and still looks balanced.

## Fixing the Edit Field

I placed the name of a [TimeToCall]({{ root_url }}/timetocall/) in an editable field inside a table cell on the Edit view. If the user taps the name, the keyboard springs up and the user can change the name. By default, the app uses a “Call from &lt;Location&gt;” placeholder, which is quite long. Deleting it takes time. So I added the clear field icon to make deletes quicker.

To edit in the middle of the name, though, you need to slide your finger along the text to move the caret to the chosen position. Now, your hands may be steady, but mine aren’t, so sometimes the whole row would scroll away. Polish means that that row does not scroll while you are editing it.

Polish also means that the keyboard should go away as soon as you are finished editing the name. This happens by default on the iPhone, but not on the iPad. It took me a long time, and a good few StackOverflow searches, to find the solution. It is sufficiently important to hide the keyboard that I needed to add a Objective-C category to UINavigationControllers just to make this happen. *But from the user’s perspective, the application behaves as they expect it should*.

## New TimeToCall Entry

The conventional Apple approach to creating new records is for the user to tap a `+` button and a new item, filled with nice defaults, pops on the top of the list. Then the user has to tap *again* to show the detail, and tap *again* to edit it to set it up. This leads to many copies of the default entry being left in the list and too many steps to create a new entry.

So, when polishing the app, I set the `+` button to launch the edit window directly and to present a default *Time to Call*. If the user hits `Cancel` because they did not want a new one, no new one is created. If they tap `Done`, then a new row is added.

One tap to add new. Much better.

## When to Scroll or Search

The *Pick a Place* view lists all places to enable users to browse and find a place they need. It also has a search bar to help them get there quicker.

To add a new place to a *Time to Call*, using standard behaviors, you would tap on `Tap to Add a New Place` and the picker would come up displaying the list at `A`. You would then have to tap the search field to bring up the keyboard, then search, then choose a place. Again, too many taps.

After polishing, if you tap on `Tap to Add a New Place`, the app focusses on the search bar and has the keyboard up and waiting. Lovely.

But what if you already have a place in that row and want to change it. What should the app do? Well, if it follows the ‘add’ idea above, the app would jump to search, the user would not be able to see which place was being edited, and has to cancel to browse. Not optimal. Instead, it should show the user the current place in the list so they can decide whether to change it or leave as is. 

*That is what users expect, so that’s what it does*.

And that is why we spend the time and effort to polish.

**Next:** [Part 8: The MacGuffin]({{ root_url }}/blog/2013/02/05/timetocall-the-macguffin/).

---
&nbsp;  
*[TimeToCall]({{ root_url }}/timetocall/) can be downloaded from the [App Store](https://itunes.apple.com/us/app/timetocall/id596429979?ls=1&mt=8) for 99c.*

*I hope you enjoy [this series of articles]({{ root_url }}/blog/categories/timetocall/) on what goes in to the design and development of an iPhone or iPad application, and have a better feel for why these things take so much time and cost so much. If you like them, buy [TimeToCall]({{ root_url }}/timetocall/) from the [App Store](https://itunes.apple.com/us/app/timetocall/id596429979?ls=1&mt=8), it helps me continue to write, and please tell your friends about these articles and this product.*

*Follow the author as [@hiltmon](http://https://twitter.com/hiltmon) on Twitter or [@hiltmon](http://alpha.app.net/hiltmon) on App.Net.*

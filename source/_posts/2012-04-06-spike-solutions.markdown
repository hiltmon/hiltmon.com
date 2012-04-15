---
layout: post
title: "Spike Solutions"
date: 2012-04-06 10:12
comments: true
categories: 
---

I am a huge fan of throwing together a few *spike solutions* at the start of a project. I get the biggest technical problems solved early, I gain understanding of any pitfalls I may encounter and I can estimate the time and work better. I highly recommend the practice. A few days spent spiking solutions saves weeks and months later.

Get your geek on, were diving in.

*A **spike solution** is a software project to figure out a tough technical or design problem (note: singular). Use it to explore potential solutions, ignoring all other requirements and standards. Expect to throw it away. The goal is to see if and how a specific problem can be dealt with.*

I use spike solutions in several scenarios:

* To see if something is doable
* To help me understand the issues relating to a technical problem and to find pitfalls
* To help create better estimates for large and complex projects
* To see if I can make something faster or more reliable

I have an itch to scratch, a product that I'd like to have and therefore to write. Sorry, not saying what it is. So I start thinking about the feature set and the technical needs.

To paraphrase Donald Rumsfeld, there are *known-knowns*, *known-unknowns* and *unknown-unknowns*. Nothing you can do about the *unknown-unknowns*. You already have the *known-knowns* covered. It's the *known-unknowns* that concern me. So I spike them.

In this case, I have three *known-unknowns* in the projected application - how hard is OAuth2, can I create some of the display widgets and can I thread plugins. Looks like I have three spikes to work on. We'll look at the first.

## Example: SpikeOAuth2

*If you want to see this spike solution, it's available at [hiltmon / SpikeOAuth](https://github.com/hiltmon/SpikeOAuth) on GitHub. **Warning**: It's a spike solution, so no documentation, tests, coding standards or refactoring. In other words, this code stinks, do not use it.*

First, I looked at the protocol at [OAuth 2.0](http://oauth.net/2/). Ouch, looks complex. Will take a while to write. But it seems like that's been taken care of as they link to existing code libraries. This may be easier than I think. But I am a little concerned. The application will rely on a robust OAuth2 implementation, are these good enough? And neither of these are both Mac and iOS, which is what I need. Still worth spiking.

I did a bit of research and came up with a library that seems to fit the bill. Oauth2 - check, Mac version - check, iOS version - check, reputable maker - check. It's Google's [gtm-oauth2](http://code.google.com/p/gtm-oauth2/) library. So, can I make this work?

I created the spike solution. Figured out the dependencies. Got it compiling. And it failed to work first time on the first site - [StackExchange](https://api.stackexchange.com/). Ok, into the debugger, added log statements to the Google code to see what is going on. And lo and behold, a bug on the server side was causing it. A quick turnaround with support (see [Receiving “redirect_uri does not match the uri used to create the passed code”, when it does match](http://stackapps.com/questions/3295/receiving-redirect-uri-does-not-match-the-uri-used-to-create-the-passed-code)) and it works. Kinda. The Google library, it seems, is too new, and StackExchange does not yet support it. Pitfall found.  Quick hack to the library, and it all works. This spike, and this library, seems promising.

But can it access other sites just as reliably?

Try another site, [Disqus](http://disqus.com/api/docs/). Wow, that went smoothly. Ok, try [Google](https://developers.google.com/accounts/docs/OAuth2), using the standard version of the library. Yay, that works. I now have confidence in the library.

Just one more test - [Twitter](https://dev.twitter.com/).

*Bah-booooww.*

Twitter does not support OAuth2. Research shows that several of the sites I want to access are the same. And OAuth2 is not backwards compatible with OAuth1. New issue identified, pitfall encountered. Now what?

Since Google has an OAuth2 library, I checked to see if they have an OAuth1 library. And they do. Added it to the spike, handled the conflicts. And now the spike does OAuth with Twitter ok.

The spike solution has proven that I can do OAuth (1 and 2) reliably with Google's code. One *known-unknown* is now a *known-known*. Time to walk away and get on to the next spike.

## Next Steps

Now that I know that the OAuth2 process is doable, there is much that could be done to this code to make it better and more usable:

* Instead of one View per source, create a single View and create an object for each source as a parameter to the view
* Consolidate the common code into a common object, and enable each source to configure the common object instead of repeating all the authentication code
* I am unhappy that the OAuth and OAuth2 code libraries are separate, with much repeated code. I plan to create a forked version of the Google code such that the user just chooses which version of the protocol to use and the library will handle it. Should get rid of the duplicated `authentication` and `signin` objects. And I could probably share it for others to use.

But I'm *not* going to do any of that now. The purpose of this spike solution was to see if using OAuth2 was doable, and how hard it was. Now I know. It has done its job, proven that it can be done and how to do it. I know how much work and effort it will take to add connections. When I get to writing the real application, that's when I can and will do the rest.

Now on to the next spike.

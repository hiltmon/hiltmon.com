---
layout: post
title: "Mischief Managed: Update Tools, Learn New"
date: 2012-08-06 12:38
comments: true
categories: Mischief-Managed
---

***Mischief Managed** is a series of posts on tasks and technologies I use to maintain my computing environment. It’s part of what I do between projects. Try it out.*

Most of us do not update our operating systems or toolkits while a project is ongoing. It increases the time to produce the product, adds risk that things will stop working, it’s just not worth doing. But once the project is over, it’s time to update the tools and study new ones.

Since most of my work these days is in [Xcode](https://developer.apple.com/xcode/) or [Rails](http://rubyonrails.org), here’s what I do for them and what I am learning now.

## Xcode Work

Xcode usually gets updated when either OS X or iOS gets updated.  When I am *not* involved in any OS X or iOS projects, I usually run the latest beta of Xcode to spike solutions or learn new APIs. As soon as a project starts, I remove the beta, install the latest release version and stay on the latest release for the duration of the project.

On thing, save the Xcode installer. Apple does have them on the [Developer Downloads](https://developer.apple.com/downloads/index.action) page, but sometimes they are lax about posting it. Also, save the installer for the version of OS X you are using. These days with App Store updates, Apple deletes the OS Installer after installing. I usually make a Flash Drive installer, just in case (See [How to Burn Your Own OS X Lion Install DVD or USB Drive](http://lifehacker.com/5823096/how-to-burn-your-own-lion-install-dvd-or-flash-drive) for how).

Now most Xcode developers usually remain on the same version of OS X and Xcode for the duration of the project, meaning that they often remain one or two versions behind to reduce platform risk. I am too impatient to do that. What I usually do *during* a project *if* there is a major OS X or Xcode update, is update the Laptop to the new version and create a project branch to test it. *I do this in my spare time as it should not affect my customers.* If it works, then I merge the branch and stay on the new version.  If not, I nuke the branch and revert the Laptop. So far, the reversion only happened once, when Xcode 4.0 came out and was too buggy to use. 4.1, 4.2, 4.3 and now 4.4 have all gone smoothly.

## Ruby and Rails Work

For Ruby and Rails work, I use [rvm](https://rvm.io). It enables me to have project specific versions of Ruby, Rails and gemsets installed. For example, the [Noverse.com](http://www.noverse.com) website runs `ruby-1.9.2-p320`, [Kifu](http://www.kifuapp.com) runs on `ruby 1.8.7-p358` and [Hiltmon.com](http://hiltmon.com) is on `ruby-1.9.3-p194`. Hmm, now that Kifu is in production, maybe I should update its toolkit.

With `rvm` I don’t have to worry about platform risk, and can upgrade projects to new versions independently.

But once projects are over, I like to install the latest version of Ruby and Rails as a new `rvm` for spikes, new projects and learning. It also helps to have these as default for downloading and trying out projects from GitHub.

## New Platforms and Technologies

One thing I love to do between projects is play with and learn new platforms, languages and technologies. Not only do I learn and adopt new things this way, but I also import ideas from these in my more traditional projects. It is because of this ‘playing’ that I moved from Perl to Ruby for scripting, and ASP.Net to Rails for web. 

I believe it’s important for a technologist to study other technologies to become a better technologist.

Right now, I’m playing with [node.js](http://nodejs.org) as a potential platform for some of my next personal projects, and comparing it to the [Sinatra](http://www.sinatrarb.com) via Ruby stack. I have yet to be approached to program a real system using either of these stacks, but who knows what I’ll be working on next, and they are both fun products. 

I’m also looking at the [Clojure](http://clojure.org) and [Haskell](http://haskelllive.com) functional programming languages to see if I can get my head around them for future work. And playing with [Lua](http://www.lua.org) and [Cocos2D](http://www.cocos2d-iphone.org) for game development. This research is but in the early stages.

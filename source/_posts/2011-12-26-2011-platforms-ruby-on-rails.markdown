---
layout: post
title: "2011 Platforms - Ruby on Rails"
date: 2011-12-26 11:55
comments: true
categories: [ Ruby, Ruby on Rails, TextMate ]
---

*Part 2 of the platforms I used in 2011 to make products. See [Part 1 - Objective-C and iOS](https://hiltmon.com/blog/2011/12/26/2011-platforms-objective-c-and-ios/).*

The second half of 2011 was spent developing two web app products using Ruby on Rails. And what a joy this platform is to use.

<!--more-->

I started coding in Ruby back in 2007 when Perl started to bug me. I had used Perl as my go-to scripting language since about 2001, but its inconsistencies and funky syntax was driving me nuts.  I experimented with Python and almost made the move to it when I stumbled upon Ruby.

I chose Ruby for one simple reason, the *elegance* of it. Both Ruby and Python are brilliant high level, dynamically typed, garbage collected languages with extensive excellent libraries, great documentation and have more in common with each-other than with Perl.  I just fell for Ruby, its blocks, the *Ruby way*, they all made sense to me.  Probably because Ruby was heavily influenced by my seminal language, Smalltalk.

When it came to choosing the platform for the two web applications this year, I had several choices, but really none. I could have used PHP for the front-end and something else for the back end, but PHP is a messy inelegant solution and I wanted a consistent platform between front and back. I could have used ASP.net but the new .Net libraries are too bloated and I did not want to be forced onto Windows servers. I could have used Java and servlets, but the libraries for Java are an inconsistent mess.

On the other hand, Ruby on Rails is simple, clean and elegant. Its open, consistent, runs fast enough and is sufficiently scaleable. And it enables rapid application development, which made my clients very happy.

My first true Ruby on Rails experience was for one of my iOS applications. My client was developing the server while I developed the iOS client. I needed a development server to test the iOS app, because the production server was only going to get done at the same time the iOS app was to be released. So I wrote one in Ruby on Rails. It took me only a few days to create the protocols that were to be used in production and it allowed me to get the iOS app done right and launch it on time.

For those unfamiliar with Rails, there are only a few things you need to really know. Its an architecture as well as a platform. Models, views and controllers are separated and linked using naming conventions. REST is the way to go, routes follow the architecture and test driven development is not only encouraged but built right in.

For my two products ([Kifu](http://www.kifuapp.com) being one of them), Ruby on Rails is the perfect platform.  Its easy to add features and grow the product, easy to find issues and resolve them, easy to deploy and easy to maintain.  With `bundler` and `gem` plugins, I am able to add security, background threads, and test frameworks without effort.  The consistency of convention in the platform really helps a lot.  And it enabled me to create not one but two complex web applications in the last 6 months.

So here I sit, day in day out, [TextMate](http://macromates.com/) on the left, Safari on the right, terminal below, creating awesome product using a great platform, Ruby on Rails.

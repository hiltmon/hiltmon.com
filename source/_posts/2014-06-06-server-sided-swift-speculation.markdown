---
layout: post
title: "Server-sided Swift Speculation"
date: 2014-06-06 19:02:20 -0400
comments: true
categories: Apple
---

<span class="light">Note: This is not a thing, it's just some idle speculation on my behalf. But maybe, just maybe, Apple will do something like this. Or not. Maybe we will do it.</span>

{% img right /images/swift-hero.png 128 128 %}

This week at WWDC, [Apple](http://www.apple.com) surprised the developer world with their new programming language, [Swift](https://developer.apple.com/swift/). And astoundingly, it's almost ready for prime time Mac and iOS client software development already.

I would very much like to use a language like Apple's new Swift on the server side as well. I suspect that we may get some of what we need there, if not all.

Note that I do not see Apple as having a server-side strategy these days. They have [iCloud](https://www.apple.com/icloud/) for hosting data and limited apps, and seem to be in no mood to compete with [Azure](http://azure.microsoft.com/en-us/) or [Amazon](http://aws.amazon.com) in the app server market. They no longer make and sell [Xserve](http://www.apple.com/support/xserve/) servers and [Xsan](http://www.apple.com/support/xsan/) storage, they no longer make and sell [WebObjects](http://en.wikipedia.org/wiki/WebObjects), their excellent server platform, and [OS X Server](http://www.apple.com/osx/server/) is just OS X with a few more applications installed. Nope, no server strategy at all. Let the [Linux](http://en.wikipedia.org/wiki/Linux) folks have that.

On the other hand, like `gcc` before it, the `clang` compiler is open source, available on server platforms and being added to and maintained *in public* by Apple. Which means that I expect Swift to follow Objective-C in being opened up,  available and supported on all `clang` platforms. Which means Swift *could* compile and run just fine on Linux distributions which host the world's servers.

Most server applications these days are built using interpreted languages (such as [Ruby](https://www.ruby-lang.org/en/) ([Rails](https://rubyonrails.org)), [Python](https://www.python.org) ([Django](https://www.djangoproject.com)), [PHP](http://www.php.net) ([WordPress](http://wordpress.org)) or [Javascript](http://www.ecmascript.org) ([Node.js](http://nodejs.org))) or runtime-based languages ([C#](http://msdn.microsoft.com/en-us/library/67ef8sbd.aspx) or [Java](http://www.java.com/en/)). In most cases, these are plenty fast and stable. But when speed or scalability issues kick in, nothing beats a compiled language. I believe this is why Google is switching to its lovely [Go](http://golang.org) language. It compiles to native, threads beautifully and runs at fully native speeds using far less hardware for the same throughput than anything else.

Imagine if we could use Swift for the same thing. It has the flexibility of a scripting language with the raw speed of a fully compiled native language. It has a REPL and playgrounds for us to play in (not available in [Go](http://golang.org)), a blindingly fast and safe compiler, and all the language features needed to build these types of applications.

Imagine [Rails](https://rubyonrails.org/) written in Swift for bigger front end web applications that scale and thread without pain. Imagine smaller Swift projects using the [Node](http://nodejs.org) or [Sinatra](http://www.sinatrarb.com) model for fast and scaleable RESTFUL web-services. Imagine a Swift-based [Jekyll](http://jekyllrb.com) to create baked blogs (<span class="light">ok, went too far, this would be completely unnecessary as the whole web server can be compiled in</span>). Using a compiled multi-core language to process web requests would turn things around that much quicker, and yet the language is as easy to use as our current slow-running tools are. The speed of a scripting language with the speed of a compiled language and none of the memory management, buffer overflow and pointer issues. Win-win.

I'm speculating that's why Google developed and is investing so heavily in Go.

What's missing, of course, is the eco-system. *But that has been written before and can be written again*. It would be a heck of a lot easier to write if Apple offered [Foundation](http://en.wikipedia.org/wiki/Foundation_Kit) and a subset of [Cocoa](https://developer.apple.com/technologies/mac/cocoa.html). But none of the other scripting and runtime languages we use today had these libraries to start with either and they run just fine now.

I think languages like [Swift](https://developer.apple.com/swift/), [Go](http://golang.org) or maybe [Rust](http://www.rust-lang.org) are the future of server side. Fast to write, yet compiled and swift running, optimized for safety, reliability and multi-threading, saving us from scaling issues and excessive server costs without increasing the complexity of the application development and support process.

But with Swift, we may be able to go further. *One language to rule them all*. Shared common code across desktop, mobile and server. All native, all fast, all cores used.

It would be amazing.

*Follow the author as [@hiltmon](http://https://twitter.com/hiltmon) on Twitter and [@hiltmon](http://alpha.app.net/hiltmon) on App.Net. Mute `#xpost` on one.*
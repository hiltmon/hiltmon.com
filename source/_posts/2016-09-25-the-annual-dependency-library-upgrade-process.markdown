---
layout: post
title: "The Annual Dependency Library Upgrade Process"
date: 2016-09-25 14:10:56 -0400
comments: true
categories: 
---

At work, we write a lot of code. In order to remain productive, we reuse the same proven dependent libraries and tools over and over again. Which is fine. Until we start seeing end-of-life notices, vulnerabilities, deprecations, performance improvements and bug-fixes passing us by. At some point we need to update our dependencies for performance and security.

But its not that easy.

Take some of the libraries we use:

- [Google’s Protocol Buffers](https://developers.google.com/protocol-buffers/) are amazing. We’ve been on 2.6.1 for ages, but 3.1.0 is out and it supports [Swift](https://swift.org/) and [Go](https://golang.org/), two languages we surely would like to use. But the `proto2` format we use everywhere is not available in the new languages. We need to migrate.
- [ZeroMQ](http://zeromq.org/) moved to a secure `libsodium` base in 4.1, making it much safer to use. But the C++ bindings from 4.0.5 are incompatible. We need to migrate.
- `g++` on [CentOS 6](https://www.centos.org/) is ancient, version 4.4.7 from 2010. We’ve been using the `devtoolset-2` edition 4.8.2 from 2013 to get C++11 compatibility, with a few library hacks. But that version of `g++` produces horribly slow and insecure C++11 code. We skipped `devtoolset-3` even though `g++` 4.9 was better. `devtoolset-4` is out, using `g++` 5.2.4 from 2015, still not the latest, but it is much better at C++11 (without our hacks), more secure and faster. Yet is ABI incompatible. We need to migrate.

The amount of work seems staggering given we have well over 100 protobufs used across our code base, ZeroMQ everywhere and everything is compiled for production using `devtoolset-2`. The old libraries and tools are a known, proven platform. The current code is stable, reliable and fast enough. *It ain’t broke.*

The benefits are also hard to measure. Given all the effort to upgrade, do we really get that much faster code, that much more secure code? And what about the code changes needed to support new interfaces, formats and ABIs? What does that get us?

{% pullquote %}
For most IT shops, the discussion stops there. {" “It ain’t broke, don’t fix it!” "}, or “All pain for no gain, not gonna play.” They stay on the known tools and platforms forever.
{% endpullquote %}

{% pullquote %}
For my IT shop, things are different. We *want* to use new tools, new languages, new platforms yet remain compatible with our existing services. We need to be secure. And we really do need to eke out each additional microsecond in computing. {" No, if it ain’t broke, break it! "}
{% endpullquote %}

So, once in a while, generally once a year, we update the platform. Update the libraries. Update the tools. Update the databases.

And we do it right.

Firstly we try the new libraries on our development machines. [Homebrew](http://brew.sh/) installs make that easy for the dependencies. [Rake](http://rake.rubyforge.org/) tasks make it easy to upgrade our [Ruby](http://www.ruby-lang.org/en/) dependencies and [Rails](http://rubyonrails.org/) versions. We build and test our code in a migration branch and make sure it all works, changing to new interfaces and formats where necessary.

We then spin up a virtual machine on our production operating system ([CentOS 7](https://www.centos.org/) now), install the new compiler and dependencies, and rebuild all there. Given that issues are mostly resolved in development, we only find `g++` quirks in this test.

And then one weekend, we run the scripts to update our production servers to the new tools and dependencies and deploy the new versions.

And since we do this every year, it runs like a well-oiled machine.

It helps that we have tools to recompile, run and test our entire code base. It helps that we have tools to stage and deploy all our code automatically. And it helps that we have done this before, and will do it again.

Long term, the benefits are amazing. We can try new platforms with ease. Our code gets better, faster and more secure all the time. The need for workarounds and hacks and platform specific coding becomes less and less. The ability to nimbly move our code base grows each time.

Many of the projects we want to take on become possible after the annual upgrade. That’s why we do it.

[If it ain’t broke, break it.](https://hiltmon.com/blog/2011/12/17/hiltmonism-if-it-aint-broke/)

And it really is not that much work!

*Follow the author as [@hiltmon](http://twitter.com/hiltmon) on Twitter.*
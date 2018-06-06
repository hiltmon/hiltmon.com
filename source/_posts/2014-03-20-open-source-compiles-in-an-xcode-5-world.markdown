---
layout: post
title: "Open Source Compiles in an Xcode 5.1 World"
date: 2014-03-20 12:21:04 -0400
comments: true
categories: 
---

So today I needed to work on an older, open-source based C++ application on my Mac and there was no way to compile it under Xcode 5 even though the development tools were installed and working perfectly.

The issue, it seems, is that Xcode 5.1 has finally removed and deprecated a lot of old C++ stuff that is still required by older, popular libraries such as `boost` and `quickfix`. It emulates `g++` 4.2.1 OK, but is no longer 100% compatible with it. I am quite sure that Apple and the Open Source community will eventually get these to work with the new compiler.

But I needed it **now**. And no end of futzing with compiler options and paths would work.

Fortunately, you can run Xcode 4 side-by-side with Xcode 5.1 on OS X Mavericks. And Xcode 4 comes with a real `g++` 4.2.1 which does contain the deprecated code and compatibility.

To get this to work, download Xcode 4.6.3 from Apple Developer downloads. Once downloaded, drag and drop the Xcode install onto your **Desktop** (not applications) and rename it `Xcode4`. *Then* drag the renamed application to your **Applications** folder. You now have Xcode 5.1 (named **Xcode**) and Xcode 4.6.3 (named **Xcode4**) side by side.

To make things easier, Apple has provided the `xcode-select` command to enable you to choose which Xcode install is the one used in system compiles or from the command-line.

To use Xcode 4 and the older `g++`, just select Xcode 4:

	sudo xcode-select -s /Applications/Xcode4.app/Contents/Developer
	
Running `g++ -v` gives me:

	Using built-in specs.
	Target: i686-apple-darwin11
	Configured with: /private/var/tmp/llvmgcc42/llvmgcc42-2336.11~182/src/configure --disable-checking --enable-werror --prefix=/Applications/Xcode.app/Contents/Developer/usr/llvm-gcc-4.2 --mandir=/share/man --enable-languages=c,objc,c++,obj-c++ --program-prefix=llvm- --program-transform-name=/^[cg][^.-]*$/s/$/-4.2/ --with-slibdir=/usr/lib --build=i686-apple-darwin11 --enable-llvm=/private/var/tmp/llvmgcc42/llvmgcc42-2336.11~182/dst-llvmCore/Developer/usr/local --program-prefix=i686-apple-darwin11- --host=x86_64-apple-darwin11 --target=i686-apple-darwin11 --with-gxx-include-dir=/usr/include/c++/4.2.1
	Thread model: posix
	gcc version 4.2.1 (Based on Apple Inc. build 5658) (LLVM build 2336.11.00)
	
To use Xcode 5 and the new LLVM/Clang `g++`, just select Xcode 5:

	sudo xcode-select -s /Applications/Xcode.app/Contents/Developer
	
Running `g++ -v` now gives:

	Configured with: --prefix=/Applications/Xcode.app/Contents/Developer/usr --with-gxx-include-dir=/usr/include/c++/4.2.1
	Apple LLVM version 5.1 (clang-503.0.38) (based on LLVM 3.4svn)
	Target: x86_64-apple-darwin13.1.0
	Thread model: posix

To simplify the process, I added the following to my `~/.bash_profile`:

	# Switch xcodes
	alias setxcode4="sudo xcode-select -s /Applications/Xcode4.app/Contents/Developer"
	alias setxcode5="sudo xcode-select -s /Applications/Xcode.app/Contents/Developer"

Now all I have to do is type

	setxcode4
	
Or

	setxcode5
	
And my password to switch environments.

With both environments installed and a quick command, you too can work on old code using the old `g++` compiler, and switch back to Xcode 5 and `llvm/clang` for newer projects.

*Follow the author as [@hiltmon](http://https://twitter.com/hiltmon) on Twitter and [@hiltmon](http://alpha.app.net/hiltmon) on App.Net. Mute `#xpost` on one.*
---
layout: post
title: "Xcode 4 Code Completion for External Build Projects"
date: 2013-07-07 21:53
comments: true
categories: [ programming, c++ ]
---

In [Xcode and the Simple C++ Project Structure](https://hiltmon.com/blog/2013/07/05/xcode-and-the-simple-c-plus-plus-project-structure/), I showed how to set up Xcode as your IDE for the [Simple C++ Project Structure](https://hiltmon.com/blog/2013/07/03/a-simple-c-plus-plus-project-structure/).

But one thing does not work, Code Sense. Xcode does not provide code completion or jump to definition for these projects.

Wouldn't it be nice if we could enable this too.

The solution is simple, you need to use the Xcode build system to create the indices that the IDE uses. But since we are working on cross-platform Makefile systems, we do not want to switch compilers.

The answer is to create a new target that uses the Xcode build tools, and add all your source `*.cpp` files to it. Xcode will now index these files. And you can simply ignore the new target and continue to build against the old Makefile-based target.

{% img /images/document-target.jpg 700 256 %}

To add this *documentation* target, click on the project at the top, then click the **Add Target** button. In this case, I chose a command-line tool. I like to name the new target the same name as the external target with a `-doc` extension. Then save it.

{% img right /images/target-membership.jpg 185 68 %}

The next step is to make sure each `.cpp` file gets added to the `-doc` target. One way to do this is to select the file and check that `-doc` target in the file inspector.

Unfortunately, Xcode has polluted our simple C++ project and created a new `main.cpp`, a `<name>.1` file and folder for this new target. We neither want or need these.

In the new `-doc` target, remove the **Copy Files** step from the **Build Phases** tab by clicking the `X` at the top right of this step. This frees us up to remove these files from the new target (uncheck them in the File Inspector) and delete them (choose Move to Trash when asked).

Any time you add a new file to the main project, make sure you add it's source to the `-doc` target. But never use the `-doc` target to compile the project, it will not work. However, if you ever need to reindex the project for some reason, performing a Clean and a Build on the `-doc` target will recreate the index.

Now we have a cross-platform external build C++ project that also takes advantage of Xcode's autocomplete and jump to definition features.

*Follow the author as [@hiltmon](http://twitter.com/hiltmon) on Twitter and [@hiltmon](http://alpha.app.net/hiltmon) on App.Net. Mute `#xpost` on one.*
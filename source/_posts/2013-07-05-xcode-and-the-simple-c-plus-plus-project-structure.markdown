---
layout: post
title: "Xcode and the Simple C++ Project Structure"
date: 2013-07-05 11:31
comments: true
categories: [ development, programming, c++ ]
---

In a previous post, I talked about a [A Simple C++ Project Structure](https://hiltmon.com/blog/2013/07/03/a-simple-c-plus-plus-project-structure/) that I am using to create a bunch of high-speed daemons for work.

It's been fun using TextMate 2 and a Terminal to `make` and run the project, but now that I am getting to the meat of the coding, I'd prefer to use an IDE to help me navigate and debug the code.

Here's how to set up Xcode 4 on the Mac to compile using our Makefile and run/debug the application.

*Note that since these projects already exist, there is a minor shenanigan involved in setup.*

## Step 1: Create an External Build System Project

{% img right /images/external-build-1.jpg 364 246 %}

Start Xcode and choose **File / New Project**.

Click on **Other** then choose **External Build System**.

Click **Next**.

{% img right /images/external-build-2.jpg 364 246 %}

Input your project name, I use the existing project's name so that the Xcode project file matches.

Then click **Next**.

Now you will save this project at the *root* of the Simple C++ project folder. Just select the project *root* and hit **Create**.

## Step 2: Move the Project File

The problem is this. If you has chosen the root of your Projects folder where the Simple C++ project resides, Xcode would have replace the simple project folder with a blank folder and its `*.xcodeproj` file. That's not what we want.

So instead, we chose the root of the project itself.

But Xcode has created a subfolder named after your project and placed the `*.xcodeproj` file in that. That's not what we want either. So lets fix it up.

Quit XCode.

Drag the `*.xcodeproj` from the subfolder and drop it on the project *root*. Now delete the subfolder.

Double-click the moved `*.xcodeproj` to open the project again in Xcode.

## Step 3: Add the sources

{% img right /images/external-build-3.jpg 280 299 %}

At the bottom left of the Xcode window, click the `+` icon. Then choose **Add files to "Your Project Name"**.

Select everything *except the `build` folder* and choose **Add**.

## Step 4: Test the Build

Click on the project at the top to see the Project and Targets panel. You should see an **External Build Tool Configuration** already setup to use the Makefile we had before.

{% img /images/external-build-4.jpg 700 136 %}

To build, press **⌘B**.

## Step 5: Run It

We still need to do one more thing and that is to tell Xcode which executable to run.

Under the **Product** menu, choose **Scheme** then **Edit Scheme..** or press **⌘<**.

{% img /images/external-build-5.jpg 700 475 %}

Click on **Run** in the left pane. The click on the drop-down next to **Executable** and choose **Other...**. Find the executable in the `bin` folder and click on it.

If you prefer, you can change the debugger to `GDB` as well.

To pass arguments to the default run, click the arguments tab and add them there.

Click **OK** to save.

Press **⌘R** to run, and Xcode will bring up a console window to display the program's output.

## Cool Benefits

Some cool stuff that comes along for free:

* If you press **⇧⌘K** (or choose **Product / Clean**), Xcode will run the `clean` target in the Makefile.
* The Xcode organizer imports and loads the `git` source code control environment so you can branch and commit from Xcode.
* You get a really nice GUI debugging environment (which was the real goal).

Also, don't forget to commit these changes when done.

Now we have a Simple C++ Project that can and will compile under Linux using command-line tools, and a GUI IDE environment to develop and test it on the Mac.

*Follow the author as [@hiltmon](http://twitter.com/hiltmon) on Twitter and [@hiltmon](http://alpha.app.net/hiltmon) on App.Net. Mute `#xpost` on one.*


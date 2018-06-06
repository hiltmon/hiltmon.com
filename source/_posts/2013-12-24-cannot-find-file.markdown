---
layout: post
title: "Cannot find File"
date: 2013-12-24 17:08
comments: true
categories: 
---

> "Can you please send me that file again? I cannot find it"

> "I'll have to get back to you, I don't know where I saved the file I need."

I hear this every day. Even now, in 2013, more than 20 years after hierarchical file systems became the core and the norm of computing, users still struggle to understand something as simple as knowing the location of their own files in their own computer systems.

I blame the complexity of the past and I have only seen one promising idea that has a way to go but may solve this issue.

## The Cause

The hierarchical file system is something that ordinary, non-geek users do actually understand, *once they get to it*. They do *get* the concept of folders and the concept of placing files in these folders. *The issue is in the complexity of finding the starting folder to work with.*

All current Operating Systems have an issue here.

Windows sucks because of drive letters. Instead of just giving users a clean file system like Unix, Microsoft followed the CP/M and MS-DOS model of assigning letters to disk drives, something that users struggle to comprehend. What the heck is `A:` vs `C:` vs `D:` vs `J:`? Before users can even think of which folder the file *may* be in, they need to think in terms of which drive letter may contain the folder. Yet some letters are CD Drives that cannot be written to, but which? Some are inscrutably empty, but which? Some only appear at work, but which? It's too confusing, so users give up and just let the system save where it wills, thereby losing any chance of finding the file later.

Unix sucks because of the `/mnt` file system. Instead of having inscrutable drive letters, users are faced with inscrutable paths. Worse, these mounts are usually *shared* between users on the same system. Which means that other user's mount points exist to confuse the current user. And even worse, ordinary users may have to use actual command-line commands to access files remotely, using tools like `scp`. Which means that before the user can get to the folder to start looking, they need to remember which computer, server or mount the folder is on. It does not end well.

And OS X sucks these days because of iCloud. Apple may have solved the `/mnt` mess with it's GUI display of volumes mounted on the desktop, then taken two steps back by introducing iCloud. Now the user has to remember which application (even *worse* than drive letter or mount path) that they used to create the darn document before they can figure out the folder in order to find the file. Assuming they even created the file themselves.

In short, there is too much for the user to know before they can even get to the file system to find files.

## The Workarounds

Search tools such as Spotlight on OS X or Windows Desktop search attempt to resolve this mess by indexing files on all available drives. But regular users do not name or label their files properly, or know how to phrase searches in a way that these engines can find what they need. So search engines may be good, but do not work as expected and are ignored.

Some users have worked around this using their email clients. If a file is in their *recent* emails, they can find it based on who sent it and when. Go beyond a few weeks, however, and it is lost there too.

Other users jam everything onto their desktops. Because that's the only place they can find things again. And wonder why their computers get so slow.

Document management applications do exist, but your average user does not have them. Web served file stores, like SharePoint or Google Drive all provide search and folders too, but again, most users don't even think to look there first.

Even the workarounds require more user effort.

## The Promising Option

In reality, the majority of computer users hit save, name the file and hope for the best, that they can find the file again whenever it is needed.

The current model requires them to make a bunch of decisions when saving: which drive, which cloud, which mount point, which server and then which folder. It's too hard and too confusing. So they don't. And I believe that they shouldn't have to make these decisions.

I believe the option that holds the most promise in my mind is the technology behind Dropbox. Imagine for a moment that the default save location, the documents folder, on every device on every Operating System was actually a shared Dropbox-like root folder. Then have the File Open and File Save dialogs all default to this starting point. All files, all user folders, all in one place. Which leaves only one concept for users to understand, folder trees, something they do get!

Add a new drive to your computer? It should invisibly enable more storage in this documents folder or show the folders it contains *as a folder*. Go to work? The shared folders you have access to should appear there, *as folders*. Heck, work from home and they should still be there (invisibly being routed over secure VPNs without user intervention).

From a user's perspective, all their folders and all the folders they have access to appear all in one place. As folders, with their files in them. So much simpler.

## How do we get there?

Most users do not have a Dropbox account, and will never get one. And old-school IT managers want people to use *their* server drives for saving, compliance, control and backups. And I know not of a Dropbox like sync engine that *just works* within companies and homes.

So, if Operating System vendors added a common sync framework, maybe even just buy Dropbox for its technology, then share it amongst themselves, it could work.

Imagine this.

A new user gets a company computer with the operating system of their choice. IT has already set up their corporate dropbox. All the user user needs to do is save and load files to their default documents folder and the network (Dropbox) takes care of sync, shared folders and backup. Corporate shared folders appear as user folders, with special icons.

At home, if the user gets a Time Capsule, server or networked drive, it can broadcast itself as a home documents/dropbox server. The first time the user's computer sees the device on the network, it asks if the user wants to back up to it and it then takes care of syncing documents to itself. All done. If users want to share files at home, they can set up a shared folder in their Documents folder and the dropbox-like home or work server takes care of routing.

From this perspective, all users have to do is open and save files in the default location in the folders they know. No need to think about drive letters, applications or mount paths. Just folders and files. And their data.

I believe the technology exists to do this, but sadly, we cannot make it happen. The Operating System vendors need to bring it into existence, integrate it into their offerings and make it seamless and accessible to users and network administrators alike, wrapping it in necessary security using the reliability of the Dropbox model. For users, it should "just work".

Here's hoping it will happen for regular users in 2014. It cannot happen soon enough for those that work with and support them. Then maybe "I cannot find a file" can go the way of the floppy disk.

*Follow the author as [@hiltmon](http://https://twitter.com/hiltmon) on Twitter and [@hiltmon](http://alpha.app.net/hiltmon) on App.Net. Mute `#xpost` on one.*
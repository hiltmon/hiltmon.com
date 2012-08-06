---
layout: post
title: "Mischief Managed: Google 2-Factor Authentication"
date: 2012-08-06 11:45
comments: true
categories: Mischief-Managed
---

***Mischief Managed** is a series of posts on tasks and technologies I use to maintain my computing environment. It’s part of what I do between projects. Try it out.*

I’ve been planning on doing this for ages, but no excuses, you should too.

And then this happened. Last week, Mat Honan got hacked hard (see [Yes, I was hacked. Hard.](http://www.emptyage.com/post/28679875595/yes-i-was-hacked-hard)). Someone gained access to his Apple ID, reset his other accounts and nuked all his computers. You should read his experience, resecure your accounts and start backing up too. *Aside: Ignore the comments, the haters simply embarrass themselves.*

I run both my personal email (@gmail.com) and work email (@noverse.com) on Google, and forward all other accounts to one of these. Between these two and my Apple ID, they are the most commonly entered passwords I use.

2-Factor authentication means that you need to input an additional key the first time you access a service from a new, untrusted device. Google provides this key via a SMS, a phone call or its Authenticator App. Think of it as the same as those key fob thingies you get from your bank with a number to input with your password. With 2-factor enabled, bad folks trying to log into your account will trigger factor messages but not have access to the codes, only you do.

Setting it up is easy, log in to Google like you usually do, click on the tiny arrow to the right of your avatar and click **account**. Choose the second item on the left sidebar, **Security** and hit the edit button next to 2-step verification. Google will walk you through the process of turning the service on.

But there is a problem, many applications like mail clients, mobile devices and third party software that does not use OAuth do not support 2-factor authentication. Google solves this problem by enabling you to create application specific passwords. I highly recommend you set these up now, while you are setting this up. In my case, I needed ones for Mail on my laptop, mail on my iPhone, mail on my iPad and GAget. I’ll need more for the desktop. Give each password a new name and Google generates a really hard password. All you have to do is type it in to the device, you’ll only need to do this once per application per device.

I also recommend getting the iPhone (or Android or Windows Phone) authenticator software and setting it up as the primary authentication device, and use your mobile SMS as secondary. It involves scanning a QR code on your screen and typing in a number. Simple, and the authenticator is on you at all times. Next time you try to login on an untrusted device, you just launch the authenticator to get the code you need.

For the *@noverse.com* email, I had one more step to make before I started. By default, Google Apps does not have 2-factor enabled. You need to log in to your Google Apps domain and enable it under advanced tools.

As a final safety net, in case you lose your phone too, Google offers a set of 10 predefined one-time use keys that you can use to recover. I recommend downloading these as text files and saving them on Dropbox, Evernote or somewhere where you can easily retrieve it without your phone.

It’s only a small thing, but one-time passwords and 2-factor authentication means that its less likely I’ll get hacked and suffer the same fate as Mat Honan.

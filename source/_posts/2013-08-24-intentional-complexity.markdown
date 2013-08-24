---
layout: post
title: "Intentional Complexity"
date: 2013-08-24 15:21
comments: true
categories: 
---

> John Duns Scotus' (1265-1308) book Ordinatio: "Pluralitas non est ponenda sine necessitate", i.e., "Plurality is not to be posited without necessity"

> William of Ockham's Razor, modern science version: "The simplest solution is often the best."

*Intentional Complexity* is a manufactured situation where product configuration and operation are intentionally made difficult. It occurs when a software vendor exposes all the innards of their products to systems operators and end users.

It's great for marketing to Managers and sales to CTO's, but it's rubbish for operations and business. In this post I will talk about what this is, why this is, how it comes to be, how this is bad for you and the fleeting signs of improvement that I am seeing.

But first, how does one detect it?

## How is Intentional Complexity Presented?

Just look any marketing for enterprise systems and you will see some classic CIO friendly phrases (which I shall translate for you):

* **Fully Configurable** - there are hundreds of settings you can change, but only a few combinations really work, we just don't know which.
* **Fully Customizable** - you can change how the system works using code (or pay us lots of money to 'mod' the system) and then you'll have to wait for us on each upgrade to create the 'mod' for that too.
* **Fully Featured** - we have so many features that you can use (and very likely will never need) in the product that we need lots of menus, toolbars, icons, fields and wizards just to get our heads around it, we have no idea how you will.
* **Integrates with any Product** - even more settings and parameters to enable you to integrate this system with others, where settings are visible for all potential integrations, and only a few settings really work.
* **Supports -INSERT LIST HERE- protocols** - if you think we have a lot of settings now, just wait until you see all the settings for all the protocols we support that you will never need or use but some small firm in Botswana needs.
* **Installation included** - The product is so complex that we could not create a setup program for it. You need specialists just to install it and to create the initial settings.

*If you buy a piece of software that can do anything, expect it to be able to do nothing out-the-box.* You will need to configure it, customize it, choose the features to use, set up your integrations and choose your protocols, and then, only then, will it *start* working. 

Software that can do anything is made intentionally that way, and is therefore intentionally complex to set up and use.

## What is Intentional Complexity?

So what does this really mean? Well, lets take something as simple as setting up a Wi-Fi network. All you really need is to set the network name, the access user name and a password. That's not complex at all.

But *nooooooo*, almost all Wi-Fi router setups also involve choosing frequencies (2.5GHz or 5GHz), channels (0-11), choosing protocols (B, G, N or a combination thereof), choosing the type of encryption of the password (WPA, WPA2, WP-SEC) and choosing the IP network range. That is some serious complexity. The router is fully capable of knowing which frequencies are better, which channels are less crowded, supporting the necessary protocols as and when they crop up, choosing the best encryption and making sure the network range does not conflict.

But the designers of the router have chosen *not* to make these decisions for the user, they have made it intentionally complex to force the user to make these decisions.

*I am not saying these decisions should be taken away from users, just that they should not be forced on users. An advanced user should still have the ability to access the complexity and change things. But a regular user, or lazy advanced user like me, should be able to do the least amount of work and still get it up and running quickly.*

## Why create Intentionally Complex Products?

There are a lot of reasons for complexity in products, including:

* Customers have different needs and if a vendor wants to sell its product to them, it needs to support those needs.
* Customers have different workflows and processes which require configurable flows within the product.
* Customers run different product mixes which requires complex integrations to be created.
* The problem the product solves may be complex, requiring complex interfaces.
* There may be thousands of users or millions of transactions, requiring complex webs of software and hardware to keep it all flowing.

Complexity in itself is not a bad thing when the problem space is, in fact, complex.

But why *intentionally* create complexity?

* One reason is the expectation that enterprise software needs to look and feel complex. Selling what looks like a simple product against a what-looks-like-complex product is hard.
* If you are selling your software for a lot of money, you want the customer to perceive they are getting value for that money. Intentional complexity makes your product look just that more expensive because it has just that more visible stuff in it.
* If you sell your software to professionals or experts, you think you need to give them all the power you can, which means exposing the innards of the product. That decision to expose the guts of the product intentionally creates intentional complexity.
* To encourage the vicious circle of training and sales. If you can train professionals to use your complex product, when they consult or change jobs, they will want to leverage that training for more money, leading to more sales. And customers who buy these products need these trained professionals to use these products. Cisco was very successful with this strategy with its IOS routers and certifications. So is Microsoft and Oracle and SAP. Their intentionally complex software requires certified professionals, and their certified professionals push their products.
* Simple image and exclusivity. People who understand and use intentionally complex software feel smug compared to the rest of us who do not. Just try getting a SAP or Certified Network Engineer to speak in normal, it just does not happen.

## How does Intentional Complexity even happen?

This is where is starts:

* Marketing wants to compete feature-for-feature with a competitor which means the developers need to intentionally add features just for marketing.
* Sales wants to sell to the largest audience which means selling the product to customers who have different needs, or may be in even different industries, requiring additional complexity in the product.
* Product design has no idea what they are creating so they create a product that does everything and hope something sells.
* Management hears an idea at the golf course and wants that added to the product.
* Customers who have no intention of buying say they *just have to have* a feature, so that gets squeezed into the product, just for a sale that will never happen.
* New business partners and vendors enter the market, requiring developers to create new interfaces for them, just in case a customer one day, someday, maybe needs them.
* Customers want new features to mod the product for their needs, leading to more and more settings and changes to the core product. And as they upgrade, these mods become core.
* Technology changes, protocols change and to remain relevant, the software has to support these new changes, while not losing support for old technologies and protocols.

But the main reason Intentional Complexity remains is this: **nothing gets removed.** Excuses range from the difficulty in removal to backwards compatibility to just-in-case to some random customer still uses this feature. Which means all current and future customers have to intentionally bypass this feature every time they use the system.

And then there is the straw-man argument that users should be able to use the product their way and systems operators should be able to set the product up they way they want, so the product should support that. The software should be un-opinionated. Just because users *can* set something up some way does not mean that they *should*. 

There is an army of certified professionals who run around setting things up the most complex way because they *can*, not because they *should* and not because that's the best way for the business. Staff and consultants want to create job security and Intentional Complexity used just right can guarantee that.

## Why is Intentional Complexity Bad?

Once again, in this post, I am not arguing that complexity is good or bad, just that Intentional Complexity is.

* Companies need certified and trained personnel to do what they need on the product. These people usually cost more and are harder to find.
* It takes a lot more time to set things up because systems operators have to go through all this complexity just to get it started.
* It takes an even longer time to figure out when things go wrong because the fault may lie in any of a hundred places or with different people or vendors.
* Once it's working, it encourages people to resist change because the complexity of the system makes change difficult or risky.
* It's confusing as anything as to how to get things done, how things are done, how things have been done and how things should be done. The too many choices that Intentional Complexity leads to difficulties in deciding what to do and how to set things up.
* It enables customers to continue to run their businesses using inefficient workflows and protocols which are supported by the intentional complexity of the system, instead of running optimized better workflows supported by a simpler, best-practices system.
* It requires a lot of time and effort to train staff to use the product.
* Users use a small portion of the product because it's too hard and complex to use other features, or the user simply has no idea the feature exists, it gets lost in all the Intentional Complexity. Consider something like MS Word which is an intentionally complex word processor where 99% of users use less than 5% of its features yet have to wade through 100% of its features to do so.
* And people start to base software and implementation decisions on myths and on institutional knowledge (which is basically just a memory of what worked at least once before) because these intentionally complex products do not indicate in any way what is better.

## Is anyone trying to be less Intentionally Complex?

Fortunately, there is light at the end of this tunnel. Cisco's incomprehensible iOS and CNE's have been replaced at the bottom and medium ends with very easy to use web interfaces on their routers. SAP has created a significantly simpler version of their product for smaller and medium businesses by removing thousands of unnecessary settings and complexities. Citrix has created an easier to use GUI for their Xen virtualization servers, hiding the complexity of their maddening command-lines.

But some have not. Microsoft continues to add Intentional Complexity to Windows server and management infrastructure. ISP's and colocation firms still need CNE's to get things going. Accounting products get more and more intentionally complex by the day. And the ultimate in intentional complexity, Bloomberg, remains the grand master.

## What can we do?

We, the users and the buyers and the writers of checks, have to start to demand simpler, easier to use systems and products. We need to demand routers that are self configuring, we need to demand the removal or hiding of unnecessary features in products, we need to adjust our own workflows and choose the simpler products that support those flows. We need to push our vendors into making the 5% of the product we do use into the best 5% of the product and to hide the rest. We need to standardize our interfaces and all write to the same integration formats.

We need to break the mindset that Intentionally Complex software is better than complex software where the complexity is hidden behind intelligent defaults or unnecessary complexity is removed.

We need to realize that we do not do things that much differently to everyone else and that all this intentional complexity required to support our perceived uniqueness is unnecessary in the product, bad for business and bad for all our users and partners.

Unlike Occam's Razor, the simplest solution may not be the best, but the most intentionally complex one is certainly always the worst.

*Follow the author as [@hiltmon](http://twitter.com/hiltmon) on Twitter and [@hiltmon](http://alpha.app.net/hiltmon) on App.Net. Mute `#xpost` on one.*
---
layout: post
title: "Don't Panic - Flashback Trojan"
date: 2012-04-12 10:05
comments: true
categories: 
---

Please read the following list in its entirety before acting:

* 600,000+ OS X Computers have been infected by the Flashback Trojan
* In percentage terms, that's more than the largest virus infection on Windows ever
* You should panic, the "running down a corridor screaming with your hair on fire" kind of panic
* You should download, install and run all the Flashback removal tools (Links: [here](http://download.cnet.com/Flashback-Removal-Tool/3000-2239_4-75700492.html?tag=mncol;txt) or [here](http://www.kaspersky.com/about/news/virus/2012/Kaspersky_Lab_Offers_Kaspersky_Flashback_Removal_Tool))
* You should buy and install at least one anti-virus package immediately, maybe two.
* You should ensure that the anti-virus package has the latest definitions, so run its updater over and over again
* You should sit and wait while it scans all your drives, feel free to continue to hyperventilate
* You must pay for the annual subscription to the AV vendor
* You are safe, and may now stop panicking
* **_Don't do any of the above. There's no point._**

{% blockquote Nicholas J Percoco, https://twitter.com/#!/c7five/status/191496387031085057 %}
We investigated >300 breaches in 2011. 100% used malware. 0% detected by AV on targets. In lab 25 AV engines detected 12%.
{% endblockquote %}

Didn't read the whole list before acting? Sigh.

In short, **don't panic**.

## The Facts

* **Macs can get viruses**. It's true. Macs are based on UNIX and open source products shared with the Linux world, these have vulnerabilities and therefore can be infiltrated. No matter how good Apple's engineers are, even their software occasionally has holes.
* **AntiVirus software protects against known threats**. Nope. Most AV software *finds* viruses *after* they have been installed, but does *not* prevent them from being installed in the first place. It's not protection, it's detection.
* **AV software will protect you from future attacks**. Nu-uh. The *next* attack will come from a new vector, through a new vulnerability that no-one knows about yet. Since the vector is unknown, the AV software cannot watch it and detect a virus that does not yet exist.
* **AV software prevents the propagation of viruses**. Hmm, used to. In the old days, like 10 years ago, most viruses propagated in Word files or as email attachments. AV software detects those and prevents you sending them on. But these days, the attacks come via the web, through unsecured ports, downloaded scripts, human actions or unknown software vulnerabilities. AV software does not prevent this kind of propagation.

## The Solution

Protecting yourself against virus attacks on a Mac is quite simple. This is what works.

* **Keep your Mac up to date**. Unlike the Windows world where software patches just as likely ruin your system as fix it, Apple's updates rarely, if ever, cause problems. Run software update regularly. They are always fixing vulnerabilities as they are discovered.
* **Don't run as the administrator**. Always use your own user account. By default on a Mac, your user is not the administrator (unlike Windows), but your password allows admin things to happen. Most Windows switchers seem to prefer making their user accounts into administrators, don't do it.
* **Never input your password in a dialog unless you know why**. In order to install anything on your Mac, OS X asks for a password. If you ever see the password dialog come up, stop, think, did you choose to install something? If so, proceed, else, do not. It's the same idea as locking the cockpit door being the only effective anti-hijacking process; if you don't let them in, they cannot take over.
* **Turn off sharing services you don't need**. By default, Macs have almost no ports open. If you turn on some of the sharing services, such as web browser, file shares or print shares, you open ports. Which increases the attack surface for new viruses.

That's it. Oh and don't panic.

I agree with most security experts, you don't need AV on your Mac unless you like the slowdowns and associated AV crapware. AV finds what may already exist, but will *not* prevent the next infection.  I've already covered this before in [Is Antivirus Software a Waste of Money?](http://www.hiltmon.com/blog/2012/03/05/is-antivirus-software-a-waste-of-money/). It bared repeating.

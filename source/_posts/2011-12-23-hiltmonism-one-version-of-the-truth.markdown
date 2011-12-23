---
layout: post
title: "Hiltmonism - One version of the truth"
date: 2011-12-23 10:52
comments: true
categories: Hiltmonism
---

Its not uncommon for different software systems in a company to contain the *same kinds* information as others. However, it is *very* uncommon for this information to be the *same* across all systems. Often the accounting system has different information than the trading system, for example.  Inventory systems often have different stock levels than sales systems.

The impact of this is that traders trade on what they know, accountants report profit on what they know, and sales happens on what they know. Since all have different information, none of them has the *correct* information.

These discrepancies eventually get noticed. Traders trade something they no longer have, accountants have numbers that are rejected by managers who know otherwise, and sales fail because the stock is not present. These hard to detect discrepancies get noticed, and the finger pointing, blaming, and yelling begins.

Most organizations are aware of this issue. The few that decide to do something about it usually kludge together some scripts and integration tools to move data between systems, to try to reconcile between systems, trying as best as they can to keep them in sync, or at least know when they are out of sync and use manual processes to fix it.  This 'glue' code is usually hard to write, hard to maintain and it's still hard to trace when data does get of alignment. Never-mind the cost of people and time to *maintain* these copies of the truth.

*There should be only one place and one place only in your entire suite of systems to add and edit a piece of information*, there should be 'one version of the truth'. At this single control point, the information should be checked and validated, traced and controlled, and this source of the truth should feed all other systems automatically. There should be no way to edit this truth in the other systems, so that the truth remains as such.

That way, everybody in the organization is working off the same page, and each responsibility is clear.

I learned this Hiltmonism from a clothing retail chain. They were having lots of problems matching inventory with point of sales as they were on different systems. So they redesigned the point of sales system to take in the inventory data. After that, they could only sell what the inventory system said (not what the point of sales system said) and any inventory changes could only be made in one place, *in the inventory system*.  With this 'one version of the truth', they all but eliminated their stock problems.

Of course, 'one version of the truth' is also quite risky. What if the truth is actually a bad piece of information, and this bad information flows to all other systems?  

In theory this is a huge problem, in practice, not so much.

In theory, all other systems report bad information, bad decisions get made on this bad information and business fail.  In practice, the bad data will either cause a later process to fail or a report to produce noticeably incorrect results, in which case the cause is easy to detect and correct, since you know where the truth comes from. In practice, you are always dealing with bad information, but if it's the best you have, you're making the best decisions. Usually though, a few unnoticed bad data points have no impact, so there is no real problem.  

The retailer I mentioned did have invalid information in their systems, especially where 'shrinkage' of stock was occurring, but the impact was negligible, and very quickly picked up.

I wrote an entire Hedge Fund trading platform that relied on 'one version of the truth'. Our error rates were the lowest in the industry by a country mile, and our support team was the smallest.

There should be *one version of the truth* in all systems in an organization. That way, all decisions are based on the same data, all processes predicated on the same data, all decisions use the same data and errors are easy to detect and repair, without playing the blame game.

If you have the same data in two systems, and one of them is not the source for the other, and the data in the other is not read-only, you have a problem. One version of the truth.
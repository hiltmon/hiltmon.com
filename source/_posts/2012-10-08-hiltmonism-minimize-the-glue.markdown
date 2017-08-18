---
layout: post
title: "Hiltmonism - Minimize the Glue"
date: 2012-10-08 15:19
comments: true
categories: Hiltmonism
---

Glue is bad. Too much glue and your systems and processes become rigid, inflexible and incomprehensible. In technology and in business, you need to minimize the glue.

Let’s start with a few definitions. Lets call a potential interconnection between two systems a **path**. An **interface** is code to import or export data from an application. Now we can define an **integration** as a process whereby data is pulled from one interface, travels down a path and is loaded into another interface. A **reconciliation** is the process of checking that the data that travels along paths matches in both systems. **Glue** are programs that implement integrations.

The common belief is that integrating ‘best-of-breed’ systems are good. You get the benefit of having the ‘best-of-breed’ system functionality for each function of your business with the ease of shared data and less reliance on a single vendor. In reality, you land up with a bunch of disparate systems, confusing support as vendors blame each-other, duplication of functionality, a massive amount of glue to share the data, a large number of reconciliation processes to ensure all is well and business decision making based on ‘gut-feel’ not trusted facts. And when the systems change, the glue has to, and that takes time and effort. And when the business changes, the glue has to as well.

I do believe that having the best systems for each part of your business provides great functionality, competitive advantage, flexibility and scaleability *for that part* of the business, and this is a good thing. The issue happens when you glue each part of the business to each and every other part of the business and land up with a lot of glue and a rigid structure. *I see this all the time.* If you could minimize which systems get glued together, you need less glue code to manage and change, fewer reconciliation processes and you gain more flexibility and scaleability for the business.

## The network effect

If you have two systems, A and B, then to glue them together, you need two integrations, four interfaces, one glue program, and one reconciliation process, as follows:

{% img /images/mimimize-the-glue-1.png 487 234 %}

Now add another system, C:

{% img /images/mimimize-the-glue-2.png 334 296 %}

Now you are up to 12 interfaces, 6 integrations, three glue programs and three reconciliation processes.

Add another system, D:

{% img /images/mimimize-the-glue-3.png 293 296 %}

Now there are 24 interfaces, 12 integrations, 6 glue programs and 6 reconciliation processes.

Add one more system, E, and the numbers get crazy:

{% img /images/mimimize-the-glue-4.png 301 296 %}

You get the picture. Ironically, looking at the growth as I have presented it, it’s *obvious* that there is too much glue, but in practice, I do see this all the time, often with more and more systems in the mix. The glue exists because users *may* need it or the business grew without a plan to minimize the glue.

## Minimize the glue

**The solution is to choose which systems to glue, and, where possible, apply only a single integration in each glue code, in other words, only send the data *one* way.** Choosing the glue becomes a function of choosing the single source of each data element, integrating only the paths that match business flow and moving official and necessary company reporting to the final destination systems only.

Let’s look at each.

If you have multiple systems with the same data in them, then integrating them such that this data flows in all directions between all these systems does not make sense. A change in any one system needs to be moved to all other systems, and reconciled to be sure that they are all the same and correct. But, if you select one of these systems to be the single, official or ‘gold’ source of the data, and *only make changes* in it, then you can push this data from the source system to all the destination systems. As long as the push program doesn’t fail, you can be sure they all have the same [version of the truth](https://hiltmon.com/blog/2011/12/23/hiltmonism-one-version-of-the-truth/) and so do not need to reconcile.

{% img /images/mimimize-the-glue-5.png 627 296 %}

If you have systems that work at the front-end of a business process, others that work at the middle and others that work at the back-end, integrate from front to back. In my experience, I have only seen a few areas where integrating back to front is necessary, and in those cases, only integrate a limited data set to keep the front-end systems in sync.

{% img /images/mimimize-the-glue-6.png 582 297 %}

Finally, when you need *integrated* reporting, take these from systems further back in the integration flow. It is this that usually trips organizations up and leads to too much glue. A user uses a system but wants to report data from it and other systems, so glue is written to enable this report. But another user, elsewhere in the business using a different system also needs a similar report, so glue is written to that system as well. Invariably, you now have a [one version of the truth](https://hiltmon.com/blog/2011/12/23/hiltmonism-one-version-of-the-truth/) issue in that, if unreconciled, these reports may differ significantly, leading to bad business decision making. The correct approach is to select *which* of these systems is further back in the business workflow, *which* has the most data fed to it, and to make *that* the ‘gold’ master for the report. You can email, portal or provide a client to the first user so they can see the same report from the chosen source.

That’s why I have a [Hiltmonism](https://hiltmon.com/blog/categories/hiltmonism/) to minimize the glue. Less glue means less to change when systems and the business changes, increasing flexibility and scalability. Less glue means less reconciliation needed which means people can spend their time performing business functions instead of reconciling. And less glue means keeping [one version of the truth](https://hiltmon.com/blog/2011/12/23/hiltmonism-one-version-of-the-truth/) in sync and correct is easier, leading to a common business understanding across the organization and better fact-based decision making.
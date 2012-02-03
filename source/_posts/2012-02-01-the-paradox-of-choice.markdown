---
layout: post
title: "The paradox of choice"
date: 2012-02-01 10:41
comments: true
categories: 
---

**People desire more choices, yet are unable to choose when the selection is greater, that is the paradox of choice.**

[Sheena Iyengar](http://www.columbia.edu/~ss957/), a professor of business at Columbia University, conducted an interesting study in 1995. She set up a display of 24 samples of jam for customers to taste, and every few hours, she switched to a 6 sample set. The results were astonishing: 60% of customers stopped to try the jams when the selection was large versus 40% when small; and 30% of those that stopped when the selection was small purchased a jam, versus 3% when the selection was large.

In short, more people were attracted to the greater selection, but 10 times more people actually made a choice when the selection was smaller.

{% blockquote New York Times http://www.nytimes.com/2010/02/27/your-money/27shortcuts.html %}
That study “raised the hypothesis that the presence of choice might be appealing as a theory,” Professor Iyengar said last year, “but in reality, people might find more and more choice to actually be debilitating.”
{% endblockquote %}

In a similar study, Surgeon Atul Gawande found that 65% of people surveyed said if they were to get cancer, they'd want to choose their own treatment. Among people surveyed who really *do* have cancer, only 12% of patients want to choose their own treatment.

### Too many choices in software

In software, we have the same disconnect between number of choices and user's ability to make those choices. Our users declare that they want extensive choices, but they rarely, if ever, make or change those choices. For example:

* The Mac has hundreds of choices in the System Preferences application, yet very few users ever venture in there and change them.
* Apple recently released a simplified version of its Wireless Router software that *removed* the advanced menu of choices from the application, and almost no-one noticed.
* Lots of software comes with customizable report writers. Very few customers ever use them, yet all RFP's require it. As an advanced tech geek user, I have only once in the last 12 years used one of these (and that was in [Billings](http://www.marketcircle.com/billings/) to customize the layout of my invoices).

### Letting the user decide

One of the key burdens of a Software Designer is to make decisions on behalf of users. What features and functionality to implement, how to structure it, what the flows should be. When software designers get stuck, a common pattern is to *let the user decide*, create choices for the user to make and implement the necessary features for each choice.

Each and every setting or option in your application preferences is a decision by the designer to *let the user decide*. SAP software used to have 22,000 of these. And users love this, they call your software customizable and seem more comfortable to buy it.

But there are some problems with this. First, you have to design and implement the functionality for each choice, which means more programmer time, testing time, integration time, debugging time and of course, cost.

Secondly, if the designer cannot decide what is the *right* or *best* way is, how is the user supposed to make that decision? Your *expert* user, the 3% of your user base, who understands the problem domain, and knows what they want, will make a choice and be done with it.  But your *regular* user will be just as stuck as the designer as to what choice to make, which of the 24 jams to choose. We designers solve for this by choosing a random default setting. Our users solve for this by assuming we did that on purpose (see [Almost No-one Changes Their Settings](http://www.hiltmon.com/blog/2011/11/27/almost-no-one-changes-their-settings/)), so they leave it alone.

*Letting the user decide* is the software equivalent of creating all 24 jam flavors, putting them on the shelf and assuming that users will be capable of choosing the right one. Evidentially, only 3% of them can. Its a cop-out.

### More Choices, Simple Software, Pick One

Users also want simple, intuitive software. If there is no choice on how do to something in your software, then that's all users can do. Try printing from your current application, or opening a file. You always get the same operating system dialog (unless you use Adobe products, of course). Users do not get to choose which print dialog to use, or which file browser, they always get the same (Adobe users excepted). Imagine if each time you wanted to save a file, you first has to say which file browser to use before you saved. It would make the software cumbersome to use and complex to implement since the developer has to support all different file browsers available. By using the Operating System supplied print and save dialogs, developers have removed choices and made the software simpler.

Lets take another example. I'm writing this post in [Byword](http://bywordapp.com/), but I could just as easily be writing it in [Microsoft Word](http://office.microsoft.com/en-us/word/). What's the difference? Well, [Byword](http://bywordapp.com/) has no toolbar, limited formatting and makes it easy to write. Microsoft Word has a ton of menus, ribbons, colored squiggly lines, page breaks, formatting options, change detection, stylesheets and the like, oh, and you can also use it to write. I launch [Byword](http://bywordapp.com/), and write, that's it ([Byword](http://bywordapp.com/) has already chosen the font, view and styles for me). But because of all the choices in [Microsoft Word](http://office.microsoft.com/en-us/word/), my usual process is to launch Word, choose a template, change the font and screen views to hide page breaks, check my stylesheet, and write, and format and write some more and format some more. [Byword](http://bywordapp.com/) is simple, [Microsoft Word](http://office.microsoft.com/en-us/word/) is complex, both enable me to write, but [Microsoft Word](http://office.microsoft.com/en-us/word/) forces me to make more choices as I go along. Hence, I prefer [Byword](http://bywordapp.com/) for writing.

It goes even further when I realize I use 80% of [Byword's](http://bywordapp.com/) functionality, yet less than 15% of [Microsoft Word's](http://office.microsoft.com/en-us/word/).

Note that I am not saying software should have no choices, that may be too few, and may make the software too simple to even do its primary function. For example, I also have a copy of [iAWriter](http://www.iawriter.com/), which is a writing application that has even fewer choices than [Byword](http://bywordapp.com/). Why not use that? Because [iAWriter](http://www.iawriter.com/) made too many choices for me making it harder for me to use (but not for a lot of other people).

### Is it not information overload in the 24 jam case?

I don't think so. In some cases, too many choices just overloads the chooser, if and only if the choices come with *too much* supporting information.

For example, as a new arrival in the USA I went to the local supermarket to purchase milk. Where I come from, milk comes in two varieties, whole and skim (the soy stuff is not called milk). In my local supermarket, I can choose from whole, skim, 1%, 2%, organic vs non organic, local vs interstate, fresh vs reconstituted, soy vs cow, pasteurized vs non, and from several brands. It's a multidimensional matrix of choices with many axes, and all I want is milk.

On the other hand, too many choices may come with insufficient information, the overload being the sheer number of choices. I recently had to choose a new healthcare plan, and all the plans I looked at had hundreds of options, yet most of those options offered were not explained. I had to call up the company and ask a whole bunch of questions just to understand a few of the options available. I picked a plan because the few options I did get explained to me sounded right, but I have no idea if its the *right* plan for me, or what I really purchased.

### So what about how the choices are presented?

If fewer choices are better, so the jam study proves, how come people still struggle to choose from a smaller selection? It boils down to how the information about each choice is presented, just like in the overload case.

If you want an iPhone in the USA, you have three choices, AT&T, Verizon, and Sprint. Seems a simple choice, pick a carrier, get the iPhone. Yet it is almost impossible to choose a carrier, because the carriers present their services in complex, incompatible and vague terms, make no promises, hide their restrictions and limitations and therefore leave the chooser in the dark as to what they are really getting. The chooser has insufficient information to make a choice, no way to get that information and has, therefore, no way to make the *right* or *best* choice for them.  Cable companies, airlines, electronics vendors and the like do the same. It gives the seller the power to persuade choosers versus giving them actual choices.

A whole industry has arisen to try to make these choices easier. [Kayak](http://www.kayak.com/), [Hipmunk](http://www.hipmunk.com/) and [Expedia](http://www.expedia.com/), for example, all exist to help people choose flights from the morass of airline data and deals, but even they cannot simplify it enough.

### Making choices easier

As a software designer, our first goal is to make the *best* choices for our users. If there is more than one way to present information, calculate a number or execute a process, we should choose one and implement only that one. Almost all of our users will be happy with our choices, and we'll only hear from the few who wish we made the other choice.

We also sometimes do need to offer the user a plethora of choices. It's how we present those choices and the supporting information we provide that will help users choose. For example, reports. Most systems have a reports section. Most systems have a lot of reports. And most systems rely on the report name to tell the user what the report does. But most report names on incomprehensible to users. What is the difference between an aging and a collections report, they both show overdue balances? If the designer added a 1-2 sentence blurb about what the report contains, and when to use it, users will be able to choose the right report quickly and easily. Otherwise, they will have to run heaps to find the one they want, or give up.

### The paradox of choice

The paradox of choice means our users want more choices, yet cannot choose between these choices. We need to find the balance between choices for users to make and the choices we make for them. If we get that balance right, we create happy users and brilliant software experiences.

References:

* [Too Many Choices: A Problem That Can Paralyze](http://www.nytimes.com/2010/02/27/your-money/27shortcuts.html)
* [More ideas from Iyengar](Customers given too many choices are 10x less likely to buy)
* [Customers given too many choices are 10x less likely to buy](http://sivers.org/jam)
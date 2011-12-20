---
layout: post
title: "The missing feature"
date: 2011-12-19 23:07
comments: true
categories: 
---

My new product seems to be missing a key feature. One that every client so far has asked about. They are almost incredulous that I do not provide it. Come to think of it, none of the software created in my career, that's 21 years folks, has ever had this feature. The feature I am talking about is *export to Excel* for users*.

No *export to Excel*? Am I nuts. What kind of software does not have an *export to Excel* function? You ***need** export to Excel*, don't you?

No you do not, you don't even want it.

<!--more-->

---

## So why not implement *export to Excel*?

Here are my reasons why I have never implemented this feature, and don't plan on starting to do it.

### Control and Traceability

The thing about Excel spreadsheets is that they fall outside the workflow as managed by the software. Take a screen, export to Excel, change some numbers, then present them *as if they came from the application*.  No-one knows that the numbers have been massaged. If the numbers were reported from the application directly, then we can trace the numbers back to see how they were generated and by whom. In Excel, there is no control or traceability.

### Lack of Quality

Applications, especially good ones, spend a lot of time checking and validating data. You know the results are good because the inputs are validated and the calculations are consistent. Humans are rubbish at this. Excel spreadsheets are notorious for having simple errors that are never found, such as `SUM` formulae that don't cover all the rows, incorrect formulae, fields that you think are calculated but have had their formula overtyped with a fixed number.  There is no guarantee of correctness or quality in a spreadsheet.

### Fraud

One of the reasons I chose to work on [Kifu](http://www.kifuapp.com) is that the incidence of fraud in community based organizations is pretty high, and *most* have no idea that it even happened. The reason? They run their communities on spreadsheets. Fraudsters fail to record deposits on spreadsheets so the organization has no idea they paid themselves. And its very hard to determine whether a numerical error on a spreadsheet was a fat finger, done by another person or was intentionally faked by the fraudster.

### Versions of the Truth

One common use of an *export to Excel* sheet is to extract some data and then pass it around for review.  The reviewers then all have a play and some may make changes to the data.  Yet other reviewers have no idea if the data is original or has changed. Since reviewers get their information from the spreadsheet and not the application, there exist now two versions of the truth, the application's version used by all systems and the spreadsheet version, used by all personnel. This causes all sorts of problems, especially when decisions are made based on the Excel version of the, er, truth.

### Manual labor

The purpose of software is to help people get what they need to do done. Its supposed to automate and improve, not support onerous manual processes. *Export to Excel* on the other hand facilitates these old manual processes, which become entrenched in the people part of the workflow. This hurts the business efficiency that the software was supposed to provide.

---

## Why then, do people want *export to Excel*?

Well, assuming they do not want it to commit crimes, why indeed?

### Because the software does not have a needed feature

This is the actual most common reason to implement *export to Excel*. The product people either don't know they are missing a feature or report, or do not wish to implement it, or have no idea the need exists because customers clamor for *export to Excel* without saying why, so they enable the unknown by giving users access to an *export to Excel* function.

The bad thing about this is that the product people are therefore *encouraging* all the above bad behaviors, instead of doing their jobs and implementing the features their users need. And since their users can do the missing function in Excel, there's no need for them to even *tell* the product people what needs to be done and changed.

Without *export to Excel*, users are forced to communicate their real needs to development, and better features emerge in the product.

### Because "I want it my way"

Some people are quite picky about how they want things presented, no matter what the cost or time to prepare. *Export to Excel* nuzzles up to these people and licks their cheeks. The product designer designed the screens and reports carefully to provide clear and correct information. *Export to Excel* comes along and enables people to get other people to do 'make-work' to get them the same information in a different format.

Without *export to Excel*, these people have to suck it up and work with the team.

### Because "I want to do it another way, or the way I used to"

One of the reasons organizations standardize on a software product for a workflow is to ensure that all personnel in that workflow do things the same, consistent way. *Export to Excel* allows people to bypass the controls and flow of the system and do things their own way, leading to all sorts of data mismatches, manual processes and untraceable mistakes.

Without *export to Excel*, people have to follow the proper process.

### Because there is no other way

I get this one a lot. The user looks me in the eye and says with a firm and confident tone that there is no other way to do something unless that data is in Excel. And you know what, they are absolutely right. For *them*, for *their* mindset, by *their* experiences, they cannot see any other way, so they must be right.

The reality is that there is always another way. That's what we software designers do, we find the better way, we know the better way, and we implement the better way.

Without *export to Excel*, these users feel they cannot get their jobs done, yet in reality, they can get it done better, faster and with less effort and stress if they just took the 5 minutes to learn the software and flow. It's up to us (and their managers) to educate them.

---

With *export to Excel*, systems encourage the loss of controls, enable multiple versions of the truth, facilitate fraud, entrench useless manual processes and limit the communication between customer and developer. Lose, lose and lose.

Without it, people learn the product, communicate with the developer to make the product better, and have a better time doing their jobs. Without it, organizations maintain the necessary controls, reduce error rates and truth conflicts, and run more efficiently and nimbly. Win, win and win.

And that is why I have never implemented this *export to Excel* for users, and don't plan on starting to do it.

---

**Footnote**: \* Seems some readers got confused. Saving data to Excel format for integration purposes is *not* what I am talking about here. This article is about making this feature available **to users directly**. Using the Excel format to send data from one system to another at another company is a common practice, one I have used for years in Hedge Fund software. It also happens to be the worst format to do this in, but the only one some IT departments seem to be able to handle. I spent many hours attempting to get them to disavow this terribly insecure practice, to no avail.
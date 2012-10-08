---
layout: post
title: "Export to Excel is a Red Flag"
date: 2012-09-29 15:57
comments: true
categories: 
---

As a developer, I often get requests from clients asking me if I could deliver them a spreadsheet using their data from their systems that contains X and Y and Z. As a maker of software products, I often get asked whether my product supports ‘Export to Excel’.

Most developers say *yes*, here is your spreadsheet and *yes*, the product has ‘Export to Excel’. My answer is different, it’s *sometimes* and *no*, and this is why.

## The issues with data in Excel

For some, the biggest issue with sending data in Excel is that they lose control of it. They have no idea where that data will go, who is looking at it, how it will be used, and more importantly, how it is changed. Software products themselves ensure that the distribution and availability of data is strictly controlled by their security models. Once its in Excel, it can go anywhere.

For others, the biggest issue is that it’s too easy to change data in Excel, either via intent or by accident. Data loses its consistency and accuracy as it is changed manually. When receiving data in Excel, how does the receiver know if the data is original or manipulated? How can they tell if its correct or faked? Systems ensure consistency, accuracy and traceability, Excel has none of these things.

Another issue is that sending data in Excel introduces manual processes into a business. People get use to getting an Excel extract, manually manipulating it and formatting it and using it and sharing it. And the receivers of the shared sheets get used to their own manipulations and uses. All of these processes start outside the normal business flow, but become the core manual business flow. And once entrenched, they are hard to change.

Which leads to a lesser understanding of the business and the user’s needs. If the core business team are unaware of the needs being fed by the manual Excel flows, they don’t know to update the systems or fix their processes, or even know that things are going wrong. *Once the data hits Excel, it’s like it left the building, and no-one knows what’s going on outside.*

With these manual processes and data in Excel, the systems teams will never know what their clients’ true needs are and systems never get updated to meet those needs. Yet they get blamed for not doing the right thing because the Excel process *is* needed. In short, it’s a massive business communication breakdown.

The reason you have a software product in the first place is to get away from all these issues.

## Outcomes of data in Excel

The not so hidden secret behind data in Excel is the error rate, leading to bad data, bad reports and terrible business decisions and outcomes (see a 2006 article in FT [Beware the perils of spreadsheets](http://www.ft.com/cms/s/2/53faff38-df5e-11da-afe4-0000779e2340.html#axzz1GjN3QxkL) for some examples). Error rates in manually changed Excel spreadsheets are high, and are difficult to detect. Accidentally changed cells, bad copy and pastes and incorrect formulae are not uncommon, but are commonly unknown. Excel spreadsheets have no testing or QA like systems do.

But data in Excel is often needed because the *darn* systems just don’t provide the right answers, so the workaround is necessary. The outcome though is that the Excel manual process takes over and the *darn* software never gets updated with functionality needed because the workaround works. Users are unhappy because the system does not work right for them and they have to perform all this manual work in Excel. So they stop talking to the developers!

Well of course the software can’t do it, the developers have no idea that the functionality is needed in the first place!

## When is data in Excel it useful?

I don’t want you to get the idea that exporting data to Excel is evil in some way. There are some very valid uses for data in Excel and it’s the best platform for these uses, such as:

* **One-off data analyses**, or to help define and understand a problem. Excel is a great tool to help someone analyze data to see if there is something there. End users can perform these analyses because they know how to use Excel. And if the analysis works out, it makes a great specification for a developer to test against.
* **Large scale, read-only formatted reports**. The problem with the standard PDF or printed page is that it’s often too small to present information to users and decision makers properly, the report is too wide, requires more tabs or even needs some kind of graphics. Excel is good for this, as long as you make the spreadsheet read-only so that then end users cannot change it.
* **Data interchange**. As a developer, there are many better formats like CSV, XML or JSON, but Excel has become the *de-facto* standard for regular people to share data with each other. As long as the sharing is not part of a standard business flow that can be automated, data in Excel is still the most common way to share, and its a good one. Data maintains it’s typing, structure and usability in Excel.

## So what do I do?

When asked to provide data in Excel to a client, I first ask a few questions. I want to know if this is a one-off request, why they need it, what information (not data) are they trying to find out, and how they are  going to use the data. In most cases, the request is because the client has a problem, has no way to solve the problem, so asks for data in Excel to see if that would help them get a better handle on it. A short conversation with a developer often leads to an easy system change that provides the answer. And if not, interacting with the developer over a few spreadsheets usually leads to a systematic answer, update or change.

And none of my products has a generic ‘Export to Excel’ function. They do produce specific Excel formatted documents for specific needs or interchanges. By *not* having this function, I find that clients and users come to me with problems that they cannot solve with the system as it is. Communication improves, collaborative problem solving ensues, and systematic solutions are created. The software gets better, the users get happier and none of the above issues occur.

So to me, the request for data in Excel is a *red flag*. Either the system is missing functionality that requires an Excel workaround, or there is a business problem that needs to be understood, or it’s a one-off. Only if it’s not systematic, or if it’s part of a automatable flow do I believe in releasing data in Excel format.

Take a look at what you do. If you spend your days opening spreadsheets and updating them, *you’re doing it wrong*. Get with the systems folks and get them to add the functionality to the software. If you rely on ‘Export to Excel’ from your systems to start a process, get the systems changed to implement the process instead, or buy one that integrates. You should only be using Excel to read complex reports, occasionally share data with other people or perform one-off analyses.

---
layout: post
title: "Minimal Project Management"
date: 2016-03-05 17:20:56 -0500
comments: true
categories: 
---

With my team starting to grow at work, its time to add some Project Management to our process. However, I do not want this to add any additional time, meetings or burden on them (or myself) and so all of the popular formal processes are no good for my needs.

In this post, I will outline the **Minimal Project Management** process, its steps and how it works. I will also cover the issues of change and interruptions. This process only works, however, because of the quality of my team.

## The Team

My team is a group of experienced, smart folks who know how to design, program and ship product. Most of all, they understand the business, its priorities (our one weekly meeting covers that) and how their deliverables will impact. And they know how to manage their own time, interruptions and schedules.

They do not need to be micro- or even macro-level managed, they do not need systems and tools to tell them what to do when, they do not need someone else creating stories, setting tasks and getting on their cases when things slip. They know how to manage themselves, how to figure out what is needed, how to communicate effectively, and how to get it done.

That’s why I hired them.

I can assign work and know it will get done, done right, done on time with minimal overhead. And I know they will communicate progress and issues as needed. They need almost no project management from me.

## Minimal Project Management

But as the team grows, so the number of projects and tasks that *can* be performed grows. When it was two of us, a quick conversation could cover all topics. When we grew to three, a weekly meeting and a single live-document sufficed.

Now we are five. Capacity is up. And the list of tasks and projects that can be tackled in parallel grows rapidly. I, as manager, need to stay on top of a growing mountain of this stuff.

This is when I level-up to **Minimal Project Management** as I have done on so many previous occasions.

**Minimal Project Management** consists of only a few steps (and one change process):

- Assignment and prioritization of work.
- A Statement of Work to define the task or project.
- A single weekly review of progress.
- A Management of Change process.

That’s all there is to it. The team gets to manage their own time. They know the priority and impact of the work, the dependencies, the business needs and their key deliverables as its discussed in the meeting. They know the standards expected of their work, the tests to run to be sure their deliverables are correct and the pressure we are all under.

That is, again, why I hired them.

Lets look at each component.

## Assignment and Prioritization of Work

As the manager of the group, it is my responsibility to determine what work is needed, what the priority of that work is and who will do it.

I do not do this alone.

The Management Team of the business meets weekly to discuss issues, plans, challenges and review strategy. It is at these meetings where I contribute that which tech is bringing to the flow. The Management Team agrees on business priorities, and I convert that into prioritized work for my team to perform.

My team meets weekly too, and one part of this meeting is a review of the current business and work to be done — so they see the big picture. They too advise on dependencies and priorities.

With all this advice and help, I can easily determine what work needs to be done first, what next, what can remain on-hold, and can assign work to the team.

It's not hard to determine what work implies a large, complex project and what work is small and easy. And there is no need for complex estimations or deadlines, we all know what’s at stake.

Each team member gets at least one large project and several smaller ones. This is intentional. There is much downtime on a single project as developers wait for data, people or dependencies. By loading each developer with several projects, they can work on another while waiting on one. Not only that, they can schedule their time to switch between projects to keep their work fun and interesting. It is my experience that developers with several projects “on the go” tend to mix-and-match their time and yet deliver and ship great code on time. Developers with nothing to do become disruptive or lazy.

Once work is assigned, each assignee is responsible for getting that work done. And they start with a Statement of Work.

## The Statement of Work

A Statement of Work (SOW) is a *short* document that defines the objective, tasks and deliverables of a task or project. It can optionally contain assumptions and dependencies, and it may have details added later (designs, appendices, sample data, notes). But in essence, it's a document that defines **what** needs to be done and how we know when it has been done.

My Statement of Work template is a simple [Markdown](https://hiltmon.com/blog/categories/markdown/) text document as follows:

    Kind: Statement of Work
    Title: <Task or Project Name>
    Author: Hilton Lipschitz
    Affiliation: <Company Name>
    Date: 2016-03-04
    Version: 0.1
    
    # SOW: [%Title]
    
    ## Overview
    
    <What is the objective/goal is of this work>
        
    ## Tasks
    
    <A list of the tasks to be performed — very high level, clearly written>
    
    ## Deliverables
    
    <The deliverables of the project, so we know when it is complete>

Optional additional sections are

    ## Dependencies
    
    <SOWs that need to be done first for this to be viable>
    
    ## Assumptions
    
    <Any assumption made in why this work needs to be done>

That’s all there is to it.

A good Statement of Work is less than one (1) page long, complex ones get to a massive 2 pages, never more. It limits the scope of work and defines the tasks to be performed and deliverables to create. It does not detail each task, merely adds them as simple checklist items to be sure they get completed along the way. It does not say **how**, **when** or **who** will do the work. The **how** is up to the developer, the **when** and **who** is up to me, the Project Manager.

Most importantly, **the person tasked to do the work writes the Statement of Work**, not the Project Manager, not the user, not some Business Analyst.

There are many reasons for this:

- The person doing the work needs to understand what needs to be done, what needs to be delivered, to whom and what is going on if they are to do it right. The best way *for others* to know if they have this knowledge and understanding is to get them to write the Statement of Work themselves and then review it.
- The writer of the document also takes ownership of the project. It’s *their* scope, *their* tasks, *their* deliverables to make, *their* problems to solve.
- The writer of the document usually starts with no assumptions. Asking an analyst or a user to write it leads to information missing because they *assume* the developer will know things. If the developer is writing it, they assume nothing.
- And honestly, it frees me up to advise, coach, discuss, approve and work on other things, taking on my own Statements of Work. I’d rather be programming too.

Once the Statement of Work is completed (and reviewed, filed and approved by me), the person starts executing the tasks and we move into a work and review phase.

## Weekly Review

Once a week, the team meets.

More than that and we’ll be interrupting their ability to get into the zone and work on projects, reducing their productivity.

The weekly meeting never goes beyond an hour. In it, we:

- Each update the rest of the team on the projects we are doing and their  progress.
- Discuss new potential work that has come up.
- Discuss any issues, ideas and changes that apply.
- Discuss any key interruptions and bugs found.
- Completed projects are closed.
- Any new assignments are handed out.
- And with the remaining time, we talk general technology and ideas, this being the part we like the best.

A weekly, semi-formal meeting does not mean we do not talk about work during the week. On the contrary, we are always discussing what tasks, documents and deliverables we are working on. If any issues arise, the team member goes to the people they need (especially me) to discuss, plan and resolve. While this is going on, the rest of the team is free to remain [in the zone](https://hiltmon.com/blog/2011/12/03/the-four-hour-rule/) and continue to deliver on their work.

## Dealing with Change

One thing you can always be sure of is that things change. The business changes, priorities change, even small project scopes change. Whether the change is external (Management, User) or internal (Tech Issues, Dependencies), the **Minimal Project Management** process needs to deal with it.

And I boil it down to two basic change types: Scopes change and Priorities change.

### Scope Change

In scope change, the tasks and deliverables of a project as documented in a Statement of Work change. Users may ask for more features “while you are at it”, or, as the developer learns more about a topic, the nature of the tasks and deliverables change — what we thought we needed when writing the Statement of Work does not match what we actually need.

Scope change is managed by versioning the Statement of Work. A new version is generated by the developer and reviewed by me. If the scope change fits priorities, I will approve it, and the programmer will start working off the changed SOW. If not, or if the work should be a separate task or project, then a new task is generated and put aside for the next weekly prioritization and assignment.

If the scope change *stops* work on that project, no problem, because each programmer in the team always has several “on the go”, and can switch to working on another in the mean time.

### Priorities Change

Like all programmers, I prefer to finish what I start. Given the limited scope of Statements of Work, this is usually and regularly achievable. But in the real world, priorities change.

This is where the manager needs to step in. Projects may need to be stopped mid-stream, with deliverables incomplete and undelivered, so that other projects can get some time and resource. Partial code branches need to be committed in case we return to this task. That’s all the team member needs to do, they then move on to other work.

I, on the other hand, need to track what was not done and why. I need to archive the SOW, with a note as to why it was stopped, by whom and when, and I need to be sure the partial work is safe. I usually add this information as a notes appendix to the document.

And, when the time comes, I can later assign this work back to the original programmer to continue and complete. Note that I rarely assign a SOW to anyone other than the writer of the SOW as they know best.

## Interruptions

One thing that does ruin the simplicity of **Minimal Project Management** is interruptions. Users find bugs and interrupt, folks ask questions and interrupt, systems fail and interrupt, or some urgent, must be done now, yes bloody now, the place is on fire, task interrupts.

This is where the caliber of the team kicks in and where, as manager, I need to be patient and understanding (and occasionally a hard case). The people I hire and work with expect interruptions, they are realists and are experienced enough. In most cases, they deal with the interruption and move on, managing their own time and getting back to their work, without anyone being the wiser or anyone else being interrupted (until the weekly meeting where these are discussed). 

If the interruption is a bigger thing, or happening to frequently, they make a judgment call and bring me in. Between the causer of the interruption, the programmer and myself, we’ll quickly discuss the issue. If it is something urgent, we’ll agree to perform the interruption, knowing work will be delayed, to get the interruption resolved. But if the interruption is a bigger issue, and it is up to me to determine that, then its also up to me to get the programmer back to work and the cause documented, scheduled for later resolution and interrupter satisfied — which means I need to be a hard case.

Mostly though, the team can and does deal with interruptions all day, and can still get their work done in spite of them.

## Delivery

When a task is completed and the deliverables shipped, I archive the Statement of Work. Often, I will add a Notes section at the bottom to discuss how the task went, who did it and any issues that we faced.

This library of archived projects helps me to assign work in the future. I can see who is good at what, and who needs to learn what. We as a team can learn from the issues of past projects how better to think about, document and plan future ones.

## Summary

So, as my team is growing, I am moving from a semi-formal weekly meeting to a semi-formal weekly meeting and Statement of Work **Minimal Project Management** model.

I will use the same task recording and prioritization tools as before. I will hold the same weekly meeting as before. But now each team member will be responsible for managing their formal Statements of Work and more formally communicating, managing and tracking change.

Yet we’ll remain the fast, nimble, and exceptionally productive tech team as always, doing what we do best, delivering systems that multiply our firm’s capabilities and competitive edges.

*Follow the author as [@hiltmon](https://twitter.com/hiltmon) on Twitter.*

---
layout: post
title: "Coding Style Standards in 2017"
date: 2017-03-05 12:25:52 -0500
comments: true
categories: 
---

I've been writing software for well over 30 years, I've spent well over my 10,000 hours and gotten rather good at it. And I still write to a very rigorous coding style standard.

**You're kidding right? Its 2017, code style guides are so *passé.***

Nope. I'm deadly serious.

### Get off my lawn

Some of us remember when coding styles were *de rigeur*. When you climbed off your commuter dinosaur and joined a coding team, the first document they gave you was the coding style guideline. It was a thick, three-ring binder that covered everything from naming, spacing, commenting, position of braces, white space rules, spaces or tabs and the line length rule.

And, when you tried to submit your first code, the code you were so proud of, the team destroyed you in review for not following their *stupid* guidelines. There you sat, knowing your code worked, wondering why these people were being so anal about spaces and where your effin brackets were and why you could not use the letter `m` as a variable name. "The code works, dammit," you thought to yourself, "what is wrong with these people!"

The reality was that these folks knew something we rookies did not. That it was easier for them to read, review and smell-check code written the way they expected than to try to decipher yet another programmer's conventions. It saved them time, saved them effort and allowed the pattern matching engines in their brains to take over to enhance their understanding.

Back then, **code quality depended on other people reading, reviewing, understanding and smell-testing your code. It was up to humans to see if things could go wrong, find the issues and get you to fix them before the system failed**. This was how the Apollo code was done.

The coding style guideline made that job a whole bunch easier.

### The Bazaar

The rise of open source, good semantic tools, formatters, linters  and rise of the code ninja, have led to the demise in many cases of the coding style standard.

Most open source projects are a hodgepodge of coding styles because there is no leader, no team-boss and no benevolent dictator. Some, like LLVM and Python, do have such a character, and therefore a style guide. Most do not.

Some languages, like `go`, have an opinionated style and provide a formatter. And some teams use formatters to make they code look "better".

And don't get me started on projects that intermix various open-source code-bases that uses conflicting styles. *Aside: generated code has to be excluded as it gets regenerated on each compile. I'm looking at you, Google protobuf!*

**The big issue is that code these days is less readable by humans, and is less frequently reviewed by humans**. Much code is written using a mishmash of open source code, pastes from StackOverflow and a bit pf programmer code. Paying homage to some random management mandated format using a tool does not improve the quality, readability and maintainability of the code.

### The great debates

Those of us who do care believe that our coding styles are the best. Of course we do, we came up with them. We use them daily. We find code to our style easier to read. Writing to our style is now a habit.

Bring in another programmer and the war begins. Arguments erupt on line lengths, tabs or spaces to indent, indent sizes, brace positions, early exit, and function lengths. Of course, the other programmer is wrong, their habits are bad, they are idiots and their code looks terrible.

The truth is that these arguments are stupid since no side is "correct". It's a taste thing, a personal preferences thing, a habit thing and sometimes a power play.

At the end of the day, **it really does not matter what you choose, as long as you all agree and all adhere to the agreement**. Win some, lose some, it does not matter.

What matters is being able to read, review, and fix each-others code with ease. And that requires a coding style standard.

### So why still standardize in 2017

Because:

- **Code is meant to be read, reviewed, modified and refactored by humans first, and compiled second**. Code written to an agreed style is way easier to for humans to process.
- **When not sure what to do or how to write something, the standard steps in**. When to switch from a long parameter list to a parameter object, how far you can take a function before refactoring to smaller functions, and where in the code-base to place a certain file are all decided by the style standard.
- **Naming in code is a nightmare**. Styles define how to name things, and what case to use, making it easier to choose the right name. Most importantly, the reader can jump to the right inference when reading a name in the code.
- We don't care who wrote the buggy line, blame is not what we do. **But everyone in the team should be able to read, diagnose and fix it**. If you want to find the fastest way to speed up maintenance times and bug detection times, write to an agreed style.
- The debates are over, we can start to form habits, and **we can all focus on writing great code**.

### So I guess you use an old standard?

Nope, we update ours every year. Most of the time it changes little. The original space vs indent vs line length stuff remains mostly the same. Those debates are over and the habits formed.

But languages change, language practices change, and these lead to changes in the standard. We learn more about our own code over time. Misunderstandings in naming inferences change the naming conventions, identified bugs lead to file layout changes and better patterns identified by team members get added. And old, unnecessary guidelines are removed.

For example, our 2016 standard added the requirement that single line block statements must be wrapped in braces in C++, so a heartbleed like issue would never affect us. It finally allowed the use of function templates now that our tools can handle them properly — and we programmers finally got a handle on them. It changed the file extension on all our C++ headers to ".hpp" because our compilers treated them differently. And it moved function parameter lists to their own lines in headers so we could improve header file commenting and document generation. Nothing earth-shaking, but still huge improvements to readability.

### So all code is to standard?

Yes, and no. All *new* code is to standard. We do not stop all work, go back and correct old code, there is too much of it and we have better things to do.

But, each team  member knows that if they *ever* need to touch, change or fix old code, they need to refactor to the new standard at the same time. We do not commit non-standard code. Over time, the old code changes to match the new standard.

### Ok, summarize this for me

- Code is meant to be read by humans first.
- Code written in an agreed style is way easier for humans to find, read, understand, diagnose and maintain.
- Moving to a new standard takes time to build the habit, but once it becomes a habit, writing to standard becomes just part of the flow.
- The standard needs to change as languages change, as programmers get better and as new members join the team.
- All new code is written to the latest standard, all code committed is to the new standard, all old code is refactored on touch.
- Coding style guidelines are just as important in 2017 as they were when we rode dinosaurs to work.

*Follow the author as [@hiltmon](http://twitter.com/hiltmon) on Twitter.*

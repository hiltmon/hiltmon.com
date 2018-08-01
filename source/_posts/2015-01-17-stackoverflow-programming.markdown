---
layout: post
title: "StackOverflow Programming"
date: 2015-01-17 16:11:13 -0500
comments: true
categories: 
---

StackOverflow Programming happens when much of the functionality of an application is copied and pasted from the code examples found on [StackOverflow](https://stackoverflow.com). Unfortunately, it's becoming the most popular and common programming paradigm amongst younger programmers, leading to (1) shockingly shoddy, bug laden, slow, incomprehensible, unmaintainable programs that work only once, and (2) to programmers who do not understand what they are doing, their work and how to solve problems.

For example[^1], one of my interns came into my office this week to see if there was a way to do dates and times easily in C++. Java and C# both have easy Date Times classes, he said, why not C++? I told him C++ was a low-level language, and to use `time_t` and the `std::chrono` libraries like all C++ programmers do. Off he went.

But he was back in a few minutes. He'd Googled the topic, seen how horribly complex the default C++ libraries were, *found no example code*, and had come into my office to argue for `boost::DateTime`. He had one and only one reason in favor of using `boost::DateTime` - that there was plenty of example code on StackOverflow for it.

This intern is smart, he's a master's level student. And `boost::DateTime` is a perfectly good library. But still he did not argue, or even consider:

* Why the standard C++ way was so low level?
* Whether `boost::DateTime` was better than `time_t`? Or Worse?
* What other DateTime libraries were out there?
* Why his code should use the same DateTime as all the rest of the code in the system.
* Why he should learn anything instead of copy and paste from StackOverflow and move on to the next step in developing the application.

I'm seeing this more and more. Junior programmers have grown up in the StackOverflow universe, finding answers in the form of paste-able code for any questions they may have on StackOverflow. Why should they learn, or understand, or take the time to figure out a solution when *an* answer is a Google search away?

{% pullquote %}
And lets be fair, us mentors, leads, managers and the business do not help here. We assume savant level programming skills when planning and assigning programming tasks and the only way to meet these insane deadlines is StackOverflow Programming. {" Google a solution, paste it in, move on. "}
{% endpullquote %}

The result is shoddy, badly performing, unmaintainable, inconsistent code that we cannot use in production and must rewrite. Whether it's the choice of tools to use, the libraries, the functions to implement features or otherwise, the result is code that delivers the results we need in a completely unsustainable way. And when there are bugs, and there invariably are, the poor programmer has no way to understand them, never mind fix them.

{% pullquote %}
I am not presenting the argument that all StackOverflow answers are bad, most are absolutely excellent. I have had occasion when stuck to be helped by and try to understand many myself. And the ones I have provided are awesome, of course. {" My point is that the StackOverflow examples are just that, examples, to help the reader view a sample and try to understand a potential solution to their problem. "} They are not intended as production-level code snippets, *but that is how they are being used.*
{% endpullquote %}

I do understand, especially as a programmer, that re-inventing the wheel is a waste of time. And that having to write low-level code is a drag when there are potentially simple copy and paste options available. But I also understand that code changes, requirements change, code needs to be maintainable and robust and performant (especially when writing real-time systems) and that production systems need to be well understood and stable.

StackOverflow Programming is great for quick and dirty, one-off programs and prototypes. But for long-term, stable, production-level applications, the programmer needs to understand their tools, language, libraries and the code they write so it can be maintained, evolved and supported.

{% pullquote %}
I love how people, myself included, have contributed to StackOverflow. And it has saved my bacon on many occasions. But we need to teach younger StackOverflow generation programmers that the answers they find there are just examples, nothing more. {" Examples that need to be understood, compared, evaluated and studied. "} Only then should the knowledge, understanding and skills gained be used in order to create stable, consistent, maintainable applications.
{% endpullquote %}

This way, we'll all get more. Better applications made by better programmers. And better examples on StackOverflow from better programmers for existing questions.

*Follow the author as [@hiltmon](https://twitter.com/hiltmon) on Twitter.*

[^1]: Names and details withheld, and the story adjusted, to protect the innocent.
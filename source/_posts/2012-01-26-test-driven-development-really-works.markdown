---
layout: post
title: "Test Driven Development Really Works"
date: 2012-01-26 11:09
comments: true
categories: Business
---

In 2008, Nachiappan Nagappan, E. Michael Maximilien, Thirumalesh Bhat, and Laurie Williams wrote a paper called [“Realizing quality improvement through test driven development: results and experiences of four industrial teams“](http://research.microsoft.com/en-us/groups/ese/nagappan_tdd.pdf) (PDF link). The abstract:

{% blockquote %}
Test-driven development (TDD) is a software development practice that has been used sporadically for decades. With this practice, a software engineer cycles minute-by-minute between writing failing unit tests and writing implementation code to pass those tests. Test-driven development has recently re-emerged as a critical enabling practice of agile software development methodologies. However, little empirical evidence supports or refutes the utility of this practice in an industrial context. Case studies were conducted with three development teams at Microsoft and one at IBM that have adopted TDD. The results of the case studies indicate that the pre-release defect density of the four products decreased between 40% and 90% relative to similar projects that did not use the TDD practice. Subjectively, the teams experienced a 15–35% increase in initial development time after adopting TDD.
{% endblockquote %}

In 2012, [Ruby on Rails](https://rubyonrails.org/) development practices assume TDD. I personally rely on tools like [rspec](http://rspec.info/) for writing tests and mocks, [factory_girl](https://github.com/thoughtbot/factory_girl) for creating objects, [capybara](https://github.com/jnicklas/capybara) for browser automation, [simplecov](https://github.com/colszowka/simplecov) for code coverage and [guard](https://github.com/guard/guard) for automating these tests.

As a result of using this methodology and these tools, I tend to agree subjectively with Nagappan et al:

* It does take more time to write tests. But a 15-35% increase in time seems excessive. Most tests are short, quick and simple to write. Using mocks and factories helps a lot.
* It takes no time to run them if you use a tool like [guard](https://github.com/guard/guard) that continuously monitors and runs them as they change. Add [growl](http://growl.info/) notifications on the Mac and you only need to pay attention when you see red.
* Tests help me write better code. Because thinking up and executing tests often shows up code defects early, and this is a very good thing. I often find myself writing a function that I think is great, then throw a few additional tests at it and find my logic or execution was flawed.
* My defect rates are much lower, just like Nagappan et al state. I think this is simply due to the use of TDD to identify and catch defects earlier in the process. And I get far fewer bug reports from Beta testers.
* I am no longer afraid to refactor mercilessly. The tests will tell me if the refactor breaks anything. This is probably the most important point. I *know* that its safe to change code, I *know* if the change affects other components and I can *see* where and how it does so, so I can *fix* it.
* I can *trust* the code base. No need to tiptoe around API's or functions. I can *trust* that calling an API or module will work, and that the tests will tell me if they break. I can *trust* the work of others because their tests work too.
* I seem to have found, empirically, that writing tests after the fact is just as fine as writing them before. The important thing is to *have* the tests, and to have good tests, to have tests that go after both expected and unexpected cases, outlier cases, failure modes and are in some cases ridiculous tests.
* It also helps when taking on legacy or other people's code to spend time writing tests to help you learn that code. Or at least trust that code by testing the components you use.
* Testing for 100% coverage does not seem to be all that worth it. Using my toolkit in Rails, I can test the workflow, UI and all models and business logic. In reality, getting 100% coverage on models and libraries pays off, but the UI and workflow stuff changes so much during development that the tests for that stuff get in the way.
* Adding tests for bugs found is another great way to document not only the bug but your bug checking and fixing process. You know something is wrong when a bug is found, tests can help you to corral it, and then be sure that it never happens again. Tests also ensure that your fix does not break anything else. I often find new bugs by fixing one bug and watching other tests fail.
* I don't release unless all tests are passing, *obviously*.
* I also don't skip testing to meet deadlines. I estimate with tests in mind, I develop with tests in mind. And if I have a deadline, the few minutes more it takes to create and run tests make no significant difference.
* I make no secret that I use this methodology. My clients understand that the small increase in development time pays off handsomely in later iterations, and reduces beta testing and maintenance issues. Based on my experience alone, TDD actually reduces the net time to develop and ship quality software because you don't spend time later in the project trying to figure out what went wrong.

For many developers, introducing Test Driven Development, is a challenge. You have to explain it to your team, to managers and clients, then find the time to write tests, then find the time to learn how to write good tests, build a process and infrastructure to automate testing, and the payoff is difficult to see until far later in the project timeline. I hope just some of the benefits I have found above help you get there.  With TDD, you will make better software, you will be a happier developer and your manager and client will see the benefit in the end.

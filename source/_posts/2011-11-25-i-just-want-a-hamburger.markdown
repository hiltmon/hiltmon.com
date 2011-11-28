---
layout: post
title: "I just want a Hamburger"
date: 2011-11-25 12:30
comments: true
categories: 
---

Or **too many choices lead to the inability to choose**.

In the USA, when one walks into a restaurant to eat a hamburger, one has to endure a full interrogation. *How would you like the burger cooked? Would you like cheese on it? What kind of cheese would you like? Would you also like bacon on it? Lettuce and tomato? Onions? Raw or Fried? Mayonnaise, ketchup, relish or mustard? Which kind of mustard? Do you want fries on the side? A pickle too? Sesame on the bun? Raw or toasted?*

Give us a break.  We want a hamburger, make by a professional in the making of hamburgers, and presented to us as the best mix of ingredients prepared properly that they believe makes a great hamburger.  We did not go in there to make choices, we went in to eat a delicious burger, pay and leave.

It turns out software users want the same thing.  Product, made by us, that satisfies their needs, without the options and choices and interrogations that make using it difficult, confusing and dissatisfying.

<!--more-->

Take a look at the TED talk by [Barry Schwartz on the paradox of choice](http://www.ted.com/talks/barry_schwartz_on_the_paradox_of_choice.html) (20 mins, flash required).  "In Schwartz's estimation, choice has made us not freer but more paralyzed, not happier but more dissatisfied."

In short, too many choices make it harder for us to decide what to do, make it easier for us to put off decisions because they are too hard (even if we lose significant benefits), and leave us dissatisfied when we do make one, because maybe another choice would have been better.

As developers, we often feel that a too-simple interface to a product offers less value.  As analysts, we feel that fewer features detract from the product's usefulness.  As designers, we try to meet the needs of all our customers, no matter how conflicting and confusing they may be.  As programmers, we're comfortable with complexity, and are happy to program up a large number of options.

And so we tend to offer too many choices to our users.  Like Microsoft did in Windows Vista:

{% blockquote Joel Spolsky, Choices = Headaches  http://www.joelonsoftware.com/items/2006/11/21.html %}
A total of fifteen different ways to shut down a laptop that you're expected to choose from.
...
iPods don't even have an on/off switch.
{% endblockquote %}

Anyone who has spent any time in usability labs has observed this problem.  Users, in a lab, when given a task, move their mouse over the list of choices, and hover above them trying to make the choice.  They do not click.  They stop.  They dither. They do not want to make the 'wrong' choice.  Wordpress gets it:

{% blockquote Wordpress http://wordpress.org/about/philosophy/ %}
Ultimately these choices end up being technical ones, choices that the average end user has no interest in. It's our duty as developers to make smart design decisions and avoid putting the weight of technical choices on our end users.
{% endblockquote %}

Just because we can expose a setting or function to the user with a few lines of code doesn’t mean we should.  We need to consider the impact of adding one more menu item or one more button to the UI before we do. It might be a simple line of code, but it could greatly impact our product.

And just because one user took the time to email us about a feature they want, doesn't mean we should add it.  It may be a lot of work, it may be little work, but the additional UI increases the number of choices for *all* of our users, many who won't even understand the new option but then have to deal with it every day.

It is our duty as developers to make the best choices for our users, to select the most useful defaults and to offer only the most necessary options.  It is our duty to make the best hamburger we can, and to stay of our customer's way while they eat and enjoy it.

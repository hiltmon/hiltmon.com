---
layout: post
title: "The 10 commandments of good source control management"
date: 2012-03-05 20:36
comments: true
categories: [Business]
---

Troy Hunt lists the [The 10 commandments of good source control management](http://www.troyhunt.com/2011/05/10-commandments-of-good-source-control.html) in his blog. I use [git](http://git-scm.com/) and [github](https://github.com/hiltmon) for *eveything*, including this web site and blog.

1. Stop right now if you’re using VSS – just stop it!
2. If it’s not in source control, it doesn’t exist
3. Commit early, commit often and don’t spare the horses
4. Always inspect your changes before committing
5. Remember the axe-murderer when writing commit messages
6. You must commit your own changes – you can’t delegate it
7. Versioning your database isn’t optional
8. Compilation output does not belong in source control
9. Nobody else cares about your personal user settings
10. Dependencies need a home too

{% blockquote %}
None of these things are hard. Honestly, they’re really very basic: commit early and often, know what you’re committing and that it should actually be in VCS, explain your commits and make sure you do it yourself, don’t forget the databases and don’t forget the dependencies.
{% endblockquote %}

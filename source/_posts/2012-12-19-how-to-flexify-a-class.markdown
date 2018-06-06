---
layout: post
title: "How to Flexify a Class"
date: 2012-12-19 13:19
comments: true
categories: [ Software, Design ]
---

OK, so you managed months ago to stop yourself from [Premature Flexification](https://hiltmon.com/blog/2012/12/19/premature-flexification/) when creating a class (or someone else did), but now the time has come to add features or flexify the existing feature set of the class.

There are many **wrong** ways to do this, and I have seen all of them in practice:

* Duplicate the existing class, rename it and add the flexibility to the new class. This sounds great as existing code remains unaffected, but sucks if a bug is found in the original and both need to be maintained.
* Wrap the existing class in a new class (or sub-class it), passing through the original methods, and adding new methods for the flexible class. Replace all calls to the original with the new wrapper or sub- class (or not!). This time, it seems that the maintenance problem above is dealt with, but the code base becomes crufty, and the workarounds in the wrapper start to break.
* Create a new class that has nothing to do with the original and write a new implementation. Great, now you have two problems.
* Extract the class implementation code into a new implementation sub-class, and default the original to use the extracted implementation class. Then create a new implementation class for the new flexibility version and add a method to the original class to enable you to change the implementation. This is why the suicide rate for Java programmers is so high.

Why do people do this? For a lot of *not very good* reasons. Some do it because they do not *own* the code, as in they did not write it or do not have permission to modify it. Some do it because they have no idea where the code is being used and are afraid to break something else somewhere else. Some do it because they think they can write a better class. And some do it because it is easy to be lazy and copy and paste code. And some do it because they just don’t have the time to do it right. And some just don’t care.

*Excuses, excuses, excuses.*

This is the path to the dark side of programming. In flexing classes incorrectly, the programmer is creating a maintenance nightmare, a more rigid and fragile product, and more cruft. It’s not worth it.

There is only one **right** way to do this:

* Document where the class is used
* Wrap the class in a test suite
* Make the necessary modifications
* Use the test suite to *prove* that all existing uses of the class will remain unaffected.

*That’s right, use [test driven development](http://en.wikipedia.org/wiki/Test-driven_development) and good old [refactoring](http://en.wikipedia.org/wiki/Code_refactoring) techniques to do it right.*

Finding where a class is used is not as hard as it seems. Just do a search through the code-base to find the class name. IDE’s and programmers editors have it built in. Or use a shell command like:

```
 find -type f -name "*" | xargs grep ‘<classname>’
```

If the class already has a test suite, check to make sure that all methods are tested for both success and failure conditions, and that the tests run and run correctly. If the test suite does not exist, take the time to write one. You’d be surprised how quickly you can do this after creating your first few. Test each method with a bunch of expected valid values, and a bunch of invalid values. Do a quick scan of existing uses to determine any edge cases. Then run the suite.

Now refactor the class, add the new features or add the flexibility. As you go along, keep running the test suite making sure the original tests continue to pass. Oh, and while you are at it, add tests for the new flexibility and features.

When the new flexibility has been added and you have a passing test suite, you can be sure that existing code will run with the new flexible class. The best parts of doing it right are that the existing code can now take advantage of the new class features, maintenance and cruft are minimized and you have the tools in place to come back and add more flexibility later.

But you are not done yet. Invariably adding flexibility adds dependencies, either meta-data files or artwork. Document the dependencies, so that future users of the class can find them quickly. Then walk through all uses of the pre-flexed class and ensure the dependencies are added and compile properly.

If you flex your classes properly, your code-base remains maintainable, your product does not become fragile and it becomes easier and easier to add features and flexibility in the future.

*Follow the author as [@hiltmon](http://https://twitter.com/hiltmon) on Twitter or [@hiltmon](http://alpha.app.net/hiltmon) on App.Net.*
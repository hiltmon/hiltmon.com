---
layout: post
title: "Simple C++ Testing with Catch in Xcode"
date: 2014-10-26 14:34:32 -0400
comments: true
categories: [development, programming]
---

{% img right /images/catch-logo-small.png 300 145 %}

[Catch](https://github.com/philsquared/Catch) is a simple, open-source, *dependency-free* unit testing framework for C++ projects. In this post I show you how to use it in a [Simple C++ Project](http://hiltmon.com/blog/2013/07/05/xcode-and-the-simple-c-plus-plus-project-structure/) from Xcode.

### Why Catch?

I am writing fast C++ libraries for work and need to wrap them in unit tests to ensure that they continue to operate and perform as they evolve. *My number one constraint is that these libraries must be dependency-free.* The only tools that I may use to compile or install these libraries on any platform (in my case OS X and Linux) is a C++11 compiler and a C++ standard library. Nothing else.

This dependency-free requirement precludes the use of excellent popular testing frameworks such as [Boost Test](http://www.boost.org/doc/libs/1_49_0/libs/test/doc/html/index.html) (a dependency), [cppunit](http://sourceforge.net/projects/cppunit/) (not up to C++11 yet), [google-test](https://code.google.com/p/googletest/) (uses a dylib or library depending on the platform) or XCTest (Xcode only and not C++).

[Catch](https://github.com/philsquared/Catch) is a single header only, dependency-free, lightweight testing framework that's perfect for my needs. It's simple to add to a project, simple to create tests cases and scenarios and simple to run. It also allows the user to run only a subset of tests using tags, which is really cool.

And that's why I chose it.

### Install Catch

Just include `catch.hpp` in a target and you're halfway there.

The `catch.hpp` file can be downloaded from [http://builds.catch-lib.net/](http://builds.catch-lib.net/). You can find the full source at [https://github.com/philsquared/Catch](https://github.com/philsquared/Catch).

### Sample Tests

Catch is well documented. I recommend you follow the [tutorial](https://github.com/philsquared/Catch/blob/master/docs/tutorial.md) for simple functional unit tests and how to use the product.  Since there is no point in me repeating how to write simple tests, go ahead and read through the [tutorial](https://github.com/philsquared/Catch/blob/master/docs/tutorial.md), and I'll wait until you return.

<span class="light">PLAYS ON-HOLD MUSAK</span>

Ok, back? Good. You have seen how simple it is to spin up a `TEST_CASE`, break it down into several `SECTION` elements and test results using `CHECK` and `REQUIRE`.

Lets do something more complex, lets test a sample class. This sample project is what I used to test Catch when I first saw it and helped me choose it.

First, the tests:

``` c++ test_sample_class.cpp
#include "catch.hpp"

#include "SampleClass.h"

TEST_CASE("Testing Sample Class") {
  SampleClass sc;
  
  SECTION("setting the str") {
    INFO("Using TestStr") // Only appears on a FAIL
    sc.setStr("TestStr");
    CAPTURE(sc.getStr()); // Displays this variable on a FAIL
    
    CHECK(sc.getStr() == "TestStr");
  }
  
  SECTION("test bigStr") {
    sc.setStr("TestStr");
    REQUIRE(sc.bigStr() == "TestStr : 7");
  }
  
  SECTION("Test doubles") {
    sc.setD(1);
    CHECK(sc.getD() == 1);
    sc.setD(1.0/3.0);
    CHECK(sc.getD() == Approx(0.33333)); // Nice
  }
}
```

In this example, we have a single `TEST_CASE` and three sections. Inside the `TEST_CASE` we instantiate the object and each `SECTION` tests a function in the sample class. Note that in the example, I arbitrarily switch between `CHECK` (no stop test) and `REQUIRE` (stop test), whereas in a real testing environment, I use them appropriately.

Here's the sample class that we're testing's header, it really is quite a useless class but gives us a range of things to try:

``` c++ sample_class.h
#include <string>

class SampleClass {
 
public:
  std::string getStr() { return _str; };
  void setStr(const std::string& s) { _str = s; };
  
  double getD() { return _d; };
  void setD(double x) { _d = x; };
  
  std::string bigStr();
  
private:
  std::string _str;
  double _d;
};
```

And its body:

``` c++ sample_class.cpp
#include "SampleClass.h"

#include <sstream>

std::string SampleClass::bigStr()
{
  std::stringstream ss;
  ss << _str << " : " << _str.length();
  return ss.str();
}
```

### Testing In Xcode

{% img right /images/catch-tests.png 255 276 %}

I setup testing in Xcode using a separate tests folder and a second tests target and scheme. In this sample case, the main project code is in the  `SampleProject` group (usually a library project) and the test target code is in the `TestSampleProject` group. This group (and its matching file system folder) are automatically created when you add an Xcode command-line target.

To create this target, select the project at the top and click `+` or choose **File** \ **New** \ **Target** from the menu, choose **OS X** \ **Application** \ **Command Line Tool**, choose `C++` as the language and give it a name.

I then add `catch.hpp` and edit the `main.cpp` file. The `main.cpp` in the test target uses the default Catch main function, there is no point in writing my own:

``` c++ main.cpp
#define CATCH_CONFIG_MAIN  // This tells Catch to provide a main() - only do this in one cpp file
#include "catch.hpp"
```

I also add the following command-line options to the test target scheme and toggle when needed:

{% img right /images/catch-command-line.png 313 120 %}

- `-r console` sets up readable console output (not necessary but a good reminder)
- `-d yes` shows the time taken on each test (usually disabled)
- `s` verbosely displays tests (usually disabled)
- You could also add any test tags you want to run as an option, but I find most of my test projects run sufficiently fast that I usually leave this out and run all tests. *It also protects me from forgetting to run the full test suite.*

I then start to add `.cpp` files for each test case and write my tests.

{% img right /images/catch-include-target.png 197 96 %}

Finally, you also need to add each class that is being tested to the Test target as well or it will not compile.

Running the test target delivers the following console output *on success*:

``` plain
===============================================================================
All tests passed (8 assertions in 2 test cases)
```

If any test cases fail, you get:

``` plain
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
TestSampleProject is a Catch v1.0 b53 host application.
Run with -? for options

-------------------------------------------------------------------------------
Testing Sample Class
  test bigStr
-------------------------------------------------------------------------------
/Users/Hiltmon/Projects/Spikes/TestCatch/TestSampleProject/testSampleClass.cpp:13
...............................................................................

/Users/Hiltmon/Projects/Spikes/TestCatch/TestSampleProject/testSampleClass.cpp:26: FAILED:
  REQUIRE( sc.bigStr() == "TestStr : 8" )
with expansion:
  "TestStr : 7" == "TestStr : 8"

===============================================================================
test cases: 2 | 1 passed | 1 failed
assertions: 8 | 7 passed | 1 failed
```

Correct the failures. Then add more tests. Run. Iterate, iterate, iterate. You know how to unit test.

### Sample Project

You can download the sample project to see how it works from [here](http://hiltmon.com/files/TestCatch.zip).

### Experience

I have been using [Catch](https://github.com/philsquared/Catch) for several weeks now in multiple C++ projects and it's been wonderful. Setup is easy, adding test cases is simple, running tests is a keystroke away and evolving my core dependency-free libraries is easier and more reliable than ever.
 
My thanks to [Phil Nash](http://www.levelofindirection.com) ([@phil_nash](https://twitter.com/phil_nash)) for creating and maintaining this wonderful tool.

*Follow the author as [@hiltmon](http://twitter.com/hiltmon) on Twitter.*


---
layout: post
title: "Testing C++17 Projects in Xcode with XCTest"
date: 2019-02-09 13:55:39 -0500
comments: true
categories: 
---

The vast majority of development I perform is in C++17 on an Apple Mac Computer using Xcode. For a while now, I have been using [Catch2](https://github.com/catchorg/Catch2) as my Unit Testing framework, and its absolutely excellent. But its not integrated into the Xcode IDE and I wanted the ability to use Xcode's excellent testing and test debugging tools to improve my productivity and workflow.

In this post I will show you how to set up a simple standard C++17 library project in Xcode 10 and then add XCTests to it.

<span class="light">You can find and download the sample project from Github at [HiltmonLibrary-with-XCTest](https://github.com/hiltmon/HiltmonLibrary-with-XCTest).</span>

<!-- more -->

## Setting Up the Library

### Create the Project

I am going to start with my standard, designed for cross platform, C++17 library project. In a terminal, lets create the folders needed:


	cd Projects
	mkdir HiltmonLibrary
	cd HiltmonLibrary/
	mkdir -p doc include/hmlib src test
	touch README.md
	git init

<span class="light">NOTE: `hmlib` above is the namespace I will be using for the standard library project.</span>

Now we will create the Xcode Project:

{% img right /images/hmlib-01.png %}

- In Xcode, choose **File** / **New Project**.
- Select **macOS** at the top, then **Library** and click **Next**.
- Fill in the project details, choose **C++** and click **Next**.
- Select the Project Folder we just created, then click **Done**.
- Close the project Xcode window. Do this because we need to move some files around.

{% img right /images/hmlib-02.png %}

The next two steps clean up that which we just created:

- In Finder, go to the Project Folder.
- Drag and drop the `*.xcodeproj` up a level, then delete the new folder (`HiltmonLibrary` under **HiltmonLibrary**).
- Double-click to open the project in Xcode.
- {% img right /images/hmlib-03.png %} Right-Click on the red folder and select **Delete** to remove the Xcode created folder and files.
- Right-click on the Project (at the top of the tree) and select **Add files to "HiltmonLibrary"...**.
- Press `CMD-A` to Select all, then click **Add**.

The standard library template is almost ready.

{% img /images/hmlib-04.png %}

### Update for C++17

Lets make it C++17 compliant, add extra warnings and expose inline methods from the library:

- Click on the Project Name at the top to see the project settings panel.
- Click on **Build Settings**, then type `C++` in the search box. Change the **C++ Language Dialect** to `C++17 [-std=c++17]`.
- Search for `Inline` and change **Inline Methods Hidden** to `No`.
- Search for `Other Warning` and double-click to the right of  **Other Warning Flags**. Click `+` to add the following flags:
	- `-Wall`
	- `-Wextra`
- {% img right /images/hmlib-06.png %} Search for `Search` and double-click to the right of **Header Search Paths**. Click `+` to add the following flags:
	- `$SRCROOT/include/hmlib`
	- `/usr/local/include`
- While there, double-click to the right of **Library Search Paths**. Click `+` to add the following flags:
	- `/usr/local/lib`

If you clear the search, and select **Customized** at the top, you should see something like this:

{% img /images/hmlib-05.png %}

### Add Project Code

And finally, lets add our first items to test. We'll create a utilities namespace to host some string manipulation functions to test:

- Right-click on the `src` folder and choose **New File** or select the `src` folder and hit `CMD-N`.
- Choose **C++ File** and click **Next**.
- {% img right /images/hmlib-07.png %} Create the C++ File, in this case `string_utilities`, make sure create header file is checked, and click **Next**.
- Make sure it goes in the `src` folder and that the target is checked (in my case `HiltmonLibrary`, and click **Create**.
- Finally, drag and drop the `.hpp` file under the `include/hmlib` folder.

{% img /images/hmlib-08.png %}

Ok, lets create some code to test, say a function that converts a string to lowercase.

In `string_utilities.hpp`:

``` c++ string_utilities.hpp
//===------------------------------------------------------------*- C++ -*-===//
//
//  string_utilities.hpp
//  HiltmonLibrary
//
//  Created by Hilton Lipschitz on 2019-02-09.
//  Copyright © 2019 Hiltmon.com. All rights reserved.
//
//===----------------------------------------------------------------------===//

#ifndef hmlib_string_utilities_hpp
#define hmlib_string_utilities_hpp

#include <algorithm>
#include <string>

namespace hmlib::utilities {

  /// @brief Copy a string to a lower case string
  /// NOTE: The copy is intentional
  std::string toLower(
    const std::string& sourceString
  );

} // Namespace hmlib::utilities

#endif // hmlib_string_utilities_hpp
```

In `string_utilities.cpp`:

``` c++ string_utilities.cpp
//===------------------------------------------------------------*- C++ -*-===//
//
//  string_utilities.cpp
//  HiltmonLibrary
//
//  Created by Hilton Lipschitz on 2019-02-09.
//  Copyright © 2019 Hiltmon.com. All rights reserved.
//
//===----------------------------------------------------------------------===//

#include "string_utilities.hpp"

namespace hmlib::utilities {

  std::string toLower(const std::string& sourceString)
  {
    std::string destString = sourceString; // Copy Mutable
    std::transform(destString.begin(), destString.end(),
      destString.begin(), ::tolower);
    return destString;
  }

} // Namespace hmlib::utilities
```

Compile with `CMD-B` and the library should compile OK. If you expand the `Products` folder, you should see the compiled library. *Note that a bug in Xcode 10 means that you may need to restart Xcode for it to stop showing as red.*

## Setting Up the Tests

Great, we have an awesome library, how do we go about testing it?

### Create and integrate the Test Target

{% img right /images/hmlib-09.png %}

- Press `CMD-6` to show the Test Navigator (or select the icon to the right)

{% img right /images/hmlib-10.png %}

- At the bottom, click the plus and choose **New Unit Test Target...**
- I prefer to make a strong name for test targets, so I named mine `TestHiltmonLibrary`.
- Make sure `Objective-C` is selected as the language and that the test target is your library (in my case `HiltmonLibrary`)
- Click **Finish** to create the target

Xcode helpfully shows you the new Target configuration page. 

### Update for C++17

Lets bring it up to C++17 standard (same as for the main library project):

- Click on **Build Settings**, then type `C++` in the search box. Change the **C++ Language Dialect** to `C++17 [-std=c++17]`.
- Search for `Inline` and change **Inline Methods Hidden** to `No`.
- Search for `Other Warning` and double-click to the right of  **Other Warning Flags**. Click `+` to add the following flags:
	- `-Wall`
	- `-Wextra`
- Search for `Search` and double-click to the right of **Header Search Paths**. Click `+` to add the following flags:
	- `$SRCROOT/include/hmlib`
	- `/usr/local/include`
- While there, double-click to the right of **Library Search Paths**. Click `+` to add the following flags:
	- `/usr/local/lib`

And to standardize the project:

- Drag and drop the `Info.plist` and `TestHiltmonLibrary.m` file to under the `tests` folder.
- Delete the **TestHiltmonLibrary** folder.

The reconnect the `Info.plist`

- Click on the Project name in the Project Navigator, and choose the test target.
- Change the **Info.plist File** entry to `test/Info.plist`.

{% img /images/hmlib-11.png %}

### Integrate with the Main Library Project

And finally, hook it all up:

- Click on **Product**, **Scheme**, **Edit Scheme...**, right-click on the scheme in the tool bar and choose **Edit Scheme**, or press `CMD-<`.

{% img right /images/hmlib-12.png %}

- Make sure the scheme selected is the Library scheme (`HiltmonLibrary`), not the Test scheme (`TestHiltmonLibrary`) in the top left of the sheet that shows up.
- Click on **Test** on the left.
- Click the plus at the bottom to add a test target and choose the test target (now add `TestHiltmonLibrary`).
- Click **Close** when done.

Lets Compile and Run the tests to see what happens. Press `CMD-U`. Xcode will:

- Compile the main Library
- Compile the test Target
- Run the tests
- Switch you to the Test Navigator

Since no tests have been created, it should have no failures.

{% img /images/hmlib-13.png %}

Thats it, the hoops have been jumped through to set things up. From now on, all you need to care about is developing your project code and your new tests.

## Adding The First Tests

Let's add our first C++17 tests.

Rename the default file `TestHiltmonLibrary.m` to better reflect the tests being run, in this case we're testing our String Utilities, so rename it to `TestStringUtilities.mm`

**NOTE THE FILE EXTENSION CHANGE FROM `.m` TO `.mm.` This is the secret, it tells Clang to compile the file as Objective-C++ which is how we get XCTest to talk C++.**

- Include the header of the class being tested

``` c++ TestStringUtilities.mm
#include "string_utilities.hpp"
```

- Remove the current functions and add the test function

``` c++ TestStringUtilities.mm
- (void)testCaseChanges {

}
```

**FOR XCTEST TO WORK, THE FUNCTION MUST START WITH `test.`**

- Add the test code:

``` c++ TestStringUtilities.mm
  std::string upper1 = "HILTMON.COM";
  XCTAssert(hmlib::utilities::toLower(upper1) == "hiltmon.com");
```

The `XCTAssert` macro is used to evaluate an expression and pass if `true`.

The final file should look like:

``` c++ TestStringUtilities.mm
//===---------------------------------------------------------*- objC++ -*-===//
//
//  TestStringUtilities.mm
//  TestHiltmonLibrary
//
//  Created by Hilton Lipschitz on 2019-02-09.
//  Copyright © 2019 Hiltmon.com. All rights reserved.
//
//===----------------------------------------------------------------------===//

#import <XCTest/XCTest.h>

#include "string_utilities.hpp"

@interface TestStringUtilities : XCTestCase

@end

@implementation TestStringUtilities

- (void)testCaseChanges {
  std::string upper1 = "HILTMON.COM";
  XCTAssert(hmlib::utilities::toLower(upper1) == "hiltmon.com");
}

@end
```

{% img right  /images/hmlib-14.png %} Press `CMD-U` to run the tests. Xcode will run the tests and put a bezel up that tests have passed and puts a green checkmark next to the test functions that passed.

Lets create a failing test:

- Add to the `testCaseChanges` code:

```
  std::string lower1 = "hiltmon.com";
  XCTAssert(hmlib::utilities::toUpper(lower1) == "HILTMON.COM");
```

And press `CMD-U`. Xcode compiles the tests and fails because the `toUpper` function has not yet been written. As expected.

Lets add it:

- In `string_utilities.hpp`, add:

``` c++ string_utilities.hpp
  /// @brief Copy a string to an upper case string
  /// NOTE: The copy is intentional
  std::string toUpper(
    const std::string& sourceString
  );
```

- In `string_utilities.cpp`, add:

``` c++ string_utilities.cpp
  std::string toUpper(const std::string& sourceString)
  {
    std::string destString = sourceString; // Copy Mutable
    std::transform(destString.begin(), destString.end(),
      destString.begin(), ::toupper);
    return destString;
  }
```

Ok, lets test again. Press `CMD-U`. Tests succeeded.

## Adding More Test Targets

Lets add another class to test. But this time, lets make it header-only so under normal circumstances, the library compiler will ignore it.

- Create `numeric_utilities.hpp` (Header File only) under `include/hmlib` as:

``` c++ numeric_utilities.hpp
//===------------------------------------------------------------*- C++ -*-===//
//
//  numeric_utilities.hpp
//  HiltmonLibrary
//
//  Created by Hilton Lipschitz on 2019-02-09.
//  Copyright © 2019 Hiltmon.com. All rights reserved.
//
//===----------------------------------------------------------------------===//

#ifndef hmlib_numeric_utilities_hpp
#define hmlib_numeric_utilities_hpp

#include <iostream>
#include <cmath>

namespace hmlib::utilities {

  /// @brief Generate a static round function at compile time to get
  /// a given precision. Not bankers, relies on C++ round.
  template <int precision>
  double roundTo(double value) {

    static_assert(precision > 0, "Precision must be > 0");

    double factor = std::pow(10.0, static_cast<double>(precision));
    return std::round(value * factor) / factor;
  }

} // Namespace hmlib::utilities

#endif // hmlib_numeric_utilities_hpp
```

Since this is a header-only file, the compiler will pretty much do nothing with it when building the library. So let's add a test to get it to compile and see it this mad round code works.

- Go to the test Navigator. Click the plus and choose **New Unit Test Class...**.
- Name it `TestNumericUtilities.mm`. **REMEMBER the `.mm` extension to get C++**.
- Clean it up and make it ready for the test.
- Include the header file `#include "numeric_utilities.hpp"`.
- The add a test function and some test Asserts.

The file will now look like this:

``` c++ TestNumericUtilities.mm
//===---------------------------------------------------------*- objC++ -*-===//
//
//  TestNumericUtilities.mm
//  TestHiltmonLibrary
//
//  Created by Hilton Lipschitz on 2019-02-09.
//  Copyright © 2019 Hiltmon.com. All rights reserved.
//
//===----------------------------------------------------------------------===//

#import <XCTest/XCTest.h>

#include "numeric_utilities.hpp"

@interface TestNumericUtilities : XCTestCase

@end

@implementation TestNumericUtilities

- (void)testRounding {

  double number = 0.123456789;
  XCTAssert(hmlib::utilities::roundTo<2>(number) == 0.12);
  XCTAssert(hmlib::utilities::roundTo<3>(number) == 0.123);
  XCTAssert(hmlib::utilities::roundTo<4>(number) == 0.1235);
  XCTAssert(hmlib::utilities::roundTo<5>(number) == 0.12346);

}

@end

```

{% img right  /images/hmlib-15.png %}

Press `CMD-U` to compile the Library and run the tests. 

Since the header file is included in the test compile, the compiler looks at it (and will fail if there are any issues). 

If the compilation succeeds, it will run the tests.

## C++17 Tests with XCTest in Xcode

And there you have it, a standard C++17 project, editable and compilable in Xcode, with single key access to tests and all the IDE features of Xcode to help debug and analyze your project.

A few tricks you can add:

- Setting a breakpoint in a test case will work as expected. Xcode will stop testing there and you'll be able to use all the debugger tools in Xcode to see what is going on.
- Hover over a Test Class in the Test Navigator or place your mouse on any line, and you will see a small right triangle icon with a circle appear. Click that to run just that one test class. That way you can work an individual test until such time as it works without having to wait for and run *all* test cases.

Happy Testing C++17 in Xcode with XCtest.

Reminder: You can find and download the sample project from Github at [HiltmonLibrary-with-XCTest](https://github.com/hiltmon/HiltmonLibrary-with-XCTest).


*Follow the author as [@hiltmon](https://twitter.com/hiltmon) on Twitter.* 
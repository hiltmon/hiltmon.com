---
layout: post
title: "The Simple C++ Makefile - Executable Edition"
date: 2015-09-28 22:07:23 -0400
comments: true
categories: [C++]
---

I develop a lot of applications in C++ using Xcode on OS X and deploy them to CentOS Linux Servers to run. I follow the [Simple C++ Project Structure](https://hiltmon.com/blog/2013/07/03/a-simple-c-plus-plus-project-structure/) (and the [Xcode edition](https://hiltmon.com/blog/2015/08/01/simple-c-plus-plus-from-makefiles-to-xcode-builds/)) to code up each product.

However, Xcode is not available on Linux. To compile and deploy (and to test compiles and deploys), I use standard Unix [Makefiles](https://www.gnu.org/software/make/manual/make.html#Introduction), available almost everywhere.

In this post I will show you the Makefile I use for multi-platform C++ *executable* builds and explain what each line and command does in detail. <span class="light">For Library builds, I have a similar, but different Makefile, see The Simple C++ Makefile - Library Edition (Coming Soon).</span>

## The Standard Project

I have selected one of my real projects for this post. The project is laid out as follows <span class="light">(most of the source files have been removed to shorten the list)</span>:

	.
	├── Makefile
	├── README.markdown
	├── SantaCruzServer.xcodeproj
	├── doc
	│   └── SantaCruz-dev.yml
	├── include
	│   ├── caches
	│   │   └── session_cache.h
	│   ├── components
	│   ├── connections
	│   ├── queues
	│   ├── workers
	│   └── version.h
	└── src
	    ├── caches
	    │   └── session_cache.cpp
	    ├── components
	    ├── connections
 	   ├── workers
    	└── main.cpp


As expected, the C++ source files are under the `src` folder and includes are in the `include` tree.

And here is the Makefile, the actual one I am using. Scroll below to see the breakdown and why I did it this way.

``` make
#
#  Makefile
#  SantaCruzServer
#
#  Created by Hilton Lipschitz on 2015-09-01.
#  Copyright (c) 2015 Maritime Capital LP. All rights reserved.
#

# HIL: No spaces or comments after otherwise it captures them!
# Determine the platform
UNAME_S := $(shell uname -s)

# CC
ifeq ($(UNAME_S),Darwin)
	CC := clang++ -arch x86_64
else
	CC := g++
endif

# Folders
SRCDIR := src
BUILDDIR := build
TARGETDIR := bin

# Targets
EXECUTABLE := SantaCruzServer
TARGET := $(TARGETDIR)/$(EXECUTABLE)

# Final Paths
INSTALLBINDIR := /usr/local/bin

# Code Lists
SRCEXT := cpp
SOURCES := $(shell find $(SRCDIR) -type f -name *.$(SRCEXT))
OBJECTS := $(patsubst $(SRCDIR)/%,$(BUILDDIR)/%,$(SOURCES:.$(SRCEXT)=.o))

# Folder Lists
# Note: Intentionally excludes the root of the include folder so the lists are clean
INCDIRS := $(shell find include/**/* -name '*.h' -exec dirname {} \; | sort | uniq)
INCLIST := $(patsubst include/%,-I include/%,$(INCDIRS))
BUILDLIST := $(patsubst include/%,$(BUILDDIR)/%,$(INCDIRS))

# Shared Compiler Flags
CFLAGS := -c
INC := -I include $(INCLIST) -I /usr/local/include
LIB := -L /usr/local/lib -lsantacruzengine -lsantacruzlib -larcadia -lcorinth -lyaml-cpp -lzmq -lhiredis -lbondoas

# Platform Specific Compiler Flags
ifeq ($(UNAME_S),Linux)
    CFLAGS += -std=gnu++11 -O2 # -fPIC
    
    # PostgreSQL Special
    PG_VER := 9.3
    INC += -I /usr/pgsql-$(PG_VER)/include
    LIB += -L /usr/pgsql-$(PG_VER)/lib 
else
	CFLAGS += -std=c++11 -stdlib=libc++ -O2
endif

$(TARGET): $(OBJECTS)
	@mkdir -p $(TARGETDIR)
	@echo "Linking..."
	@echo "  Linking $(TARGET)"; $(CC) $^ -o $(TARGET) $(LIB)

$(BUILDDIR)/%.o: $(SRCDIR)/%.$(SRCEXT)
	@mkdir -p $(BUILDLIST)
	@echo "Compiling $<..."; $(CC) $(CFLAGS) $(INC) -c -o $@ $<

clean:
	@echo "Cleaning $(TARGET)..."; $(RM) -r $(BUILDDIR) $(TARGET)

install:
	@echo "Installing $(EXECUTABLE)..."; cp $(TARGET) $(INSTALLBINDIR)
	
distclean:
	@echo "Removing $(EXECUTABLE)"; rm $(INSTALLBINDIR)/$(EXECUTABLE)

.PHONY: clean
```

## Breaking the Makefile down

This Makefile compiles a program called `SantaCruzServer` into the local `bin` folder, and installs it into the standard shared OS X and Linux `/usr/local/bin` folder. Lets see how it does it, line by line.

	UNAME_S := $(shell uname -s)

The first step is to determine which platform the `make` is running on. I look for `Darwin` indicating an OS X computer or `Linux` for Linux.

	# CC
	ifeq ($(UNAME_S),Darwin)
		CC := clang++ -arch x86_64
	else
		CC := g++
	endif


OS X uses the new LLVM Clang compiler (I choose the C++ version), but my Linux servers run GCC 4.8. The `$(CC)` variable now contains the compiler command for the current platform.

	# Folders
	SRCDIR := src
	BUILDDIR := build
	TARGETDIR := bin

These variables set the location of the Source Code (`src`), where the build object files will go (`build`) and where the target will be saved (`bin`).

	# Targets
	EXECUTABLE := SantaCruzServer
	TARGET := $(TARGETDIR)/$(EXECUTABLE)

This sets up the Makefile target to make `bin/SantaCruzServer`. Note that, by default, this Makefile builds to a local `bin` folder so it does not overwrite the running application in case of a failed compile on deploy.

	# Final Paths
	INSTALLBINDIR := /usr/local/bin

This sets where the executable will be installed.

	# Code Lists
	SRCEXT := cpp
	SOURCES := $(shell find $(SRCDIR) -type f -name *.$(SRCEXT))
	OBJECTS := $(patsubst $(SRCDIR)/%,$(BUILDDIR)/%,$(SOURCES:.$(SRCEXT)=.o))

`Make` needs a list of source code files to compile to object files. This list gets built here. I use the `$(SRCEXT)` variable to store my source code file extension. I then use a shell command to search the `src` folder (and its subfolders) for all `.cpp` files and build the `$(SOURCES)` list. I then create an `$(OBJECTS)` list from the `$(SOURCES)` substituting the source path and extension with the build path and the object extension. This makes our compile rule simpler.

	# Folder Lists
	# Note: Intentionally excludes the root of the include folder so the lists are clean
	INCDIRS := $(shell find include/**/* -name '*.h' -exec dirname {} \; | sort | uniq)
	INCLIST := $(patsubst include/%,-I include/%,$(INCDIRS))
	BUILDLIST := $(patsubst include/%,$(BUILDDIR)/%,$(INCDIRS))

The next set of lists are used to build the list of include folders and related lists. 

<span class="light">Aside: I am one of those quirky C++ programmers that does not use pathed `#includes` (e.g. Instead of `#include "../caches/session_cache.h"` I simply use `#include "session_cache.h"`) and expect the compiler to figure it where things are. This way I can re-arrange the code-base by moving files around, not change anything and it still compiles and runs. Xcode behaves the same way by default.</span>

So, the `$(INCDIRS)` variable contains a unique list of subfolders under the `include` folder where all my header files reside. The `$(INCLIST)` variable is a transformation of `$(INCDIRS)` into the format needed as compiler flags. For example `include/caches` is transformed into `-I include/caches`. The `$(BUILDLIST)` variable creates a list of pathed subfolders for the `build` folder, where `include/caches` becomes `build/caches` for the compile step.

	# Shared Compiler Flags
	CFLAGS := -c
	INC := -I include $(INCLIST) -I /usr/local/include
	LIB := -L /usr/local/lib -lsantacruzengine -lsantacruzlib -larcadia -lcorinth -lyaml-cpp -lzmq -lhiredis -lbondoas

Most of the compiler flags are shared across both platforms and are set here. In this case, `$(CFLAGS)` is set to tell the compiler to compile only.

The `$(INC)` variable is set to help the compiler find include files automatically, so it adds the `include` folder where the root header files are, the list of include subfolders determined above and the system shared `/usr/local/include` folder for shared library includes. Now I no longer need to worry when I move files around the code-base.

The `$(LIB)` variable adds the shared system `/usr/local/lib` folder where the shared libraries can be found. The rest of that line contains a long list of libraries that this real program needs to link with (*and is project specific - you need to set these for each project based on that project's needs*). Note that all my shared libraries are in `/usr/local`.

	# Platform Specific Compiler Flags
	ifeq ($(UNAME_S),Linux)
    	CFLAGS += -std=gnu++11 -O2 # -fPIC
    
    	# PostgreSQL Special
    	PG_VER := 9.3
    	INC += -I /usr/pgsql-$(PG_VER)/include
    	LIB += -L /usr/pgsql-$(PG_VER)/lib 
	else
		CFLAGS += -std=c++11 -stdlib=libc++ -O2
	endif

Not all settings are the same, which is why the Makefile now adds platform-specific parameters to our variables.

On Linux, I use the `gnu++11` system library (to go with `g++`) and this gets added to the `$(CFLAGS)` variable. Also, for some unknowable reason, the PostgreSQL include and library files are in a non-standard location in Linux, so they get added to the `$(INC)` and `$(LIB)` variables too.

On OS X, I set `clang` to use the `c++11` language and to link with the `libc++` system library.

	$(TARGET): $(OBJECTS)
		@mkdir -p $(TARGETDIR)
		@echo "Linking..."
		@echo "  Linking $(TARGET)"; $(CC) $^ -o $(TARGET) $(LIB)

As a habit, I set the final goal of the Makefile first. In this case, `make` needs to make the `$(TARGET)` which is `bin/SantaCruzServer` given the list of `$(OBJECTS)` we generated above.

First it creates the `bin` folder if it does not exist, then links the objects into an executable. The `$^` represents the list of targets.

<span class="light">Aside: I am also not one of those people who has to see a busy screen of detailed commands as they compile. So, for Makefile rules, I prepend them with a friendly message and do not print out the actual multi-line incomprehensible command. See the output later on for examples.</span>

	$(BUILDDIR)/%.o: $(SRCDIR)/%.$(SRCEXT)
		@mkdir -p $(BUILDLIST)
		@echo "Compiling $<..."; $(CC) $(CFLAGS) $(INC) -c -o $@ $<

The Makefile needs to know how to generate the `$(OBJECTS)`, and that's where the compile step comes in. For all files in the `src` folder, it compiles to a matching object file in the `build` folder.

That's all we need to build the application, but the Makefile has to do more.

	clean:
		@echo "Cleaning $(TARGET)..."; $(RM) -r $(BUILDDIR) $(TARGET)

The `clean` target tells `make` to remove the target `bin/SantaCruzServer` and the `build` folder. This gives us the ability to force a full recompile.

	install:
		@echo "Installing $(EXECUTABLE)..."; cp $(TARGET) $(INSTALLBINDIR)

The `install` target copies `SantaCruzServer` to `/usr/local/bin` where it will run in production.

	distclean:
		@echo "Removing $(EXECUTABLE)"; rm $(INSTALLBINDIR)/$(EXECUTABLE)

And to uninstall, we have the `distclean` target.

	.PHONY: clean

This final line of code tricks `make` into being able to run the `clean` rules. If it were not here, `make` would try to build a file called `clean` and fail.

## Using the Makefile

To start

	$ make clean

This resets the environment. The output in this project is:

	Cleaning bin/SantaCruzServer...

To build the executable

	$ make -j


This tells `make` to build the primary target - in this case the first and only one in the file.

<span class="light">**Tip: The `-j` parameter parallelizes the build for speed. The documentation for `make` specifies that you need a number of jobs as part of this parameter, but if you set none, `make` uses all cores.**</span>

In my case, the output is:

	Compiling src/connections/control_channel_responder.cpp...
	Compiling src/connections/request_listener.cpp...
	Compiling src/connections/response_publisher.cpp...
	Compiling src/caches/session_cache.cpp...
	Compiling src/main.cpp...
	Compiling src/sc_configuration.cpp...
	Compiling src/sc_logger.cpp...
	Compiling src/sc_server.cpp...
	Compiling src/workers/worker.cpp...
	Compiling src/workers/worker_pool.cpp...
	Linking...
	  Linking bin/SantaCruzServer


The executable can now be found in `bin/SantaCruzServer` and run.

	$ bin/SantaCruzServer
	2015-09-28 21:50:53.999 Info: SantaCruz V0.01 Alpha Server Starting...
	2015-09-28 21:50:53.006 Debug: Using SantaCruzLIB Version 0.1 Alpha
	2015-09-28 21:50:53.013 Debug: Using SantaCruzEngine Version 0.1 Alpha

To install the executable in production:

	sudo make install

This will copy the new executable into production. <span class="light">For development deploys, you do not need the `sudo`.</span>

The output is:

	Installing SantaCruzServer...

And to uninstall:

	$ make distclean
	Removing SantaCruzServer

And the executable is all gone.

## Reusing this Makefile in the next project

The entire Makefile can be copied to the next project. Only a few changes are needed:

* The `$(EXECUTABLE)` name needs to change for the new project
* The list of libraries in the `$(LIB)` variable needs to match the libraries linked to by the new project.
* If PostgreSQL is  not needed, remove it from the Linux Platform Specific Compiler Flags (and remove the `$(INC)` and `$(LIB)` additions).

And that's all there is to it.

I am using this same Makefile pattern across many, many projects and it works well for me. I hope it can help you compile and deploy your C++ projects with ease.

*Follow the author as [@hiltmon](http://twitter.com/hiltmon) on Twitter.*
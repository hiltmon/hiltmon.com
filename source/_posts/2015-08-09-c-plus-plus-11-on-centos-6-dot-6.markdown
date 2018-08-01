---
layout: post
title: "C++11 on CentOS 6.6"
date: 2015-08-09 18:07:25 -0400
comments: true
categories: [ c++, development, programming ]
---

As mentioned in previous [articles](https://hiltmon.com/blog/2015/08/01/simple-c-plus-plus-from-makefiles-to-xcode-builds/), I write a lot of C++11 code on OS X but deploy it on CentOS Linux 6.6 servers. But CentOS 6.6 does not contain a C++11 development environment by default. 

Here's how to set one up.

## Install a C++11 Compiler

We need to get the `repo` files for DevTools2, a Red Hat package that contains a supported C++11 compiler. As `root`, run the following command to retrieve the `repo` file:

    wget http://people.centos.org/tru/devtools-2/devtools-2.repo -O /etc/yum.repos.d/devtools-2.repo
    
Then install the compiler and support tools:

    yum install devtoolset-2-gcc devtoolset-2-binutils devtoolset-2-gcc-c++
    
Before you can compile C++11 code with the DevTools2 compiler, you need to enable it in a new shell:

    scl enable devtoolset-2 bash
    
All compiles in this new shell will use the new compiler.

## Make it permanent

In your `.bash_profile`, add at the bottom:

    echo "WARNING: devtoolset-2 is enabled!"
    . /opt/rh/devtoolset-2/enable
    
All new shells you create will use the new tools.

Enjoy.

*Follow the author as [@hiltmon](https://twitter.com/hiltmon) on Twitter.*
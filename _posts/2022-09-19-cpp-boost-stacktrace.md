---
layout: post
title:  "C++ Boost Stacktrace"
date:   2022-09-19 23:23:23 +0800
categories: c++ boost
---

Code for printing stack at a particular point

Reference: https://stackoverflow.com/questions/3899870/print-call-stack-in-c-or-c/54365144#54365144

``` cpp
#include <iostream>

#define BOOST_STACKTRACE_USE_ADDR2LINE
#include <boost/stacktrace.hpp>

void foo() {
  std::cout << boost::stacktrace::stacktrace() << std::endl;
}

int main() {
  foo();
}

// you may need to use -ldl flag with g++
```
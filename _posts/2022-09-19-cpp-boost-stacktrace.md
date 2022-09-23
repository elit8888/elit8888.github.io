---
layout: post
title:  "C++ Boost Stacktrace"
date:   2022-09-19 23:23:23 +0800
categories: c++ boost
tags: c++ boost
---

Code for printing stack at a particular point

Reference: https://stackoverflow.com/questions/3899870/print-call-stack-in-c-or-c/54365144#54365144

{% highlight cpp %}
#include <iostream>

#define BOOST_STACKTRACE_USE_ADDR2LINE
#include <boost/stacktrace.hpp>

using namespace std::string_literals;

struct Fun {
    Fun(const std::string& s) : _s(s) {}
    void check() const {
        std::cout << boost::stacktrace::stacktrace() << std::endl;
    }
    std::string _s;
};

void foo(const std::string& s) {
    Fun fun(s);
    fun.check();
}

int main() {
    foo("Hello"s);
    return 0;
}

// you may need to use -ldl flag with g++
{% endhighlight %}

Example output:

```
> g++ -o a.out -std=c++17 test.cpp -ldl && ./a.out

 0# Fun::check() const in ./a.out
 1# foo(std::__cxx11::basic_string<char, std::char_traits<char>, std::allocator<char> > const&) in ./a.out
 2# main in ./a.out
 3# __libc_start_main in /lib64/libc.so.6
 4# _start in ./a.out
```

---
layout: single
title:  "C++ Boost Stacktrace"
categories:
  - c++
  - boost
tags:
  - c++
  - boost
---

Code for printing stack at a particular point

Reference: [Stack Overflow](https://stackoverflow.com/questions/3899870/print-call-stack-in-c-or-c/54365144#54365144)

{% highlight cpp %}
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
{% endhighlight %}

<h3>Tags</h3>
{% for tag in site.tags %}
  {{ tag[0] }}
{% endfor %}

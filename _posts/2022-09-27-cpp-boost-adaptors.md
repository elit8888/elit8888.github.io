---
layout: post
title:  "C++ Boost Adaptor"
date:   2022-09-27 15:00:00 +0800
categories: c++ boost
tags: c++ boost
---

Code for using filtered / transformed view over some existing containers

This is similar to range-v3, a feature that will be in c++20.

``` cpp
#include <iostream>
#include <vector>
#include <boost/range/adaptor/filtered.hpp>
#include <boost/range/adaptor/transformed.hpp>

auto main() -> int {
    // the program should print the cubed of even number only
    auto v = std::vector<int>{2, 1, 3, 5, 4};
    auto power_of_three = [](auto num) { return num * num * num; };
    for (auto elem : v
            | boost::adaptors::filtered([](auto num) { return num % 2 == 0; })
            | boost::adaptors::transformed(power_of_three)) {
        std::cout << elem << std::endl;
    }
    return 0;
}

// g++ -o a.out -std=c++17 -I/path/to/boost test.cpp && ./a.out

// should have output:
8
64
```
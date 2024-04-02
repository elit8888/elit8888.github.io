---
title: "C++ Scoped Timer"
date: 2023-01-10 22:22:22 +0800
categories: [c++]
tags: [c++, raii]
---

Code for scoped timer. Once a block goes out of a scope, duration will be printed.

```c++
#include <iostream>
#include <string>
#include <chrono>

struct ScopedTimer {
  std::chrono::steady_clock::time_point m_begin;
  std::string m_name;
  ScopedTimer(const std::string& name) : m_begin{std::chrono::steady_clock::now()}, m_name{name} {
    std::cout << '[' << m_name << "] Starts...\n";
  }
  ~ScopedTimer() {
    auto end = std::chrono::steady_clock::now();
    std::cout << '[' << m_name << "] Time difference (sec) = "
      << (std::chrono::duration_cast<std::chrono::microseconds>(end - m_begin).count()) / 1'000'000.0
      << std::endl;
  }
};

auto main() -> int {
  {
    ScopedTimer t{"Foo"};
    // some code
  }
  return 0;
}
```

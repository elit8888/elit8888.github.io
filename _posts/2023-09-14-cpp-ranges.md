---
title: "C++ Ranges"
date: 2023-09-14 09:09:09 +0800
categories: [c++, ranges]
tags: [c++, ranges]
---

Code for std ranges to transform from a collection to another collection after some ranges operations, available in c++23.
Doing this we can have AAA style.

```c++
#include <vector>
#include <string>
#include <ranges>
#include <map>

int main() {
    auto src = std::map<std::string, int>{};
    auto dst = std::ranges::to<std::vector<std::string>>(
            src |
            std::views::filter([](const auto& p) { return p.second == 0; }) |
            std::views::transform([](const auto& p) { return p.first; }));
    return 0;
}
```

https://godbolt.org/z/vMn1se8P7

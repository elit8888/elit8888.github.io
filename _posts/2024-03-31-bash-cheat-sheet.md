---
title: "Bash Cheat Sheet"
date: 2024-03-31 09:09:09 +0800
categories: [bash]
tags: [bash]
---

Some bash utils that I am easy to forget.

```
Ctrl-o - used when browsing history command (Ctrl-r), it will execute the command, and fetch the next one from the history.
```

To copy some files to a backup to have the same extension name
```bash
cp a.txt a.txt.a-long-text-for-testing-that-i-dont-want-to-retype
cp b.txt b.txt.${_##*.}
```

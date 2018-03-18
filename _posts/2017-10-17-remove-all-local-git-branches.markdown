---
layout: post
title:  "Remove All Local Git Branches"
date:   2017-10-17 19:40:00
description: "git branch | grep -v \\* | xargs git branch -D"
label: note
---

``` shell
git branch | grep -v \* | xargs git branch -D
```

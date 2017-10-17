---
layout: post
title:  "Remove all local git branches"
date:   2017-10-17 19:40:00
description: "git branch | grep -v \\* | xargs git branch -D"
---

``` shell
git branch | grep -v \* | xargs git branch -D
```

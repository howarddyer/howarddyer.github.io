---
layout: post
title:  "Show Hidden Files and Folders in Mac OS"
date:   2016-01-17 17:34:56
description:
  nested:
    - description: "defaults write com.apple.finder AppleShowAllFiles -boolean true"
    - description: "killall Finder"
---

``` shell
defaults write com.apple.finder AppleShowAllFiles -boolean true
killall Finder
```

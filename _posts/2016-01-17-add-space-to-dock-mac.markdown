---
layout: post
title:  "Add a Space to the Dock in Mac OS"
date:   2016-01-17 17:54:56
description:
  nested:
    - description: "defaults write com.apple.dock persistent-apps -array-add &#39;{&#34;tile-type&#34;=&#34;spacer-tile&#34;;}&#39;"
    - description: "killall Finder"
label: note
---

``` shell
defaults write com.apple.dock persistent-apps -array-add '{"tile-type"="spacer-tile”;}'
killall Dock
```

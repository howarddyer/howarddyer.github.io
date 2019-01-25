---
layout: post
title:  "Git Stash Commands"
date:   2018-12-15 12:00:00
label: note
---

To push a named stash to the stack:
``` shell
git stash push -m "The name of my stash"
```

To view the stash stack:
``` shell
git stash list
```

To apply a stash and remove it from the stack:
``` shell
git stash pop stash@{n}
```

To apply a stash and keep it on the stack:
``` shell
git stash apply stash@{n}
```

To turn a stash into a branch:
``` shell
git stash branch branchname stash@{n}
```

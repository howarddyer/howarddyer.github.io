---
layout: post
title:  "Create Command Line Directory Shortcuts"
date:   2015-05-15 00:44:53
description:
  nested:
    - description: "nano .bash_profile"
    - description: "alias shortcutToMyDevFolder='cd /Path/To/My/Dev/Folder'"
    - description: "source ~/.bash_profile"
---

Open the .bash_profile file (at the root) for editing:

``` bash
nano .bash_profile
```

Add your alias:

``` bash
alias shortcutToMyDevFolder='cd /Path/To/My/Dev/Folder'
```

Save the file, and then refresh the shell:

``` bash
source ~/.bash_profile
```

Alternatively, symlimks can be created with the "ln" command (so that typing "cd shortcutToMyDevFolder" will do the same).

``` bash
ln -s /Path/To/My/Dev/Folder shortcutToMyDevFolder
```

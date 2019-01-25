---
layout: post
title:  "Generate a New SSH Key"
date:   2019-01-25 16:30:00
label: note
---

Run the following in Git Bash, with the relevant email address. This will create a new SSH key (using the provided email as a label), before copying that SSH key to the pasteboard for use on a third party website.

```shell
ssh-keygen -o -t rsa -b 4096 -C "name@email.com"
cat ~/.ssh/id_rsa.pub | clip
```

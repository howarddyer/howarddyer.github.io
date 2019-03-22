---
layout: post
title:  "Turn Any GitHub Repository Into A CDN"
date:   2019-03-22 11:00:00
label: note
description: "https://cdn.jsdelivr.net/gh/{username}/{repo}/{path_to_file}"
---

(This tip is originally from <a href="https://frontstuff.io/" target="_blank">Sarah Dayan, Frontstuff</a> via <a href="https://gomakethings.com/" target="_blank">Chris Ferdinandi, Go Make Things</a>)

Using <a href="https://www.jsdelivr.com/" target="_blank">jsDelivr</a>, you can turn any GitHub repository into a CDN:

## How to do this:

1. Use the base URL **https://cdn.jsdelivr.net/gh/**
2. Add **{username}/** where **{username}** is your GitHub username
3. Add **{repo}/** where **{repo}** is the name of your GitHub repository
4. Add **{path_to_file}/** where **{path_to_file}** is the exact path to the file in your repository that you want to access.

---
layout: post
title:  "A checkpoint of my current approach to CSS"
date:   2019-07-26 22:00:00
label: post
---

## Introduction

The way I implement CSS has changed and morphed drastically over the years, with the incorporation of different technologies and methodologies. However I feel somewhat confident in my current methods and thought I would share this for archival purpose.

*(What this really means is I’m aware that these methods are open/destined to change further over time. This post serves as a checkpoint of my current approach to CSS)*

## My current approach to CSS

I write my CSS using SCSS, and implement the ITCSS (Inverted Triangle CSS) architecture using the BEM (Block Element Modifier) naming convention.

## Why SCSS?

The simple (and obvious) reason for using SCSS is that it provides a DRY (Don’t Repeat Yourself) and feature rich way of creating CSS.

## Why ITCSS?

ITCSS pushes for styles to be grouped by CSS specificity, instead of arbitrary contexts. This drastically reduces style collisions/leaks and calls an end to specificity wars. However, the benefit of the architecture that I like the most is that styles are very manageable and easily extended into the future.

## Why BEM?

Utilising BEM naming means that styles can be built up in a structured and modular fashion. The outputted benefit of this is a library of reusable blocks that can be used intelligently across a wide range of UI compositions.

## Conclusion

This implementation has allowed me to follow a pattern that delivers a manageable and reusable library of styles of which I am confident can be highly effective in any project. I’ll follow up with further detail about my implementation of these technologies and methodologies in future posts.

## Further reading

<a href="https://sass-lang.com" target="_blank">Sass</a>

<a href="https://www.creativebloq.com/web-design/manage-large-css-projects-itcss-101517528" target="_blank">Manage large CSS projects with ITCSS by Harry Roberts | Creative Bloq</a>

<a href="https://tech.yandex.com/bem/" target="_blank">Bem | Yandex</a>

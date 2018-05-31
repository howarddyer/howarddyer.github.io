---
layout: post
title:  "Speeding Up the Critical Rendering Path"
date:   2018-05-31 20:00:00
description: "The CRP is the steps that a browsers need to take before any visual change can be shown to the user. The question is how can we optimise the CRP to speed up the time to first render?"
label: post
---

### Introduction

I recently did a talk at my place of work on the process that the browser goes through to render a page, following a subject that I've recently been researching. Part of the talk is summed up in my previous post "Browser Rendering or: How I Learned to Stop Wondering and Understand the CSSOM".

In the talk I highlighted how a web developer could use this knowledge to implement improvements to the Critical Rendering Path (CRP). The CRP is the steps that a browsers need to take before any visual change can be shown to the user.

A simplified version of these steps would be:
1. Parse HTML and build DOM
2. Parse CSS and build CSSOM
3. Parse JavaScript
4. Execute JavaScript
5. Build Render Tree using the DOM and CSSOM
6. Execute first render

The question is how can we optimise the CRP to speed up the time to first render?

### Minimise the amount of bytes to be downloaded

It seems obvious to say, but if the browser is given less things to parse, then it will take less time to do so.

- Using common sense, reduce and simplify your content as much as is practical so that you only use HTML, CSS and images that are absolutely required
- Reduce the size and amount of files that are implemented by the page - make use of optimisation steps such as minification, concatenation, image optimisation and compression, caching, sprites, etc

### Reduce the length and complexity of the CRP

If page content is prioritised, it can be ensured that the CRP only contains content that the first render is reliant on.

- Consider styling above-the-fold content with inline CSS (in the head) to ensure that the first render is not dependant on construction of the CSSOM
- If the CRP contains any content that the first render does not require (e.g. JavaScript, images), remove it from the CRP and load it asynchronously or after the first render is complete (e.g. using a Lazy Load plugin)

### Conclusion

To summarise, once you’ve streamlined your content, ensure that it is prioritised to deliver the first render sooner. The CRP has to be executed every time a webpage is visited, so it makes sense to ensure that it is as slight and also as relevant as possible.

### Further Reading

<a href="https://docs.google.com/presentation/d/1tADQjXUTpXKi8srWbPp7EfmF68Gx-krhVBxT5NgmHxk/edit?usp=sharing" target="_blank">Slides from the "Browser Rendering (deep dive)" presentation</a>

<a href="https://css-tricks.com/examples/LazyLoading/" target="_blank">Lazy Loading Images — CSS Tricks</a>

<a href="https://developers.google.com/web/fundamentals/performance/critical-rendering-path/" target="_blank">Critical Rendering Path — Google Developers</a>

---
layout: post
title:  "Improving the Render"
date:   2018-07-16 13:00:00
description: "I've blogged previously about how the browser goes about rendering content, and separately about how we can improve the path to content that is critical for the render. The final piece of this puzzle is to explore how to make renders more performant."
label: post
---

## Introduction

I've blogged previously about <a href="http://howard-dyer.co.uk/browser-rendering-or-how-i-learned-to-stop-wondering-and-understand-the-cssom.html" target="_blank">how the browser goes about rendering content</a>, and separately about <a href="http://howard-dyer.co.uk/speeding-up-the-critical-rendering-path.html" target="_blank">how we can improve the path to content that is critical for the render</a>.

The final piece of this puzzle is to explore how to make renders more performant.

### What is a render?

A render is the browser's process of adding visual change to the screen. It's cause and effect &mdash; an action is made (usually by the user) and the render is the result.

### What causes a render?

Anything that requires the screen to be updated could cause a render. Here are a few examples:
<ul>
	<li>A user scrolls the page</li>
	<li>A user resizes the browser</li>
	<li>A user hovers over an element</li>
    <li>A user navigates to a new page</li>
	<li>A JavaScript function is run</li>
	<li>A transition/animation is initiated</li>
</ul>

## How can I improve the render?

Having a good understanding of the render is of course a prerequisite to knowing how to improve it. In parallel to my points about <a href="http://http://howard-dyer.co.uk/speeding-up-the-critical-rendering-path.html" target="_blank">Speeding Up the Critical Rendering Path</a>, the key to improving the render is mostly about reducing and simplifying what the browser actually has to do.

### Consider the render cycles that are required for updates

To render content on the screen the browser goes through three steps (Layout, Painting, Composite) in different combinations, depending on the update required.

If layout of the page needs to change at all &mdash; for example, if an element's height or width changes &mdash; then all 3 steps will need to be completed. If a non layout visual change needs to happen &mdash; for example, if text needs to turn red &mdash; then the Painting and Composite stages will need to be completed.

If already rendered visuals need to be brought into view, then only the Composite step needs to happen &mdash; for example, if the user scrolls the page, the elements that are below-the-fold have already been rendered and the 'final image' just needs to be reassembled. The least costly in terms of time and resources is for the browser to *only* go through the Composite stage.

Improvements can be made by ensuring that the browser doesn't go through any steps that are not necessary. To assist this, <a href="https://csstriggers.com/" target="_blank">CSS Triggers</a> is a helpful resource to indicate the steps that each CSS property invokes.

### Take advantage of composite layers and GPU acceleration

If content is promoted to its own composite layer (during the painting stage), it will be individually uploaded to the GPU as a "texture" (flat image). Any visual change on content within its own layer will only require a Composite step, since the "texture" is simply swapped out by the GPU. This is called GPU acceleration.

You can actually instigate the creation of a layer by using certain CSS styles, such as:

<ul>
    <li>transform properties &mdash; translate, scale, rotate, skew, matrix</li>
    <li>opacity</li>
    <li>position or z-index</li>
    <li>will-change (or transform: translateZ(0) for browsers that don’t have support)</li>
</ul>

It is worth noting, that elements should not be promoted to their own layer unneccessarily,  since the impact on performance could be outweighed by the requirement of uploading too many "textures" to the GPU.

## Conclusion

In every day web development, this sort of knowledge doesn't really come into the main stream. Also, it could certainly be agreed that retrospectively adding 1 or 2 small changes to your code from this post won't speed up your website significantly.

However, an improved understanding of these foundations is paramount to improving the efficiency of your code and how easy it is to debug when problems arise.

If you can know how to write your website exactly the way that the browser expects to read it, then you'll be working with the tide and improving your efficiency along the way.

## Further reading

<a href="http://howard-dyer.co.uk/browser-rendering-or-how-i-learned-to-stop-wondering-and-understand-the-cssom.html"
target="_blank">Browser Rendering or: How I Learned to Stop Wondering and Understand the CSSOM — Howard Dyer</a>

<a href="http://howard-dyer.co.uk/speeding-up-the-critical-rendering-path.html" target="_blank">Speeding Up the Critical Rendering Path — Howard Dyer</a>

<a href="https://docs.google.com/presentation/d/1tADQjXUTpXKi8srWbPp7EfmF68Gx-krhVBxT5NgmHxk/edit?usp=sharing" target="_blank">Slides from the "Browser Rendering (deep dive)" presentation</a>

<a href="https://csstriggers.com/" target="_blank">CSS Triggers</a>

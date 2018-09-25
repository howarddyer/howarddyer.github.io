---
layout: post
title:  "What Happens in a BFC, Stays in a BFC!"
date:   2018-09-21 22:00:00
description: "The Block Formatting Context (BFC) in CSS is a concept that many developers can’t name or describe, but know all about."
label: post
---

### Introduction

The Block Formatting Context (BFC) in CSS is a concept that many developers can’t name or describe, but know all about. In this post I’ll briefly outline what a BFC is, the problems that they solve and how to create one.

### What is a BFC?

A BFC is a region implicitly (or sometimes explicitly) applied to an element, so that this parent element will *contain* all children elements, i.e. the parent element is the origin of the BFC, and interactions and behaviours of children elements alter as a side-effect of this.

### But seriously, what is a BFC?

A good metaphor of a BFC is that it’s a protective parent that doesn’t allow any of its children to go outside of its 4 walls (if you were to think of the box-model, the 4 walls are the borders).

This is done by 3 means:

* Containing floats
* Preventing text wrap around outside elements
* Preventing the collapse of margins with the margins of outside elements

### Contains floats

<figure>
    <img src="/static/images/posts/2018-09-21-bfc-1.png" alt="An outer element does not respect the height of a floated element contained within it" class="c-post__image">
    <figcaption>Example 1: An outer element does not respect the height of a floated element contained within it.</figcaption>
</figure>

Example 1 shows a text element and a floated element inside an outer element without a fixed height. When there is not enough text to surpass the height of the floated element, the outer element doesn’t respect the height of the floated element in the same way that it respects the height of the text element. Due to this, the floated element ends up spilling out of the outer element.

(Note: This issue has commonly been approached by applying a hack known as the <a href="https://css-tricks.com/snippets/css/clear-fix/" target="_blank">clearfix</a>. This works by inserting an element at the bottom of the outer element that clears the floated element. Though this arguably was never a very good approach.)

<figure>
    <img src="/static/images/posts/2018-09-21-bfc-2.png" alt="An outer element that creates a BFC will respect the height of all floated element contained within it" class="c-post__image">
    <figcaption>Example 2: An outer element that creates a BFC will respect the height of all floated element contained within it.</figcaption>
</figure>

In Example 2, a BFC has been applied to the outer element so that it now contains the floated element.

### Prevents text wrap

<figure>
    <img src="/static/images/posts/2018-09-21-bfc-3.png" alt="Text that is placed next to a floated element will naturally wrap around it" class="c-post__image">
    <figcaption>Example 3: Text that is placed next to a floated element will naturally wrap around it.</figcaption>
</figure>

Example 3 shows that when there is enough text, the text element will wrap around the floated element. Notice also how the outer element wraps around the text, no matter how long the text runs (unlike the floated element in Example 1)

<figure>
    <img src="/static/images/posts/2018-09-21-bfc-4.png" alt="Text within a BFC will not wrap around floated elements that are outside the BFC" class="c-post__image">
    <figcaption>Example 4: Text within a BFC will not wrap around floated elements that are outside the BFC.</figcaption>
</figure>

In Example 4, a BFC has been applied to the text element so that it no longer wraps around the floated element.

### Prevents collapsing of margins

<figure>
    <img src="/static/images/posts/2018-09-21-bfc-5.png" alt="An element's margins will naturally collapse into another element's margins if placed adjacent" class="c-post__image">
    <figcaption>Example 5: An element's margins will naturally collapse into another element's margins if placed adjacent.</figcaption>
</figure>

Example 5 shows a series of text elements (blue) within an outer element (grey). The outer element and all text elements have top and bottom margins. However we can see that the top margin of the first text element and the bottom margin of the last text element collapses with the margins of the outer element.

<figure>
    <img src="/static/images/posts/2018-09-21-bfc-6.png" alt="If an element is within a BFC, its margins will not collapse into margins outside of the BFC" class="c-post__image">
    <figcaption>Example 6: If an element is within a BFC, its margins will not collapse into margins outside of the BFC.</figcaption>
</figure>

In Example 6, with a BFC applied to the outer element, the margins of the first and last text elements no longer collapse.

### How do you create a BFC?

A BFC can be created, as a a side effect, by applying:

* A float property of left or right
* Absolute or fixed positioning
* A display property of inline-block
* A display property of grid or inline-grid (the BFC applies to the grid items contained within this element)
* A display property of flex or inline-flex (the BFC applies to the flex items contained within this element)
* A display property of table, table-row, table-row-group, table cell, table caption, table-header-group, table-footer-group or inline-table.
* An overflow property of anything other than visible on a block element
* A contain property of layout, content, or strict

You could also apply a display property of flow-root. Though <a href="https://caniuse.com/#search=flow-root" target="_blank">browser support is still limited</a>, the sole purpose of this property is to create a BFC.

### Conclusion

There are many issues that occur in CSS that, through iteration, you acquire knowledge on how to solve. But it’s quite interesting that, whilst problems are solved, it’s not always fully understood why the problems are caused or how the solution actually solves it.

For Block Formatting Contexts it could simply be put, that what happens in a BFC stays in a BFC.

### Resources

<a href="https://caniuse.com/#search=flow-root" target="_blank">display: flow-root | Can I Use...</a>

<a href="https://css-tricks.com/snippets/css/clear-fix/" target="_blank">The Clearfix: Force an Element To Self-Clear its Children | CSS Tricks</a>

<a href="https://codepen.io/howarddyer/full/NLmqMb" target="_blank">Block Formatting Context examples, pen by Howard Dyer | Codepen</a>

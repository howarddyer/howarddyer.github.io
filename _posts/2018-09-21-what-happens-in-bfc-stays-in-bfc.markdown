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

A BFC is a region implicitly (or sometimes explicitly) applied to an element, which means this parent element will contain all children elements, i.e. the parent element is the origin of the BFC, and interactions and behaviours of children elements alter as a side-effect of this.

### But seriously, what is a BFC?

A good metaphor of a BFC is that it’s a protective parent that doesn’t allow any of its children to go outside of its 4 walls (if you were to think of the box-model, the 4 walls are the borders).

This is mostly done through 3 means:

* Containing floats
* Preventing text wrap around outside elements
* Preventing the collapse of margins with the margins of outside elements

### Contains floats

<figure>
    <p data-height="260" data-theme-id="dark" data-slug-hash="YOgMVa" data-default-tab="result" data-user="howarddyer" data-pen-title="Block Formatting Context: Example 1" class="codepen">
        See the Pen <a href="https://codepen.io/howarddyer/pen/YOgMVa/" target="_blank">Block Formatting Context: Example 1</a> by Howard Dyer (<a href="https://codepen.io/howarddyer" target="_blank">@howarddyer</a>) on CodePen.
    </p>
    <figcaption>An outer element does not respect the height of a floated element contained within it.</figcaption>
</figure>
<script async src="https://static.codepen.io/assets/embed/ei.js"></script>

Example 1 shows a text element and a floated element inside an outer element. When there is not enough text to surpass the height of the floated element, the outer element doesn’t respect the height of the floated element in the same way that it respects the height of the text element. Due to this, the floated element ends up spilling out of the outer element.

(Note: This issue has been commonly been approached by applying a hack known as the <a href="https://css-tricks.com/snippets/css/clear-fix/" target="_blank">clearfix</a>. This works by inserting an element at the bottom of the outer element that clears the floated element. Though this arguably was never a very good approach.)

<figure>
    <p data-height="308" data-theme-id="dark" data-slug-hash="PdLgmx" data-default-tab="result" data-user="howarddyer" data-pen-title="Block Formatting Context: Example 2" class="codepen">
        See the Pen <a href="https://codepen.io/howarddyer/pen/PdLgmx/" target="_blank">Block Formatting Context: Example 2</a> by Howard Dyer (<a href="https://codepen.io/howarddyer" target="_blank">@howarddyer</a>) on CodePen.
    </p>
    <figcaption>An outer element that creates a BFC will respects the height of all floated element contained within it.</figcaption>
</figure>
<script async src="https://static.codepen.io/assets/embed/ei.js"></script>

In Example 2, a BFC has been applied to the outer element so that it now contains the floated element.

### Prevents text wrap

<figure>
    <p data-height="390" data-theme-id="dark" data-slug-hash="XPGyyW" data-default-tab="result" data-user="howarddyer" data-pen-title="Block Formatting Context: Example 3" class="codepen">
        See the Pen <a href="https://codepen.io/howarddyer/pen/XPGyyW/" target="_blank">Block Formatting Context: Example 3</a> by Howard Dyer (<a href="https://codepen.io/howarddyer" target="_blank">@howarddyer</a>) on CodePen.
    </p>
    <figcaption>Text that is placed next to a floated element will naturally wrap around it.</figcaption>
</figure>    
<script async src="https://static.codepen.io/assets/embed/ei.js"></script>

Example 3 shows that when there is enough text, the text element will wrap around the floated element. Notice also how the outer element wraps around the text, no matter how long the text runs (unlike the floated element in Example 1)

<figure>
    <p data-height="432" data-theme-id="dark" data-slug-hash="bxZJgZ" data-default-tab="result" data-user="howarddyer" data-pen-title="Block Formatting Context: Example 4" class="codepen">
        See the Pen <a href="https://codepen.io/howarddyer/pen/bxZJgZ/" target="_blank">Block Formatting Context: Example 4</a> by Howard Dyer (<a href="https://codepen.io/howarddyer" target="_blank">@howarddyer</a>) on CodePen.
    </p>
    <figcaption>Text within a BFC will not wrap around floated elements that are outside the BFC.</figcaption>
</figure>
<script async src="https://static.codepen.io/assets/embed/ei.js"></script>

In Example 4, a BFC has been applied to the text element so that it no longer wraps around the floated element.

### Prevents collapsing of margins

<figure>
    <p data-height="335" data-theme-id="dark" data-slug-hash="VGRNWQ" data-default-tab="result" data-user="howarddyer" data-pen-title="Block Formatting Context: Example 5" class="codepen">
        See the Pen <a href="https://codepen.io/howarddyer/pen/VGRNWQ/" target="_blank">Block Formatting Context: Example 5</a> by Howard Dyer (<a href="https://codepen.io/howarddyer" target="_blank">@howarddyer</a>) on CodePen.
    </p>
    <figcaption>An element's margins will naturally collapse into another element's margins if placed adjacent.</figcaption>
</figure>
<script async src="https://static.codepen.io/assets/embed/ei.js"></script>

Example 5 shows a series of text elements within an outer element. The outer element and all text elements have top and bottom margins. However we can see that the top margin of the first text element and the bottom margin of the last text element collapses with the margins of the outer element.

<figure>
    <p data-height="395" data-theme-id="dark" data-slug-hash="zJbXPN" data-default-tab="result" data-user="howarddyer" data-pen-title="Block Formatting Context: Example 6" class="codepen">
        See the Pen <a href="https://codepen.io/howarddyer/pen/zJbXPN/" target="_blank">Block Formatting Context: Example 6</a> by Howard Dyer (<a href="https://codepen.io/howarddyer" target="_blank">@howarddyer</a>) on CodePe.
    </p>
    <figcaption>If an element is within a BFC, its margins will not collapse into margins outside of the BFC.</figcaption>
</figure>
<script async src="https://static.codepen.io/assets/embed/ei.js"></script>

With a BFC applied to the outer element, the margins of the first and last text elements no longer collapse.

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

There are many issues that occur in CSS that, through iteration, you acquire knowledge on how to solve. But it’s quite interesting that, whilst problems are solved, it’s never always fully understood why the problems are caused or how the solution actually solves it.

For Block Formatting Contexts it could simply be put, that what happens in a BFC stays in a BFC.

### Resources

<a href="https://caniuse.com/#search=flow-root" target="_blank">display: flow-root | Can I Use...</a>

<a href="https://css-tricks.com/snippets/css/clear-fix/" target="_blank">The Clearfix: Force an Element To Self-Clear its Children | CSS Tricks</a>

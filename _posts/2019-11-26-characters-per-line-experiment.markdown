---
layout: post
title:  "Characters Per Line experiment"
date:   2019-11-26 17:00:00
label: post
description: Whilst researching Accessibility topics, I came across the discussion of considering line length when laying out text. The general consensus being that there's a sweet spot between too many characters and too few characters.
---

## Introduction

Whilst researching Accessibility topics, I came across the discussion of considering line length when laying out text. The general consensus being that there's a sweet spot between too many characters and too few characters.

The immediate benefit of defining an ideal line length is that content is generally easier to scan. However, the deeper win in terms of accessibility, is that content is more approachable for individuals who have trouble reading or processing words.

I conducted an experiment to understand the concepts around line length and how a "characters per line" approach can be made.

## How I intended to approach

The current (most basic) approach to laying out text would involve the following:

1. Width of container is set
2. Font size is set
3. The lines of text fills the space, regardless of line length

I was looking to see if there was a way for the following to be done:

1. Width of container is set
2. Character Per Line (CPL) value is set
3. The font size is set automatically so that the line lengths do not exceed the CPL value

## How to work out font size using CPL?

A font size is determined by the vertical height/cap height of the font. However it is important to remember that this value is not 100% representative, i.e. there is usually some marginal white space to the top and bottom of the font (even when line height is not excessive).

The missing value that is required to define the font size using CPL, is the ratio of font size to character width.

<img src="/static/images/posts/2019-11-26-cpl-1.png" alt="By multiplying the character width by the ratio you can get the font size, and therefore by dividing the font size by the ratio you can get the character width." class="c-post__image">

Using the same sentence defined at different font sizes, I was able to work out the average pixel width of a font's character by dividing the sentence width by the amount of characters . I then divided the font size by the width value to get the ratio of font size to character width.

<img src="/static/images/posts/2019-11-26-cpl-2.png" alt="4 sentences with 27 characters per line each and set at font sizes 10px, 20px, 30px and 40px respectively, have sentence width of 148.45, 296.91, 445.34 and 593.8 respectively, have character width of 5.4981, 10.9967, 16.4941, 21.9926 respectively, and all have a ratio of 1.81 to 1 of font size to width." class="c-post__image">

From this we can deduce that to get the font size for a certain amount of characters in a predefined element width, we could use the following equation:

<img src="/static/images/posts/2019-11-26-cpl-3.png" alt="To get the font size, divide the element width by characters per line, and multiply by ratio." class="c-post__image">

**Note:** These values are _very_ approximate. We can expect the ratios to be widely varying between different fonts (especially those of a different font type, i.e. monotype, sans-serif, serif etc).

## Mixin

By doing the above formula using several fonts, I worked out average values for the 3 fonts types of monospace, sans-serif and serif. I then implemented these values into a mixin as a proof of concept for generating font size by characters per line.

```css
$s-font-type-constants: (
    "serif": 2.3333,
    "sans-serif": 2.2513,
    "monospace": 1.67
);

@mixin cpl-font-size($width, $cpl, $font-type) {

    @if map-has-key($s-font-type-constants, $font-type) {

        $constant-value: map-get($s-font-type-constants, $font-type);
        $cpl-font-size-value: ($width / $cpl) * $constant-value;

        font-size: #{$cpl-font-size-value + "px"};
        width: #{$width + "px"};

    } @else {

        @error "The value `#{$font-type}` passed to cpl-font-size is not valid. Please use serif, sans-serif or monospace.";

    };

}

// @include cpl-font-size(600, 50, monospace);
```

## Demo

<p data-height="338" data-theme-id="0" data-slug-hash="BaaMpKP" data-default-tab="result" data-user="howarddyer" data-embed-version="2" data-pen-title="Characters Per Line experiment - CPL Customiser" class="codepen">See the Pen <a href="https://codepen.io/howarddyer/pen/BaaMpKP">Characters Per Line experiment - CPL Customiser</a> by Howard Dyer (<a href="https://codepen.io/howarddyer">@howarddyer</a>) on <a href="https://codepen.io">CodePen</a>.</p>
<script async src="https://static.codepen.io/assets/embed/ei.js"></script>


## Conclusion

I don't intend on using the mixin in production sites, nor do I recommend this. Though it was an interesting way of understanding the requirements around line lengths. I believe the EM unit and the CH unit are very useful if line lengths need to be explicitly set in production sites.

## Further reading

* https://meyerweb.com/eric/thoughts/2018/06/28/what-is-the-css-ch-unit/


## Resources

* https://docs.google.com/presentation/d/1V8MJ7saDdzAOqbPXYFTm2uMkswI223mkXf5Zm9CgHk8/edit?usp=sharing
* https://www.smashingmagazine.com/2014/09/balancing-line-length-font-size-responsive-web-design/
* https://blog.prototypr.io/how-to-set-perfect-line-lengths-for-the-web-528f08f8b344
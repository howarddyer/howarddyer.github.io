---
layout: post
title:  "How I use ITCSS"
date:   2019-09-26 16:00:00
label: post
description: ITCSS is a CSS framework that helps keep a project's stylesheets organised so that there are less issues to do with style collisions, file bloat and redundant styles.
---

## Introduction

**<abbr title="Inverted Triangle CSS">ITCSS</abbr>** is a CSS framework that helps **keep a project's stylesheets organised** so that there are **less issues** to do with **style collisions**, **file bloat** and **redundant styles**. ITCSS also works with the cascade in mind, so that styles are **ordered by specificity and importance**.

ITCSS stands for Inverted Triangle CSS, since the visualisation of the layers (and the associated reach of styles contained therein) resembles an upside-down triangle.

<img src="https://www.xfivecdn.com/xfive/wp-content/uploads/2016/02/01083650/itcss-layers2.svg" alt="The further you go down the ITCSS layers, the more specific and less far reaching the style. From top to bottom, Settings, Tools, Generic, Elements, Objects, Components and Utilities." class="c-post__image">

## ITCSS Layers

### Settings

The Settings layer contains definitions for colours, fonts, layouts, typography and anything that can be used within a style in a later file. Using SCSS variables, I treat this layer as configuration for the CSS project as a whole.

No CSS should be outputted from this layer.

### Tools

The Tools layer contains mixins and functions that can be used to output repeatable patterns throughout the later files.

Again, no CSS should be putputted from this layer.

### Generic

The Generic layer contains base reset styles, normalise styles and box sizing that should be applied widely across the DOM, i.e. you could apply styles to the html, body or * selectors.

This is the first layer that has the opportunity to output CSS.

### Elements

The Elements layer contains styles applicable to HTML tag names only — such as body, p, table, h1, etc. No class names or nested selectors should be used in this layer.

### Objects

The Objects layer targets elements by their class name only. Also, styles in this layer should only be of a layout nature — such as height, width, padding, margin, etc — and not apply any decoration — such as colours, font-size, etc.

If an object happens to add anything other than layout, then it would be moved to the next layer, Components.

### Components

The Components layer, like the Objects layer, targets elements by their class name only. However, unlike the Objects layer, the Components layer can contain layout AND decoration styles.

### Utilities

The Utilities layer contains utility and helper classes that can override individual styles, for example a hidden class.

## My conventions

### Numbered folders

I like to have a separate folder for each ITCSS layer to keep the files separated and organised. I also add a number to the folder so that the folders remain in the correct order, as per ITCSS:
1. Settings
2. Tools
3. Generic
4. Elements
5. Objects
6. Components
7. Utilities

### Multiple manifest files

For importing the styles, I have a manifest file (named styles.scss) at the root of the stylesheets structure which imports additional manifests (partials named _-manifest.scss) at each level:

```css
/* styles.scss */

@import "1.Tools/-manifest";
@import "2.Settings/-manifest";
@import "3.Generic/-manifest";
@import "4.Elements/-manifest";
@import "5.Objects/-manifest";
@import "6.Components/-manifest";
@import "7.Utilities/-manifest";
```

The advantage of splitting the imports over many files is that the files don't get too long, and I personally like the separation of concerns.

I also prepend the partial manifest with a hyphen, so that when the layer folders contain other files, the manifests are always at the top and are easily found.

<img src="/static/images/posts/2019-09-26-itcss-1.png" alt="The take away from how I structure my ITCSS folder is that I number each ITCSS layer folder, each folder contains its own manifest, and I prepend the manifest files with a hyphen to ensure it sits at the top when the files are ordered alphabetically." class="c-post__image">

### Files with 1 context

I ensure that each file has only one context — a file in the Elements layer contains styles for 1 context of HTML tags, a file in the Components layer contains 1 component, a file in the Utilities layer should contains overrides for one property.

To illustrate this, some of the files I would implement include:

**Elements**
* _headings.scss
* _links.scss
* _table.scss

**Components**
* _accordion.scss
* _buttons.scss
* _slideshow.scss

**Utilities**
* _margin.scss
* _padding.scss
* _text.scss

### Prefixed names

I prefix each variable, tool and style to highlight its ITCSS level:

* Tools — _t-name_
* Settings — _s-name_
* Objects — _o-name_
* Components — _c-name_
* Utilities — _u-name_

This is _very_ useful when it comes to debugging, or generally identifying where the CSS is situated in the folder structure. To further aid findability, I also ensure that variable/style names contain the file name:

```css
/* 2. Settings/_colour.scss */

$s-colour-primary: red;
$s-colour-secondary: blue;
$s-colour-mono-1: black;
$s-colour-mono-2: grey;
```

```css
/* 2. Settings/_layout.scss */

$s-layout-small: 10px;
$s-layout-medium: 20px;
$s-layout-large: 30px;
```

```css
/* 6. Components/_button.scss */

$c-button {}
```

```css
/* 7. Utilities/_text.scss */

$u-text-center {text-align: center;}
$u-text-left {text-align: left;}
$u-text-right {text-align: right;}

$u-text-bold {font-weight: bold;}

$u-text-underline {text-decoration: underline;}
```

## Further reading
<a href="https://www.xfive.co/blog/itcss-scalable-maintainable-css-architecture/" target="_blank">ITCSS: Scalable and Maintainable CSS Architecture</a>

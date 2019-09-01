---
layout: post
title:  "How I use BEM"
date:   2019-08-30 19:00:00
label: post
description: BEM is a naming convention that can be used to break a website’s CSS into super useful, reusable components.
---
## Introduction

BEM is a naming convention that can be used to break a website’s CSS into super useful, reusable components. This means that components can be organised effectively for ongoing and future development, and they are also easily extendable.

BEM stands for Block Element Modifier, which describes the classes used to build up a single component.

Let’s use the context of a bike to describe how to create a BEM component.

## Block

A Block works like the outer container for the component and the namespace for the entire component. In this example, the Block would be "bike", and all further classes (Elements and Modifiers) that make up this component should be prepended with "bike".

```html
<div class="bike"></div>
```

```scss
.bike {}
```

## Element

An Element is a child within the Block. Elements are described using the Block followed by 2 underscores followed by the Element, e.g. "block__element"

```html
<div class="bike">
    <div class="bike__handlebar"></div>
    <div class="bike__seat"></div>
    <div class="bike__frame"></div>
    <div class="bike__wheel"></div>
    <div class="bike__wheel"></div>
</div>
```

```scss
.bike {
    &__handlebar {}
    &__seat {}
    &__frame {}
    &__wheel {}
}
```

Note, that Elements can be nested in the markup, however the CSS should always remain flat, i.e. chaining of elements ("block__element__another-element”) should be avoided.

```html
<div class="bike">
    <div class="bike__handlebar">
        <div class="bike__handle"></div>
        <div class="bike__handle"></div>
        <div class="bike__bell"></div>
    </div>
    <div class="bike__seat"></div>
    <div class="bike__frame"></div>
    <div class="bike__wheel"></div>
    <div class="bike__wheel"></div>
</div>
```

```scss
.bike {
    &__handlebar {}
    &__handle {}
    &__bell {}
    &__seat {}
    &__frame {}
    &__wheel {}
}
```

## Modifier

A Modifier is an alternative look for an Block or an Element. Modifiers are described using the Block/Element followed by 2 hyphens followed by the Modifier, e.g. "block--modifier", "block__element--modifier"

```html
<div class="bike bike--bmx">
    <div class="bike__handlebar">
        <div class="bike__handle"></div>
        <div class="bike__handle"></div>
        <div class="bike__bell"></div>
    </div>
    <div class="bike__seat bike__seat--large"></div>
    <div class="bike__frame"></div>
    <div class="bike__wheel"></div>
    <div class="bike__wheel"></div>
</div>
```

```scss
.bike {
    &--bmx {}

    &__handlebar {}
    &__handle {}
    &__bell {}
    &__seat {
        &--large
    }
    &__frame {}
    &__wheel {}
}
```

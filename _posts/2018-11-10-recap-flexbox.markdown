---
layout: post
title:  "Flexbox Recap"
date:   2018-11-10 17:00:00
label: note
---

## TL; DR

<table>
    <tr>
        <th>Element</th>
        <th>Property</th>
        <th>Values</th>
        <th>Default</th>
    </tr>
    <tr>
        <th rowspan="7">flex-container</th>
        <td>display</td>
        <td>flex | inline-flex</td>
        <td>N/A</td>
    </tr>
    <tr>
        <td>flex-direction</td>
        <td>row | row-reverse | column | column-reverse</td>
        <td>row</td>
    </tr>
    <tr>
        <td>flex-wrap</td>
        <td>nowrap | wrap | wrap-reverse</td>
        <td>nowrap</td>
    </tr>
    <tr>
        <td>flex-flow</td>
        <td>&lt;'flex-direction'&gt; || &lt;'flex-wrap'&gt;</td>
        <td>row nowrap</td>
    </tr>
    <tr>
        <td>justify-content</td>
        <td>flex-start | flex-end | center | space-between | space-around | space-evenly</td>
        <td>flex-start</td>
    </tr>
    <tr>
        <td>align-items</td>
        <td>flex-start | flex-end | center | baseline | stretch</td>
        <td>stretch</td>
    </tr>
    <tr>
        <td>align-content</td>
        <td>flex-start | flex-end | center | space-between | space-around | stretch</td>
        <td>stretch</td>
    </tr>
    <tr>
        <th rowspan="6">flex-item</th>
        <td>order</td>
        <td>&lt;number-with-no-unit&gt;</td>
        <td>0</td>
    </tr>
    <tr>
        <td>flex-basis</td>
        <td>&lt;number-with-unit&gt; | auto</td>
        <td>auto</td>
    </tr>
    <tr>
        <td>flex-grow</td>
        <td>&lt;number-with-no-unit&gt;</td>
        <td>0</td>
    </tr>
    <tr>
        <td>flex-shrink</td>
        <td>&lt;number-with-no-unit&gt;</td>
        <td>1</td>
    </tr>
    <tr>
        <td>flex</td>
        <td>none | &lt;'flex-grow'&gt; &lt;'flex-shrink'&gt; || &lt;'flex-basis'&gt;</td>
        <td>0 1 auto</td>
    </tr>
    <tr>
        <td>align-self</td>
        <td>auto | flex-start | flex-end | center | baseline | stretch</td>
        <td>auto</td>
    </tr>
</table>

## Parent properties (flex container)

**display**

Enables a flex context for all direct children.

``` css
.flex-container {
    display: flex | inline-flex;
}
```

<p data-height="262" data-theme-id="dark" data-slug-hash="oQjNdP" data-default-tab="result" data-user="howarddyer" data-pen-title="1/11: Flexbox display example" class="codepen">See the Pen <a href="https://codepen.io/howarddyer/pen/oQjNdP/">1/11: Flexbox display example</a> by Howard Dyer (<a href="https://codepen.io/howarddyer">@howarddyer</a>) on <a href="https://codepen.io">CodePen</a>.</p>
<script async src="https://static.codepen.io/assets/embed/ei.js"></script>

**flex-direction**

Defines the main axis of the flex context.

``` css
.flex-container {
    flex-direction: row | row-reverse | column | column-reverse; /* default: row */
}
```

<p data-height="260" data-theme-id="dark" data-slug-hash="NEGWXq" data-default-tab="result" data-user="howarddyer" data-pen-title="2/11: Flexbox flex-direction example" class="codepen">See the Pen <a href="https://codepen.io/howarddyer/pen/NEGWXq/">2/11: Flexbox flex-direction example</a> by Howard Dyer (<a href="https://codepen.io/howarddyer">@howarddyer</a>) on <a href="https://codepen.io">CodePen</a>.</p>
<script async src="https://static.codepen.io/assets/embed/ei.js"></script>

**flex-wrap**

Flex items will, by default, naturally try and fit onto one line. This property can be used to redefine this behaviour.

``` css
.flex-container {
    flex-wrap: nowrap | wrap | wrap-reverse; /* default: nowrap */
}
```

<p data-height="320" data-theme-id="dark" data-slug-hash="bQbOeK" data-default-tab="result" data-user="howarddyer" data-pen-title="3/11: Flexbox flex-wrap example" class="codepen">See the Pen <a href="https://codepen.io/howarddyer/pen/bQbOeK/">3/11: Flexbox flex-wrap example</a> by Howard Dyer (<a href="https://codepen.io/howarddyer">@howarddyer</a>) on <a href="https://codepen.io">CodePen</a>.</p>
<script async src="https://static.codepen.io/assets/embed/ei.js"></script>

**flex-flow**

Shorthand for ```flex-direction``` and ```flex-wrap```.

``` css
.flex-container {
    flex-flow: <'flex-direction'> || <'flex-wrap'>; /* default: row nowrap */
}
```

**justify-content**

Controls the alignment/distribution of flex items along the main axis.

``` css
.flex-container {
    justify-content: flex-start | flex-end | center | space-between | space-around | space-evenly; /* default: flex-start */
}
```

<p data-height="263" data-theme-id="dark" data-slug-hash="vQNYrb" data-default-tab="result" data-user="howarddyer" data-pen-title="4/11: Flexbox justify-content example" class="codepen">See the Pen <a href="https://codepen.io/howarddyer/pen/vQNYrb/">4/11: Flexbox justify-content example</a> by Howard Dyer (<a href="https://codepen.io/howarddyer">@howarddyer</a>) on <a href="https://codepen.io">CodePen</a>.</p>
<script async src="https://static.codepen.io/assets/embed/ei.js"></script>

**align-items**

Controls the alignment/distribution of flex items along the cross axis (affecting each individual line of flex items).

``` css
.flex-container {
    align-items: flex-start | flex-end | center | baseline | stretch; /* default: stretch */
}
```

<p data-height="505" data-theme-id="dark" data-slug-hash="xQwxJj" data-default-tab="result" data-user="howarddyer" data-pen-title="5/11: Flexbox align-items example" class="codepen">See the Pen <a href="https://codepen.io/howarddyer/pen/xQwxJj/">5/11: Flexbox align-items example</a> by Howard Dyer (<a href="https://codepen.io/howarddyer">@howarddyer</a>) on <a href="https://codepen.io">CodePen</a>.</p>
<script async src="https://static.codepen.io/assets/embed/ei.js"></script>

**align-content**

Controls the alignment/distribution of multiple lines of flex items along the cross axis (affecting multiple lines of flex items as one).

``` css
.flex-container {
    align-content: flex-start | flex-end | center | space-between | space-around | stretch; /* default: stretch */
}
```

<p data-height="395" data-theme-id="dark" data-slug-hash="PxPoxY" data-default-tab="result" data-user="howarddyer" data-pen-title="6/11: Flexbox align-content example" class="codepen">See the Pen <a href="https://codepen.io/howarddyer/pen/PxPoxY/">6/11: Flexbox align-content example</a> by Howard Dyer (<a href="https://codepen.io/howarddyer">@howarddyer</a>) on <a href="https://codepen.io">CodePen</a>.</p>
<script async src="https://static.codepen.io/assets/embed/ei.js"></script>

## Children properties (flex items)

**order**

Flex items are, by default, laid out in source order. This property can be used to redefine this for each individual flex item.

``` css
.flex-item {
    order: <number-with-no-unit>; /* default: 0 */
}
```

<p data-height="263" data-theme-id="dark" data-slug-hash="EOVxrE" data-default-tab="result" data-user="howarddyer" data-pen-title="7/11: Flexbox order example" class="codepen">See the Pen <a href="https://codepen.io/howarddyer/pen/EOVxrE/">7/11: Flexbox order example</a> by Howard Dyer (<a href="https://codepen.io/howarddyer">@howarddyer</a>) on <a href="https://codepen.io">CodePen</a>.</p>
<script async src="https://static.codepen.io/assets/embed/ei.js"></script>

**flex-basis**

Defines the default size of an element along the main axis, before it is manipulated by other properties. The value given is a ratio, for example:
* if all flex items have ```flex-basis: 1;```, the space will be shared out evenly.
* if all flex items have ```flex-basis: 1;``` except for one that has ```flex-basis: 2;```, the latter will take up twice the amount of space of the former.

``` css
.flex-item {
    flex-basis: <number-with-unit> | auto; /* default: auto */
}
```

<p data-height="261" data-theme-id="dark" data-slug-hash="gQaOyO" data-default-tab="result" data-user="howarddyer" data-pen-title="8/11: Flexbox flex-basis example" class="codepen">See the Pen <a href="https://codepen.io/howarddyer/pen/gQaOyO/">8/11: Flexbox flex-basis example</a> by Howard Dyer (<a href="https://codepen.io/howarddyer">@howarddyer</a>) on <a href="https://codepen.io">CodePen</a>.</p>
<script async src="https://static.codepen.io/assets/embed/ei.js"></script>

**flex-grow**

Defines the extent of the flex item's ability to grow. This property controls how free space can be occupied by flex items, when the entirety of the main axis is not filled.

``` css
.flex-item {
    flex-grow: <number-with-no-unit>; /* default: 0 */
}
```

<p data-height="263" data-theme-id="dark" data-slug-hash="bQVGyp" data-default-tab="result" data-user="howarddyer" data-pen-title="9/11: Flexbox grow example" class="codepen">See the Pen <a href="https://codepen.io/howarddyer/pen/bQVGyp/">9/11: Flexbox grow example</a> by Howard Dyer (<a href="https://codepen.io/howarddyer">@howarddyer</a>) on <a href="https://codepen.io">CodePen</a>.</p>
<script async src="https://static.codepen.io/assets/embed/ei.js"></script>

**flex-shrink**

Defines the extent of the flex item's ability to shrink. This property comes into play when the container is too small to contain the flex items.

``` css
.flex-item {
    flex-shrink: <number-with-no-unit>; /* default: 1 */
}
```

<p data-height="264" data-theme-id="dark" data-slug-hash="YRyzbM" data-default-tab="result" data-user="howarddyer" data-pen-title="10/11: Flexbox shrink example" class="codepen">See the Pen <a href="https://codepen.io/howarddyer/pen/YRyzbM/">10/11: Flexbox shrink example</a> by Howard Dyer (<a href="https://codepen.io/howarddyer">@howarddyer</a>) on <a href="https://codepen.io">CodePen</a>.</p>
<script async src="https://static.codepen.io/assets/embed/ei.js"></script>

**flex**

Shorthand for ```flex-grow```, ```flex-shrink``` and ```flex-basis```.

``` css
.flex-item {
    flex: none | <'flex-grow'> <'flex-shrink'> || <'flex-basis'>; /* default: 0 1 auto */
}
```

**align-self**

This property mirrors the behaviour of the flex container's ```align-content``` property, but can be used to override individual flex items.

``` css
.flex-item {
    align-self: auto | flex-start | flex-end | center | baseline | stretch; /* default: auto */
}
```

<p data-height="399" data-theme-id="dark" data-slug-hash="qQOBzQ" data-default-tab="result" data-user="howarddyer" data-pen-title="11/11: Flexbox align-self example" class="codepen">See the Pen <a href="https://codepen.io/howarddyer/pen/qQOBzQ/">11/11: Flexbox align-self example</a> by Howard Dyer (<a href="https://codepen.io/howarddyer">@howarddyer</a>) on <a href="https://codepen.io">CodePen</a>.</p>
<script async src="https://static.codepen.io/assets/embed/ei.js"></script>

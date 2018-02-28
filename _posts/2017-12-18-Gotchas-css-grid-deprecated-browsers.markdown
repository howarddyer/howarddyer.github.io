---
layout: post
title:  "Gotchas When Implementing CSS Grid in Deprecated Browsers"
date:   2017-12-19 20:50:00
description: "CSS Grid is a modern technology for modern browsers. In an ideal world we would only develop for modern browsers, but there are (unfortunately) still many instances that call for the continued support of deprecated browsers."
---

When using CSS Grid in IE10, IE11 and Edge (15 and below), implementation is based on the <a href="https://www.w3.org/TR/2011/WD-css3-grid-layout-20110407/" target="_blank">2011 implementation of CSS Grid</a>. There are a few things that need to be considered whenever support for those browsers is required.

### Gotcha 1: The repeat function

To create a 4 column grid in CSS grid, the repeat function can be used as follows:

``` css
.grid {
    grid-template-columns: repeat(4, 60px);
}
```

However, the repeat function was included after the 2011 implementation. To allow the same behaviour in deprecated browsers, the values need to be written out fully using the prefixed property for "grid-template-columns":

``` css
.grid {
    -ms-grid-columns: 60px 60px 60px 60px;
    grid-template-columns: repeat(4, 60px);
}
```

### Gotcha 2: Autoplacement

Autoplacement in CSS Grid is a set of rules that automatically places items that have not been explicitly placed within the grid. For example, consider the following:

``` html
<div class=”grid”>
    <p class=”column-1”>First column</p>
    <p class=”column-2”>Second column</p>
</div>
```

The autoplacement of these items, as per the current implementation, would result in the following layout:

![Autoplacement, as per the current CSS Grid implementation](/static/images/posts/2017-12-18-grid-normal.png "Autoplacement, as per the current CSS Grid implementation")

Unfortunately, Autoplacement is not featured in the 2011 implementation. Therefore, the same layout in deprecated browsers causes the items to stack up in the first cell of the grid.

![Autoplacement, as per the 2011 CSS Grid implementation](/static/images/posts/2017-12-18-grid-ie.png "Autoplacement, as per the 2011 CSS Grid implementation")

To get around this, items must be placed manually using the prefixed property for "grid-template-columns".

``` css
.column-2 {
    -ms-grid-column: 2;
}
```

### Gotcha 3: The grid gap property (creating a grid with grid gap)

The "grid-column-gap", "grid-row-gap" and "grid-gap properties" can be used to add gutters between columns in a grid. For example, adding 20 pixel gutters to the grid in [Gotcha 1](#gotcha-1-the-repeat-function) and [Gotcha 2](#gotcha-2-autoplacement) would result in the following layout:

![Using grid gap in CSS Grid, as per the 2011 CSS Grid implementation](/static/images/posts/2017-12-18-grid-gap.png "Using grid gap in CSS Grid, as per the 2011 CSS Grid implementation")

Unfortunately, these properties are not available in the 2011 implementation. A work around is to create extra columns using the prefixed property for "grid-template-columns" to act as gutters in deprecated browsers.

``` css
grid {
    -ms-grid-columns: 60px 20px 60px 20px 60px 20px 60px;
    grid-template-columns: repeat(4, 60px);
    grid-column-gap: 20px;
}
```

### Gotcha 4: The grid gap property (placing items within a grid with grid gap)

Within a grid that incorporates grid gap, manually placed items will need adjusting. For example, using "-ms-grid-column: 2"; in the workaround mentioned in [Gotcha 3](gotcha-3-the-grid-gap-property-creating-a-grid-with-grid-gap) would place the item into the grid gutter. A workaround would be to use the following:

``` css
.column-2 {
    -ms-grid-column: 3;
}
```

Tip: The following could be used to automate this value, where $i represents the placement of an item in the current implementation:

```
// The value of column placement $i in the 2011 implementation

$i + ($i - 1)
```

If you wish to use a SASS mixin to generate item placement for both implementations, use the following:

``` scss
// Column placement in a 4 column grid, creating.column-1 through to .column-4

@for $i from 1 through 4 {
    .column-#{ $i } {
        -ms-grid-column-span: $i + ($i - 1);
        grid-column-end: span $i;
    }
}
```


### Gotcha 5: the span keyword

The "span" keyword is not featured in the 2011 implementation. There are equivalent property prefixes that you can use instead:

``` css
.second-column {
    -ms-grid-column-span: 4;
    grid-column: span 4;
}
```

### Conclusion

CSS Grid is a modern technology for modern browsers. In an ideal world we would only develop for modern browsers, but there are (unfortunately) still many instances that call for the continued support of deprecated browsers.

CSS Grid will really begin to shine when it is not held back by the limitations of deprecated browsers.

### Further reading:

<a href="https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Grid_Layout/CSS_Grid_and_Progressive_Enhancement" target="_blank">List of prefixed CSS Grid properties, visit MDN Web Docs</a>

<a href="https://www.w3.org/TR/2011/WD-css3-grid-layout-20110407/" target="_blank">2011 implementation of CSS Grid</a>

<a href="https://www.w3.org/TR/css3-grid-layout/" target="_blank">Current implementation of CSS Grid</a>

---
layout: post
title:  "Most Useful CSS Grid Properties and Their Shorthands"
date:   2017-08-09 19:31:00
description: "If nothing else, ensure you learn how to use grid-template, grid-area and grid-gap."
---

### Explicit grid properties

* grid-template-rows: \<line-names> \<track-size> ... \| none;
* grid-template-columns: \<line-names> \<track-size> ... \| none;
* grid-template-areas: \<area-names> \| . \| none;

``` css
.grid {
  grid-template-rows:
    [row-1-start] 1fr [row-1-end]
    [row-2-start] 1fr [row-2-end]
    [row-3-start] 1fr [row-3-end]
    [row-4-start] 1fr [row-4-end];
  grid-template-columns:
    [col-1-start] 1fr [col-1-end col-2-start] 1fr [col-2-end col-3-start] 1fr [col-3-end];
  grid-template-areas:
    "header header header"
    "main main sidebar"
    ". . ."
    "footer footer footer";
}
```

**Shorthand:** grid-template: \<line-names> \<track-size> \<area-names> \<line-names> / \<grid-template-columns> ... \| subgrid \| none;

``` css
.grid {
  grid-template:
    [row-1-start] 1fr "header header header" [row-1-end]
    [row-2-start] 1fr "main main sidebar" [row-2-end]
    [row-3-start] 1fr ". . ." [row-3-end]
    [row-4-start] 1fr "footer footer footer" [row-4-end] /
    [col-1-start] 1fr [col-1-end col-2-start] 1fr [col-2-end col-3-start] 1fr [col-3-end];
}
```

* grid-row-gap: \<gap-size>;
* grid-column-gap: \<gap-size>;

``` css
.grid {
  grid-row-gap: 10px;
  grid-column-gap: 20px;
}
```

**Shorthand:** grid-gap: \<grid-row-gap> \<grid-column-gap>;

``` css
.grid {
  grid-gap: 10px 20px;
}
```

**Note** the bracket syntax for line names and quotation syntax for area names.  

### Implicit grid properties

* grid-auto-rows: \<track-size> ... \| min-content \| max-content \| auto;
* grid-auto-columns: \<track-size> ... \| min-content \| max-content \| auto;
* grid-auto-flow: [ row \| column ] dense;

``` css
.grid {
  grid-auto-rows: 200px;
  grid-auto-columns: 200px;
  grid-auto-flow: row dense;
}
```

### Grid item properties

* grid-row-start: \<line-name> | \<number> \| span [ \<line-name> | \<number> ] \| auto;
* grid-row-end: \<line-name> | \<number> \| span [ \<line-name> | \<number> ] \| auto;

``` css
.grid-item {
  grid-row-start: 2;
  grid-row-end: span 2;
}
```

**Shorthand:** grid-row: \<grid-row-start> / \<grid-row-end>;

``` css
.grid-item {
  grid-row: 2 / span 2;
}
```

* grid-column-start: \<line-name> | \<number> \| span [ \<line-name> | \<number> ] \| auto;
* grid-column-end: \<line-name> | \<number> \| span [ \<line-name> | \<number> ] \| auto;

``` css
.grid-item {
  grid-column-start: 1;
  grid-column-end: 4;
}
```

**Shorthand:** grid-column: \<grid-column-start> / \<grid-column-end>;

``` css
.grid-item {
  grid-column: 1 / 4;
}
```

**Shorthand:** grid-area: \<area-name> \| \<grid-row-start> / \<grid-column-start> / \<grid-row-end> / \<grid-column-end>;

``` css
.grid-item {
  grid-area: 2 / 1 / span 2 / 4;
}
```

### Conclusion

If nothing else, ensure you learn how to use:
* grid-template
* grid-area
* grid-gap

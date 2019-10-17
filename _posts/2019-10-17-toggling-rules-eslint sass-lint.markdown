---
layout: post
title:  "Toggling rules in ESLint and Sass Lint"
date:   2019-10-17 17:00:00
label: note
---

## Disable rule-name in file

```js
/* eslint-disable rule-name */
```

```css
// sass-lint: disable rule-name
```


## Disable rule-name on current line

```js
/* eslint-disable-line rule-name */
```

```css
// sass-lint: disable-line rule-name
```

## Disable rule-name on next line

```js
/* eslint-disable-next-line rule-name */
```

## Disable rule-name in current block

```css
// sass-lint: disable-block rule-name
```

## Disable all rules

```js
/* eslint-disable */
```

```css
// sass-lint: disable-all
```

## Enable all rules

```js
/* eslint-enable*/
```

```css
// sass-lint: enable-all
```
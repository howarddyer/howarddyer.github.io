---
layout: post
title:  "Manipulate CSS Custom Properties Using JavaScript"
date:   2020-05-30 00:00:00
label: note
---

```javascript
function readCssVariable (elementNode, customProperty){
  const elementStyles = getComputedStyle(elementNode);

  return elementStyles.getPropertyValue(`--${customProperty}`).trim();
}


function writeCssVariable (elementNode, customProperty, value){
  return elementNode.style.setProperty(`--${customProperty}`, value);
}
```

## Resources

<a href="https://www.smashingmagazine.com/2017/04/start-using-css-custom-properties/" target="_blank">It’s Time To Start Using CSS Custom Properties by Serg Hospodarets | Smashing Magazine</a>
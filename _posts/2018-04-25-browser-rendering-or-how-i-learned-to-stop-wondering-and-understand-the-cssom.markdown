---
layout: post
title:  "Browser Rendering or: How I Learned to Stop Wondering and Understand the CSSOM"
date:   2018-04-25 17:00:00
description: "A brief documentation of the steps that the browser takes to render the CSSOM, to better understand how/why the CSSOM plays such a vital role in the rendering of content on the web."
label: post
---

### Introduction

I listened to <a href="http://shoptalkshow.com/episodes/306-debugging-css-aimee-knight/" target="_blank">episode 306 of the Shoptalk Show</a> featuring <a href="https://twitter.com/Aimee_Knight" target="_blank">Aimee Knight</a> (of Javascript Jabber fame) in which she talks about the CSSOM. Before this, the CSSOM was a relatively unknown concept to me, even though it plays a pivotal role during the rendering of content on the web.

### What is the CSSOM?
The CSSOM stands for CSS Object Model, and in principal, is the same deal as the DOM (Document Object Model), except that where the DOM relates to the content of a HTML file, the CSSOM relates to the content of a CSS file. What follows is a brief documentation of the steps that the browser takes to render the CSSOM, to better understand how/why the CSSOM plays such a vital role in the rendering of content on the web.

### How the browser renders content (in brief)
The following steps start after the point that the browser has received a response from the server:

1. **DOM:** The browser downloads and parses the HTML file, and then undergoes a process to build the DOM
    - Raw bytes of the HTML file are read
    - Bytes are translated to characters based on encoding of file
    - Characters are converted into distinct tokens as specified by the <a href="https://www.w3.org/TR/html52/" target="_blank">W3C HTML5 Standard</a>
    - Tokens are converted to objects (resembling nodes) with defined properties and rules
    - Objects are aligned into a tree data structure
2. **CSSOM:** When the browser encounters an external CSS file in the HTML, it downloads and parses the CSS file, and undergoes the same process to build the CSSOM
    - Raw bytes of the CSS file are read
    - Bytes are translated to characters based on encoding of file
    - Characters are converted into distinct tokens as specified by the <a href="https://www.w3.org/TR/CSS22/" target="_blank">W3C CSS3 Standard</a>
    - Tokens are converted to objects (resembling nodes) with defined properties and rules
    - Objects are aligned into a tree data structure
3. **Render Tree:** It's important to note that CSS is a render blocking resource. This is because the Render Tree (i.e. what you actually see) relies on the CSSOM being fully constructed, and whilst the CSSOM is being constructed, no other process will be allowed to proceed. So, once the DOM and CSSOM are constructed, they are merged using the following steps to create the Render Tree
    - Each visible node within the DOM (i.e. not the head element, script tags, etc) are transversed
    - Appropriate CSS rules are identified in the CSSOM and applied (if a node is hidden via CSS, for example particularly using "display: none;" then it is omitted)
    - The node is emitted with its content and computed styles
4. Once the Render Tree is created, the browsers undergoes a set of render stages to actually display the content
    - **Layout:** The browser transverses the Render Tree and uses each nodes computed styles to precisely capture its geometry (size and position)
    - **Painting:** Each node in the Render Tree is converted to pixels on screen using multiple layers, which govern the order in which objects are painted (from back to front)
    - **Compositing:** All layers are flattened into the final image

### Conclusion
Having a more in-depth understanding of how the actually browser renders content is a heuristic hack to producing more informed, efficient and performant code. In a future post, I'll explore more about how this knowledge can be used to level-up your code.

### Further Reading

<a href="http://howard-dyer.co.uk/speeding-up-the-critical-rendering-path.html" target="_blank">Speeding Up the Critical Rendering Path — Howard Dyer</a>

<a href="http://howard-dyer.co.uk/improving-the-render.html" target="_blank">Improving the Render — Howard Dyer</a>

<a href="http://www.aimeemarieknight.com/It's-Not-Dark-Magic-Pulling-Back-the-Curtains-From-Your-Stylesheets/" target="_blank">It's Not Dark Magic: Pulling Back The Curtains From Your Stylesheets - Aimee Knight</a>

<a href="https://developers.google.com/web/fundamentals/performance/critical-rendering-path/constructing-the-object-model" target="_blank">Constructing the Object Model — Google Developers</a>

<a href="https://developers.google.com/web/fundamentals/performance/critical-rendering-path/render-tree-construction" target="_blank">Render-tree Construction, Layout, and Paint — Google Developers</a>

<a href="https://m.youtube.com/watch?v=SmE4OwHztCc" target="_blank">Ryan Seddon: So how does the browser actually render a website (video)</a>

<a href="https://www.youtube.com/watch?v=ZTnIxIA5KGw" target="_blank">Gecko Reflow Visualization - mozilla.org</a>

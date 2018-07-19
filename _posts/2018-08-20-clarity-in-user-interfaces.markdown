---
layout: post
title:  "Clarity In User Interfaces"
date:   2018-08-20 00:00:00
description: "A topic was discussed on episode 271 of the Shoptalk show that I want to explore further. The subject was around pagination and the correct placement of the 'Next' and 'Previous' buttons (on the left or the right). I feel that this discussion alludes to deeper routed issues in UI."
label: post
---

### Introduction

A topic was discussed on <a href="http://shoptalkshow.com/episodes/271-headless-material-sass-queries/" target="_blank">episode 271 of the Shoptalk show</a> that I want to explore further. The subject was around pagination and the correct placement of the 'Next' and 'Previous' buttons (on the left or the right).

I feel that this discussion alludes to deeper routed issues in UI.

### Issue 1: Baking in perspective

In westernised languages such as English, we read from left to right, and this clearly forms the way we approach many other problems. Our calendars are read left-to-right, our songs in our music players are scrubbed from left-to-right, maybe even our post-it notes on our desk are ordered from left-to-right.

However since many other languages are read/written from right-to-left or even top-to-bottom, this is clearly a narrow and limiting perspective.

### Issue 2: Baking in context

Imagine that there is a website containing several pages of news articles and the pagination includes buttons with the labels 'Previous' and 'Next'. The articles on the website are sorted by date and time.

![Unclear pagination using next and previous buttons](/static/images/posts/2018-08-20-pagination.png "Unclear pagination using next and previous buttons")

Different people will visit a website for different purposes, but if, in the example above, you were intending on getting the most recent episode, which button would you press? Or more to the point, **how would you know** which button to press?

### Clarity in labels

Both of these issues can be addressed by improving the text within the buttons.

In the example above, if the buttons were renamed to 'Newer articles' and 'Older articles', then their contexts would be very clear and there would be no room for interpretation &mdash; you would easily be able to find what you were looking for. Either button could be placed on the left or the right as this would not in any way obscure what the button does.


### Conclusion

It is very easy to rely on your own perspective, however not everyone shares this. Creating UIs with reliance on your own perspective often gives the end user more questions than answers.

Chris discussed on the episode that this is "not a solved problem", which is certainly true. There's no correct or incorrect way to layout the buttons, however there are certainly *clear* and *unclear* approaches.

### Resources

<a href="http://shoptalkshow.com/episodes/271-headless-material-sass-queries/" target="_blank">Headless Material Sass Queries — Shoptalk Show</a>

### Further reading

<a href="https://www.goodreads.com/book/show/18197267-don-t-make-me-think-revisited" target="_blank">Don't Make Me Think: , Revisited: A Common Sense Approach to Web Usability by Steve Krug</a>

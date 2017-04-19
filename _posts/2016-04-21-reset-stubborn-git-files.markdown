---
layout: post
title:  "Reset stubborn git files"
date:   2016-04-21 19:12:44
description:
  nested:
    - description: "git rm --cached -r ."
    - description: "git reset --hard"
---

{% highlight shell %}
git rm --cached -r .
git reset --hard
{% endhighlight %}

---
layout: post
title:  "Create command line directory shortcuts"
date:   2015-05-15 00:44:53
description: "A solution to quickly access frequently used locations in the command line."
---

Open the .bash_profile file (at the root) for editing:

{% highlight shell %}
nano .bash_profile
{% endhighlight %}

Add your alias:

{% highlight -command-line %}
alias shortcutToMyDevFolder='cd /Path/To/My/Dev/Folder'
{% endhighlight %}

Save the file, and then refresh the shell:

{% highlight -command-line %}
source ~/.bash_profile
{% endhighlight %}

Alternatively, symlimks can be created with the "ln" command (so that typing "cd shortcutToMyDevFolder" will do the same).

{% highlight -command-line %}
ln -s /Path/To/My/Dev/Folder shortcutToMyDevFolder
{% endhighlight %}

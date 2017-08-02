---
layout: post
title:  "Using .htaccess"
date:   2015-06-03 00:44:53
description: "Helpful notes for using .htaccess."
categories: htaccess apache url redirect
---

### Is .htaccess enabled?

To test whether .htaccess is enabled on your web server, create two files with unique content and add the following to your .htaccess file (if the leftmost file is loaded, then .htaccess will be enabled):

{% highlight -directives %}
DirectoryIndex index_enabled.html index.html
{% endhighlight %}

### Error pages

404 error — "page not found":

{% highlight -directives %}
Redirect 404 /path/to/404-error-page.html
{% endhighlight %}

301 error — "moved permanently":

{% highlight -directives %}
Redirect 301 /path/to/old-page.html /path/to/new-page.html
{% endhighlight %}

### Rewrite

Redirect serves the browser a different URL to use, and the browser is aware of the redirect.
Rewrite is a set of conditional rules that leaves the client's browser none the wiser of the rewrie (in contrast to Redirect's if EXACTLY THIS do EXACTLY THAT nature).

A Rewrite request is made up of two parts&mdash;RewriteCond and RewriteRule. RewriteCond defines when the RewriteRule should be used and RewriteRule defines what is to be done.

Replace non-canonical URLs with a canonical URL (this is actually processed as a 301 redirect):

{% highlight -directives %}
RewriteCond %{HTTP_HOST} !^www
RewriteRule .* http://www.%{SERVER_NAME}%{REQUEST_URI} [R=301,L]
{% endhighlight %}

Remove any trailing slashes from the URL:

{% highlight -directives %}
RewriteCond %{REQUEST_FILENAME} !-d
RewriteRule ^(.*)/$ /$1 [L,R=301]
{% endhighlight %}

Remove index.html from the URL:

{% highlight -directives %}
RewriteCond %{REQUEST_URI} ^.*/index.html
RewriteRule ^(.*)index.html$ /$1 [R=301,L]
{% endhighlight %}

Set rules for search engine robots:

{% highlight -directives %}
<FilesMatch "sitemap\.xml">
  Header set X-Robots-Tag "noindex, nofollow"
</FilesMatch>
{% endhighlight %}

### Further reading

<p><a href="https://developers.google.com/webmasters/control-crawl-index/docs/robots_meta_tag" target="_blank">Apache HTTP server</a></p>
<p><a href="http://httpd.apache.org/docs/current/howto/htaccess.html" target="_blank">Google Robots Meta Tag</a></p>

---
layout: post
title:  "Using .htaccess"
date:   2015-06-03 00:44:53
description: "Helpful notes for using .htaccess."
label: note
---

## Is .htaccess enabled?

To test whether .htaccess is enabled on your web server, create two files with unique content and add the following to your .htaccess file (if the leftmost file is loaded, then .htaccess will be enabled):

``` apache
DirectoryIndex index_enabled.html index.html
```

## Error pages

404 error — "page not found":

``` apache
Redirect 404 /path/to/404-error-page.html
```

301 error — "moved permanently":

``` apache
Redirect 301 /path/to/old-page.html /path/to/new-page.html
```

## Rewrite

Redirect serves the browser a different URL to use, and the browser is aware of the redirect.
Rewrite is a set of conditional rules that leaves the client's browser none the wiser of the rewrie (in contrast to Redirect's if EXACTLY THIS do EXACTLY THAT nature).

A Rewrite request is made up of two parts&mdash;RewriteCond and RewriteRule. RewriteCond defines when the RewriteRule should be used and RewriteRule defines what is to be done.

Replace non-canonical URLs with a canonical URL (this is actually processed as a 301 redirect):

``` apache
RewriteCond %{HTTP_HOST} !^www
RewriteRule .* http://www.%{SERVER_NAME}%{REQUEST_URI} [R=301,L]
```

Remove any trailing slashes from the URL:

``` apache
RewriteCond %{REQUEST_FILENAME} !-d
RewriteRule ^(.*)/$ /$1 [L,R=301]
```

Remove index.html from the URL:

``` apache
RewriteCond %{REQUEST_URI} ^.*/index.html
RewriteRule ^(.*)index.html$ /$1 [R=301,L]
```

Set rules for search engine robots:

``` apache
<FilesMatch "sitemap\.xml">
  Header set X-Robots-Tag "noindex, nofollow"
</FilesMatch>
```

## Further reading

<p><a href="https://developers.google.com/webmasters/control-crawl-index/docs/robots_meta_tag" target="_blank">Apache HTTP server</a></p>
<p><a href="http://httpd.apache.org/docs/current/howto/htaccess.html" target="_blank">Google Robots Meta Tag</a></p>

---
id: 2951
title: 'Jekyll Migration'
date: '2024-12-21T20:08:00-08:00'
author: 'Aaron Lord'
layout: post
guid: 'https://blog.devlord.io/?p=2951'
permalink: /2024/12/21/jekyll-migration/
footnotes:
    - ''
activitypub_status:
    - federated
categories:
    - General
tags:
    - technology
    - programming
---

So there's more going on at Wordpress. The boss (Matt Mullenweg) isn't sure he's going to bring the open-source org back online after the new year. Even though I had meant to use Medium for new content, I wanted to preserve the archive of the last 20 years in a more sustainable manner.

So I spent the first day of my Christmas vacation migrating to Jekyll. First I used a cool "Jekyll Exporter" Wordpress plugin to download all posts as markdown files (they're still html, actually), and all my attached images. Then I installed Ruby and Jekyll on my System76 Linux laptop. Ran some tests and I had to figure out how to set up the landing page with a blogroll. Then I picked a theme. Eventually I figured out the pagination feature, which was good because before there were 1,000 posts on my home page!

I checked it all in to Git. Switched to my Macbook, installed Ruby and Jekyll again. Ran some more tests. Set it up with GitHub Pages.

I moved all my images to `/assets/img/` and used SublimeText to change the paths in all the posts.

I discovered that since I let a custom domain lapse on Wordpress.com from way before I migrated to Dreamhost, Wordpress.com had restored my site at my username.wordpress.com subdomain, and that's why Google wasn't indexing my content at devlord.io! So I set up the redirect all over again.

Now I'm just trying to figure out how to get the htaccess file working. According to an online tool I used, the following should redirect https://www.devlord.io/blog/my-post-here to https://blog.devlord.io/my-post-here.

```
RewriteEngine On
RewriteBase /
RewriteCond %{REQUEST_URI} !^blog/wp-admin.*
RewriteCond %{REQUEST_URI} !^blog/wp-json.*
RewriteCond %{REQUEST_URI} !^blog/wp-login.*
RewriteRule ^blog/(.*)$ https://blog.devlord.io/$1 [L,R=301]
```

But it's not working. Contacted support and they tried the same things I did. Turns out it was a cache issue on my end. In the end, all they did in the htaccess file was `Redirect 301 /blog https://blog.devlord.io`. No rules required.

Of course, this means I can't access my WP admin anymore. I spent some more time troubleshooting, but to no avail. I guess it's time to just rip the bandaid off.

So I'm on Jekyll with GitHub Pages now.

![Screenshot of me editing this actual post in Sublime Text](/assets/img/2024/12/screenshot.png)

---
id: 2096
title: 'New blog home'
date: '2024-03-04T17:15:05-08:00'
author: 'Aaron Lord'
layout: post
guid: 'https://blog.devlord.io/2024/03/04/new-blog-home/'
permalink: /2024/03/04/new-blog-home/
activitypub_status:
    - federated
    - federated
ast-site-content-layout:
    - default
theme-transparent-header-meta:
    - ''
adv-header-id-meta:
    - ''
stick-header-meta:
    - ''
astra-migrate-meta-layouts:
    - set
footnotes:
    - ''
categories:
    - Technology
---

<!-- wp:paragraph -->
<p>I've migrated my blog from mustfollow.wordpress.com to mustfollow.blog, and then off of Automattic's Wordpress.com entirely to self-hosted, now at blog.lorddev.com. I've changed the theme as my previous one was quite outdated. But the Tolkien quote doesn't really fit anymore, so I need to think of a new blog title.</p>
<!-- /wp:paragraph -->

<!-- wp:paragraph -->
<p>I set up an App Service Plan on Azure. Then after 1 day I was able to estimate costs, and I downgraded from a beefy production instance to a dev/test "Basic" one, and downgraded my MySQL DB as well. We'll see how this works.</p>
<!-- /wp:paragraph -->

<!-- wp:paragraph -->
<p>UPDATE: Azure costs were quite prohibitive even after downgrading. I was looking at $1.75/day. I migrated to Dreamhost instead. Their customer support has been great. I had to edit text directly in MySql because the export/import had inserted backslashes before every apostrophe and quotation mark, so that was fun (I hope it didn't break anything). New url is https://www.devlord.io/blog.</p>
<!-- /wp:paragraph -->
---
id: 2758
title: 'New blog home'
date: '2024-03-17T11:14:47-07:00'
author: 'Aaron Lord'
layout: revision
"guid: 'https://blog.devlord.io/?p=2758'
permalink: '/?p=2758'
footnotes:
    - ''
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
---
id: 1625
title: 'Abbreviations Considered Harmful'
date: '2012-07-07T22:08:09-07:00'
author: 'Aaron Lord'
layout: post
guid: 'https://blog.devlord.io/2012/07/07/abbreviations-considered-harmful/'
permalink: /2012/07/07/abbreviations-considered-harmful/
activitypub_status:
    - federated
tagazine-media:
    - 'a:7:{s:7:"primary";s:0:"";s:6:"images";a:0:{}s:6:"videos";a:0:{}s:11:"image_count";s:1:"0";s:6:"author";s:8:"28099389";s:7:"blog_id";s:8:"28571045";s:9:"mod_stamp";s:19:"2012-07-08 06:10:28";}'
categories:
    - Programming
    - Technology
tags:
    - coding
    - 'coding standards'
    - database
    - development
    - SQL
---

<p>I recently struggled for several hours over a sorted ASP.NET GridView control which was failing to behave properly. I found that on PostBack for the LinkButtons, the SortCommand was returning expressions such as &#8220;LocationDesc&#8221; and &#8220;PositionDesc&#8221;. I was confused as to why the sort direction was attached to the expression when it was already part of the SortDirection property of the EventArgs object, and assumed it might have had something to do with the way the other developers were persisting the sort data in ViewState. So I wrote a function to strip out the &#8220;Desc&#8221; from the sort expression, but as I got further in my testing, the database was telling me that &#8220;Location&#8221; and &#8220;Position&#8221; weren&#8217;t in the table. I checked to see if it was a matter of them not being included in the select statement vs. not being in the actual database table. When I looked at the database table, lo and behold, the fields were called &#8220;LocationDesc&#8221; and &#8220;PositionDesc&#8221;. Apparently &#8220;desc&#8221; is short for &#8220;description&#8221; (which is itself redundant). This results in such obviously horrid SQL statements as <code>select * from [mytable] order by locationdesc desc</code>. Terrible.</p>
<p>So I made a request to the rest of my team: let&#8217;s not do this anymore, okay? But they shot me down, as they always do. &#8220;We&#8217;ve always done it that way,&#8221; or, &#8220;That&#8217;s the naming convention they used in the legacy tables.&#8221;</p>
<p>It doesn&#8217;t matter if it sucked in the old days. That&#8217;s no reason to keep sucking! The fact that we&#8217;re still fixing things implies that what was done in the old days was not good enough. Let&#8217;s try not to suck anymore, okay?</p>
<p>&#8220;In general, you should not use abbreviations or acronyms. These make your names less readable.&#8221; —<a href="http://msdn.microsoft.com/en-us/library/ms229045.aspx" title="MSDN">Microsoft</a></p>
---
id: 1634
title: 'Visual Studio in the Cloud'
date: '2012-07-09T19:51:22-07:00'
author: 'Aaron Lord'
layout: post
guid: 'https://blog.devlord.io/2012/07/09/visual-studio-in-the-cloudcod/'
permalink: /2012/07/09/visual-studio-in-the-cloudcod/
activitypub_status:
    - federated
tagazine-media:
    - 'a:7:{s:7:"primary";s:65:"http://mustfollow.files.wordpress.com/2012/07/20120709-205029.jpg";s:6:"images";a:2:{s:65:"http://mustfollow.files.wordpress.com/2012/07/20120709-205029.jpg";a:6:{s:8:"file_url";s:65:"http://mustfollow.files.wordpress.com/2012/07/20120709-205029.jpg";s:5:"width";s:4:"1024";s:6:"height";s:3:"768";s:4:"type";s:5:"image";s:4:"area";s:6:"786432";s:9:"file_path";s:0:"";}s:65:"http://mustfollow.files.wordpress.com/2012/07/20120709-205119.jpg";a:6:{s:8:"file_url";s:65:"http://mustfollow.files.wordpress.com/2012/07/20120709-205119.jpg";s:5:"width";s:4:"1024";s:6:"height";s:3:"768";s:4:"type";s:5:"image";s:4:"area";s:6:"786432";s:9:"file_path";s:0:"";}}s:6:"videos";a:0:{}s:11:"image_count";s:1:"2";s:6:"author";s:8:"28099389";s:7:"blog_id";s:8:"28571045";s:9:"mod_stamp";s:19:"2012-07-10 04:00:56";}'
categories:
    - Programming
    - Technology
tags:
    - 'cloud computing'
    - ipad
    - 'visual studio'
format: standard
---

So, I have a couple of pending offers for side gigs lingering out there, and theoretically on any given weekend evening, someone could IM me and ask me to do a few small things for them. The problem is, I don't have a suitable Windows dev environment at home. I've had such great machines at the companies I've worked at for the last several years that I've been able to let my PC collect dust and just use my MacBook, iPad, and iPhone for whatever I needed a computer for at home. So, I thought I had better get something ready, and after a little bit of research, it became obvious that a cloud machine was going to be more economical than running up debt on a Best Buy card for a brand new Thinkpad. I found a few helpful resources online, including these <a href="http://blog.michaelckennedy.net/2011/06/13/building-a-cloud-os-for-net-developers-part-2/">two</a> <a href="http://www.michaelckennedy.net/blog/2010/01/31/BuildingWindowsMachinesInAmazonEC2.aspx">posts</a> from Michael Kennedy.

Here's my EC2 console.<br /><br /><a href="/assets/img/2012/07/20120709-205029.jpg"><img src="/assets/img/2012/07/20120709-205029.jpg" alt="20120709-205029.jpg" class="alignnone size-full" /></a>

I'm running Windows Server 2008 R2 with 7.5 GB of RAM. It will probably cost me about 50¢/hr. to run.

Here it is in action:<br /><br /><a href="/assets/img/2012/07/20120709-205119.jpg"><img src="/assets/img/2012/07/20120709-205119.jpg" alt="20120709-205119.jpg" class="alignnone size-full" /></a>

(I'll probably RDP from my MacBook more often.)
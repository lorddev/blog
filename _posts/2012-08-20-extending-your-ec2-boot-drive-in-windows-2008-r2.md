---
id: 1687
title: 'Extending your EC2 boot drive in Windows 2008 R2'
date: '2012-08-20T11:46:44-07:00'
author: 'Aaron Lord'
layout: post
guid: 'https://blog.devlord.io/2012/08/20/extending-your-ec2-boot-drive-in-windows-2008-r2/'
permalink: /2012/08/20/extending-your-ec2-boot-drive-in-windows-2008-r2/
activitypub_status:
    - federated
tagazine-media:
    - 'a:7:{s:7:"primary";s:62:"http://mustfollow.files.wordpress.com/2012/08/ec2-increase.png";s:6:"images";a:1:{s:62:"http://mustfollow.files.wordpress.com/2012/08/ec2-increase.png";a:6:{s:8:"file_url";s:62:"http://mustfollow.files.wordpress.com/2012/08/ec2-increase.png";s:5:"width";i:930;s:6:"height";i:581;s:4:"type";s:5:"image";s:4:"area";i:540330;s:9:"file_path";b:0;}}s:6:"videos";a:0:{}s:11:"image_count";i:1;s:6:"author";s:8:"28099389";s:7:"blog_id";s:8:"28571045";s:9:"mod_stamp";s:19:"2012-08-20 19:46:44";}'
categories:
    - Programming
    - Technology
tags:
    - amazon-ec2
    - asp.net
    - freelancing
    - windows
---

When you set up a new instance in the cloud <a href="http://mustfollow.wordpress.com/2012/07/09/visual-studio-in-the-cloudcod/">on Amazon's EC2 service</a>, if you use the standard snapshots for Windows 2008 R2 hosting with SQL Server, you will find that your C: drive is much smaller than you expected it to be. Basically, you're maxed out at capacity as soon as you upgrade Visual Studio. A few times a day you'll receive notifications in the system tray about how the drive is running out of disk space. My first attempt to solve this problem involved attaching an EBS volume as a D: drive, and using that for all of my downloads and SVN working copies. But even when I tried to uninstall some of the default applications (e.g. the C++ 2008 runtime, which I have no use for), I found that it didn't keep the drive from filling up. So I decided it was time to take a snapshot of the current state of my machine and see what I could do to grow that volume.

Fortunately, <a href="http://barriquesoft.com/?p=19">Sean Sullivan</a> has published an easy-to-follow outline of the steps...

<strong>Update:</strong> I happened to need to perform these steps again for a client, and the link above was not working. Basically you have to make a snapshot of the volume attached to your instance and use that to seed a new volume with a higher allocation, but then when you attach the new volume, the system still thinks it's smaller so you have to extend it. Here are the steps:
<ol>
	<li>Select your instance, go to the description tab and click on the volume link. It will tell you the volume ID.</li>
	<li>Stop your instance.</li>
	<li>Go find the volume in the Volumes tab and create a new snapshot, with a memorable name. (Pick something specific for the <em>description</em>. The drop-down where you will select this later will only show you the ID and description--not the name.) It will take a while. Use the <strong>refresh</strong> button in the Amazon web console to check your progress.</li>
	<li>Using the snapshot as the seed, create a new volume with a bigger size in the same availability zone as your instance. I think the actual volume size portion of the EC2 hosting fees is tiny, around $1/mo. for 10GB with 100% uptime.</li>
	<li>Select the original volume and detach it from your instance</li>
	<li>Attach your new larger volume to your instance as <code>/dev/sda1</code> (in the field where it says <code>xvdf</code>)</li>
	<li>Start your instance back up and RDP into it, then and go into Disk Management to extend your C: drive to its full capacity. (Remember to re-assign your Elastic IP if you are using one.)</li>
</ol>
[caption id="attachment_1688" align="alignnone" width="584"]<a href="/assets/img/2012/08/ec2-increase.png"><img class="size-full wp-image-1688" title="ec2-increase" alt="" src="/assets/img/2012/08/ec2-increase.png" width="584" height="364" /></a> Using Sean's method, I was successfully able to increase my C: drive capacity from 35 GB to 100 GB.[/caption]

And now I have a 100-GB C: drive on my cloud development machine!
---
id: 1676
title: 'Optimizing jQuery selectors for ASP.NET controls'
date: '2012-08-12T09:36:20-07:00'
author: 'Aaron Lord'
layout: post
guid: 'https://www.devlord.io/blog/2012/08/12/optimizing-jquery-selectors-for-asp-net-controls/'
permalink: /2012/08/12/optimizing-jquery-selectors-for-asp-net-controls/
activitypub_status:
    - federated
tagazine-media:
    - 'a:7:{s:7:"primary";s:0:"";s:6:"images";a:0:{}s:6:"videos";a:0:{}s:11:"image_count";i:0;s:6:"author";s:8:"28099389";s:7:"blog_id";s:8:"28571045";s:9:"mod_stamp";s:19:"2012-08-12 20:33:57";}'
categories:
    - Programming
    - Technology
tags:
    - asp.net
    - 'best practices'
    - jquery
---

I'm currently in the middle of a project where jQuery is trying to access or manipulate ASP.NET server-side controls. When these controls are nested within, say, a content object, ASP.NET prefixes the ID you give it with the ID of its container. So if you know the id of the container, then you can do this:  <code>$('#mycontent_txtInput').val();</code>. The problem is, when you update your project to the next version of .NET, typically this results in the naming schema changing, e.g. something using dollar signs, etc.

In ASP.NET 4.0, you can change a config setting to go back to the "predictable" method, but my concern about this would be maintaining that configuration setting across servers, or when trying to port code-snippets to other related sites, e.g. an admin site that you create with a similar login scheme to the site it serves.

One common workaround has been to use the ClientID property of the control, e.g.  <code>$('#&lt;%=txtInput.ClientID %&gt;').val();</code>. The problem with this method is that it uses short tags that conjure up memories of classic-ASP "spaghetti code". The other problem is that it prevents you from moving your JavaScript to a .js file.

I found this <a href="http://encosia.com/11-keystrokes-that-made-my-jquery-selector-run-10x-faster/">post on Encosia</a> where they actually did some benchmarking with the older browsers. The older browsers they tested aren't really in use anymore, but by being forced to optimize for them, they have pinched milliseconds off of the method for newer browsers as well. The technique is to use  <code>$('input[id$=txtInput]');</code>. For most browsers, it's even better when you use a class selector as well, which means most of this discussion would be moot—except for 3 points:
<ul>
	<li>In pages with lots and lots of controls, especially those which repeat, it becomes quite difficult to guarantee the uniqueness of your class name when looking for just one item, while you <em>can</em> guarantee uniqueness by ID.</li>
	<li>You don't always have control over which classes are used in all of the multiple CSS files attached to your project. For example, there might be some class used in some jQuery UI plugin and by using that class to try to expose your control to jQuery, you're actually changing its appearance accidentally.</li>
	<li>Finally, accessing by class actually seems to slow down the selector in Chrome. I use Chrome for the most part (even on my phone and tablet), and considering their growing marketshare, it seems like it would be a bad idea to optimize for 1 more millisecond in the other browsers when it slows you down by that many milliseconds in Chrome.</li>
</ul>
In conclusion, write this down somewhere: <code>$('input[id$=txtInput]');</code>

Now, maybe it's time to write a regular expression for my replace algorithm...
---
#layout: post
title: "pip Installation Problem- OSError: [Errno 28] No space left on device on [virtualenv]"
date: 2016-10-26 07:36
author: escrowdis
comments: true
tags: [django, Errno 28, install, lubuntu, no space left on device, OSError, pip, python, Tech issues]
---
I've met this error twice during pip installation in virtualenv

The point is my storage is **NOT full or overflow** what kind....weird

<span style="color: #ff0000;">```OSError: [Errno 28] No space left on device```</span>

![]({{ site.url }}/images/posts/1-1.png)

Use instructions below to resolve:
<p class="lang-py prettyprint prettyprinted">```<span class="pln">sudo umount </span><span class="pun">/</span><span class="pln">tmp sudo echo </span><span class="str">'MINTMPKB=0'</span> <span class="pun">&gt;</span><span class="pln"> sudo </span><span class="pun">/</span><span class="pln">etc</span><span class="pun">/</span><span class="pln">default</span><span class="pun">/</span><span class="pln">mountoverflowtmp </span>```</p>
BUT!!

if umount cannot work, try ```sudo umount -l /tmp```

It might **take a while** to get through this

![]({{ site.url }}/images/posts/virtualenv-installed.png)

[ref](http://stackoverflow.com/questions/28590344/ioerror-no-space-left-on-device-which-device)

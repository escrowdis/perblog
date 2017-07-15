---
#layout: post
title: "[CubieTruck] NAND Space Re-Partition 空間重新配置"
date: 2016-10-26 04:50
author: escrowdis
comments: true
tags: [A20, cb3, CT, cubieboard 3, CubieTruck, Embedded, NAND space, NAND space re-partition, nand-part, re-partition]
---
I got this CT from a friend <a href="https://github.com/tonyhccdev" target="_blank">tonyhccdev</a>. And I found that this CT has 16GB NAND space (default is 8 GB, <a href="http://docs.cubieboard.org/products/start" target="_blank">ref.</a>). But the default root partition is 8GB, so expand space is needed.

I googled some references(p.s. 1) did the same thing so I followed and get is work.
<ol>
 	<li>use <strong><code>sudo nand-part -h</code></strong> you can know how to use it.</li>
 	<li><strong><code>sudo nand-part -f a20 /dev/nand</code></strong> (My CT is A20). You can see there're 3 parts
<ol>
 	<li>bootloader. start from 32768, size 131072</li>
 	<li>rootfs. start from 163840, size 14680064</li>
 	<li>UDISK (unused part). start from 14843904, size 16089088</li>
 	<li>So if you want to add UDISK to rootf, know the sum space is 14680064 + 16089088 = 30769152</li>

![]({{ site.url }}/images/posts/CT_un-rearranged.png)

```sudo nand-part -f a20 /dev/nand 32768 'boot 131072' 'rootfs 30769152'```<br>
reboot ``shutdown -r now``

![]({{ site.url }}/images/posts/CT_rearranged.png)

check partition space. ```df -h```<br>
Resize rootfs partition. ```sudo resize2fs /dev/nandb```<br>
check. ```df -h```

[ref1](http://blog.ilc.edu.tw/blog/index.php?op=printView&amp;articleId=522693&amp;blogId=25793)<br>
[ref2](http://blog.csdn.net/mokeding/article/details/18886041)

---
#layout: post
title: "[CubieTruck] NAND Space Re-Partition 空間重新配置"
date: 2016-10-26 04:50
author: escrowdis
comments: true
tags: [A20, cb3, CT, cubieboard 3, CubieTruck, Embedded, NAND space, NAND space re-partition, nand-part, re-partition]
---
I got this CT from a [friend](https://github.com/tonyhccdev) and I found that this CT has 16GB NAND space (default is 8 GB, see [ref.](http://docs.cubieboard.org/products/start)). But the default root partition is 8GB, so expand space is needed.

I googled some references(p.s. 1) did the same thing so I followed and get is work.
1. use `sudo nand-part -h` you can know how to use it.

2.
`sudo nand-part -f a20 /dev/nand` (My CT is A20). You can see there're 3 parts
  - bootloader. start from 32768, size 131072
  - rootfs. start from 163840, size 14680064
  - UDISK (unused part). start from 14843904, size 16089088

3. So if you want to add UDISK to rootf, know the sum space is 14680064 + 16089088 = 30769152

![]({{ site.url }}/images/posts/CT_un-rearranged.png)

```bash
sudo nand-part -f a20 /dev/nand 32768 'boot 131072' 'rootfs 30769152'
reboot ``shutdown -r now
```

![]({{ site.url }}/images/posts/CT_rearranged.png)

check partition space. ```df -h```<br>
Resize rootfs partition. ```sudo resize2fs /dev/nandb```<br>
check. ```df -h```

[ref1](http://blog.ilc.edu.tw/blog/index.php?op=printView&amp;articleId=522693&amp;blogId=25793)<br>
[ref2](http://blog.csdn.net/mokeding/article/details/18886041)

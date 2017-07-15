---
#layout: post
title: "[CubieTruck a.k.a. CubieBoard 3] lubuntu NAND Installation"
date: 2016-10-25 08:53
author: escrowdis
comments: true
tags: [cb3, cubieboard 3, cubietruck. ct, Embedded, FEL, FEL mode, lubuntu, nand install]
---

Heard there's an OS called <strong><a href="http://cubian.org/" target="_blank">Cubian </a></strong>for CubieBoard series.

There's <a href="https://github.com/cubieplayer/cubian/wiki/Install-Cubian" target="_blank">installation guide</a>

But met a problem on <strong><a href="https://github.com/cubieplayer/cubian/wiki/Install-Cubian#install-to-nand" target="_blank">Install to NAND </a></strong>section that there's no folder '<code>~/nandinstall'</code>

Because Linaro 13.09 was installed inside(long time ago) and this <a href="http://cubian.org/2014/06/30/troubleshooting-nandinstall-on-a20/" target="_blank">troubleshooting</a> said we need to install ubuntu system first.

I followed <a href="http://docs.cubieboard.org/tutorials/ct1/installation/cb3_lubuntu-12.10-desktop_nand_installation_v1.00" target="_blank">this site</a> to install <strong>lubuntu</strong>

<strong>Preparation</strong>:
<ul>
 	<li><strong>PhoenixSuit</strong>. I tried to use <a href="http://linux-sunxi.org/LiveSuit" target="_blank">LiveSuit</a>. But it occurred 2 problem:
<ul>
 	<li>1) can't find driver of A20, PhoenixSuit had the driver packed inside, though.</li>
 	<li>2) don't get this from another website, you may get some problem like 'add device fail'</li>
</ul>
</li>
 	<li><strong>NAND image</strong> (sources of OS in <a href="http://dl.cubieboard.org/software/a20-cubietruck/" target="_blank">http://dl.cubieboard.org/software/a20-cubietruck/</a>, used: ct-lubuntu-server-nand-v2.0.img)</li>
 	<li><strong>MobaXterm</strong> (whatever ssh software you liked)</li>
</ul>

And entering  <strong>FEL mode</strong> (how to:<a href="http://linux-sunxi.org/FEL#Entering_FEL_mode" target="_blank">http://linux-sunxi.org/FEL#Entering_FEL_mode</a>), but I can't run into it.....because no driver for CT could be detected in Windows (not like OS X)....I first installed <span style="text-decoration: underline;">LiveSuitPack</span> from <a href="http://linux-sunxi.org/LiveSuit#Download" target="_blank">Download section</a>, however the driver was not found....QQ I just installed a bunch garbage drivers like: <del>UniversalAdbDriverSetup</del>, <del>adbdriver</del>, <del>samsung_android_usb_driverEmbedde</del>

Finally, I found the driver is <span style="text-decoration: underline;">PhoenixSuit_V1.10</span> and the driver need to be installed manually.

![]({{ site.url }}/images/posts/update-driver.png)

![]({{ site.url }}/images/posts/driver-location.png)

![]({{ site.url }}/images/posts/Phoenix_choose_img.png)

After installed, <strong>find the IPv4-address</strong> (should be like 192.168.XXX.XXX).

Then<strong> ssh</strong> into it. Default account is linaro:linaro, and port: 22

Hello! Linaro

![]({{ site.url }}/images/posts/ct-first-view.png)

set root's password first and then update it!

```
sudopasswd
sudo apt-get update && time sudo apt-get dist-upgrade
```

DONE!

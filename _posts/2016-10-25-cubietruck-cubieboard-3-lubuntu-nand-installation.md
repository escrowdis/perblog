---
#layout: post
title: "[CubieTruck a.k.a. CubieBoard 3] lubuntu NAND Installation"
date: 2016-10-25 08:53
author: escrowdis
comments: true
tags: [cb3, cubieboard 3, cubietruck. ct, Embedded, FEL, FEL mode, lubuntu, nand install]
---

Heard there's an OS called [Cubian](http://cubian.org/) for CubieBoard series.

There's [installation guide](https://github.com/cubieplayer/cubian/wiki/Install-Cubian)

But met a problem on [Install to NAND section](https://github.com/cubieplayer/cubian/wiki/Install-Cubian#install-to-nand) that there's no folder ```~/nandinstall```

Because Linaro 13.09 was installed inside(long time ago) and this [troubleshooting](http://cubian.org/2014/06/30/troubleshooting-nandinstall-on-a20/) said we need to install ubuntu system first.

I followed [this site](http://docs.cubieboard.org/tutorials/ct1/installation/cb3_lubuntu-12.10-desktop_nand_installation_v1.00) to install **lubuntu**

**Preparation**:

- **PhoenixSuit** I tried to use LiveSuit. But it occurred 2 problem:
  - can't find driver of A20, PhoenixSuit had the driver packed inside, though.
  - don't get this from another website, you may get some problem like 'add device fail'
- **NAND image** (sources of OS in http://dl.cubieboard.org/software/a20-cubietruck/, used: ct-lubuntu-server-nand-v2.0.img)
- **MobaXterm** (whatever ssh software you liked)

And entering FEL mode (see [how to](http://linux-sunxi.org/FEL#Entering_FEL_mode)),
but I can't run into it.....because no driver for CT could be detected in Windows (not like OS X)....
I first installed **LiveSuitPack** from [Download section](http://linux-sunxi.org/LiveSuit#Download),
however the driver was not found....QQ I just installed a bunch garbage drivers like: ~~UniversalAdbDriverSetup, adbdriver, samsung_android_usb_driverEmbedde~~

Finally, I found the driver is _PhoenixSuit V1.10_ and the driver need to be installed manually.

![]({{ site.url }}/images/posts/update-driver.png)

![]({{ site.url }}/images/posts/driver-location.png)

![]({{ site.url }}/images/posts/Phoenix_choose_img.png)

After installed, **find the IPv4-address** (should be like 192.168.XXX.XXX).

Then** ssh** into it. Default account is linaro:linaro, and port: 22

Hello! Linaro

![]({{ site.url }}/images/posts/ct-first-view.png)

set root's password first and then update it!

```bash
sudopasswd
sudo apt-get update && time sudo apt-get dist-upgrade
```

DONE!

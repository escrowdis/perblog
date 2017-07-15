---
#layout: post
title: "Can't Find Ubuntu/Grub with Win10 in Single Disk - Dual-Boot"
description: "Find grub boot menu with dual-boot, win10 & ubuntu 16.04"
date: 2017-06-20 23:09
author: escrowdis
comments: true
tags: [grub, ubuntu, windows10, dual-boot]
---
I've tried lots of times to re-install ubuntu and fedora recently, and failed to boot into them. It's frustrated QwQ\n
Finally! I found that it might be the Windows boot manager can't find grub, so here's the solution.


### Step1
- Win+x and choose **Power Options**
- Click **Change settings that are currently unavailable**
- Turn off **Fast startup**

### Step 2
- Reboot the computer and enter the BIOS (press F2 for my laptop)
- Turn off **secure boot**

### Step 3
- Install OS
- reboot and enter Windows
- Press 'Win' and search by 'cmd', right-click to **Run as administrator**
- Key `bcdedit /set {bootmgr} path \EFI\ubuntu\grubx64.efi` into the cmd and enter

### Step 4
- Final step, reboot and you'll see the grub boot menu!

[ref for power option](https://read01.com/jND7m.html)
[ref for grub](https://itsfoss.com/no-grub-windows-linux/)

---
#layout: post
title: "First Things after Linux Installed"
date: 2016-12-18 14:35
author: escrowdis
comments: true
tags: [kb, keyboard, linux, ssh, time-zone, tz]
---
<strong>update and upgrade first</strong>
`sudo apt-get update && time sudo apt-get dist-upgrade`

<strong>set root password</strong>
`sudopasswd`

<strong>timezone</strong>
`sudo dpkg-reconfigure tzdata`

<strong>keyboard type</strong>
`sudo dpkg-reconfigure keyboard-configuration`

<strong>ssh</strong>
`sudo iptables -A INPUT  -p tcp --dport [port-want-open] -j ACCEPT`

but iptables won't remember after reboot, so save iptables to some where like: **etc/iptables.conf**
`sudo iptables-save > etc/iptables.conf`
and if you want this rule processed each boot, create a file
`sudo vim /etc/network/if-pre-up.d/firewall`
and paste the code below:
```
#!/bin/sh
/sbin/iptables-restore < /etc/iptables.conf
```

Check CPU details if you want to overclock
`cpufrequtils`

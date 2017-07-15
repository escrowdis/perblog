---
#layout: post
title: "First Things after Linux Installed"
date: 2016-12-18 14:35
author: escrowdis
comments: true
tags: [kb, keyboard, linux, ssh, time-zone, tz]
---
## update and upgrade first
`sudo apt-get update && time sudo apt-get dist-upgrade`

## set root password
`sudopasswd`

## timezone
`sudo dpkg-reconfigure tzdata`

## keyboard type
`sudo dpkg-reconfigure keyboard-configuration`

## ssh
### Open port
`sudo iptables -A INPUT  -p tcp --dport <port-want-open> -j ACCEPT`

And save this iptables to some where like: **etc/iptables.conf**,
because  iptables won't remember after reboot

`sudo iptables-save > etc/iptables.conf`

and if you want this rule processed each boot, create a file

`sudo vim /etc/network/if-pre-up.d/firewall`

and paste the code below:

```bash
#!/bin/sh
/sbin/iptables-restore < /etc/iptables.conf
```

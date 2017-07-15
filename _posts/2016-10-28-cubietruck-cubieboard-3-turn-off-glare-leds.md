---
#layout: post
title: "[CubieTruck] Turn off glare LEDs 關掉擾人LED"
date: 2016-10-28 07:33
author: escrowdis
comments: true
tags: [bash, bash file, cb3, CT, cubieboard 3, CubieTruck, Embedded, led, startup, turn off led]
---
Create a bash to turn of  LEDs and it should have root's permission =D
<h1>Step 1</h1>

```bash
sudo su -
vi led-off
```

and paste these in the file

```bash
cd /sys/class/leds/
echo 0 &gt; blue\:ph21\:led1/brightness
echo 0 &gt; green\:ph07\:led4/brightness
echo 0 &gt; orange\:ph20\:led2/brightness
echo 0 &gt; white\:ph11\:led3/brightness
```

And make it executable

```bash
chmod +x led-off
```

Then you can run in root by

```bash
./led-off
```

BUT you have to do it after reboot again and again

So try to add the bash script into **startup step**
<h1>Step 2</h1>
```bash
cd /etc/init.d/
```

```bash
vi led-off
```

Add these codes into it

```bash
cd /sys/class/leds/
echo 0 &gt; blue\:ph21\:led1/brightness
echo 0 &gt; green\:ph07\:led4/brightness
echo 0 &gt; orange\:ph20\:led2/brightness
echo 0 &gt; white\:ph11\:led3/brightness
```

Then run

```bash
sudo update-rc.d led-off defaults
```

![]({{ site.url }}/images/posts/led-off.png)

[Ref. 1](http://cychiang719.blogspot.tw/2009/02/ubuntuupdate-rcd.html)
[Ref. 2](http://askubuntu.com/questions/228304/how-do-i-run-a-script-at-start-up)

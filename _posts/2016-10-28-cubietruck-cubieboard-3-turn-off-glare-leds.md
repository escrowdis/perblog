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
<strong><code>sudo su -</code></strong>

<code>vi led-off</code>

and paste these in the file

<strong><code>cd /sys/class/leds/
echo 0 &gt; blue\:ph21\:led1/brightness
echo 0 &gt; green\:ph07\:led4/brightness
echo 0 &gt; orange\:ph20\:led2/brightness
echo 0 &gt; white\:ph11\:led3/brightness</code></strong>

And make it executable

<strong><code>chmod +x led-off</code></strong>

Then you can run in root by

<code>./led-off</code>

BUT you have to do it after reboot again and again

So try to add the bash script into <strong>startup step</strong>
<h1>Step 2</h1>
<code>cd /etc/init.d/</code>

<code>vi led-off</code>

Add these codes into it

<code>cd /sys/class/leds/
echo 0 &gt; blue\:ph21\:led1/brightness
echo 0 &gt; green\:ph07\:led4/brightness
echo 0 &gt; orange\:ph20\:led2/brightness
echo 0 &gt; white\:ph11\:led3/brightness</code>

Then run

<code>sudo update-rc.d led-off defaults</code>


![]({{ site.url }}/images/posts/led-off.png)


Ref. about <a href="http://cychiang719.blogspot.tw/2009/02/ubuntuupdate-rcd.html" target="_blank">update-rc.d</a> and <a href="http://askubuntu.com/questions/228304/how-do-i-run-a-script-at-start-up" target="_blank">add script to startup</a>

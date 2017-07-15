---
#layout: post
title: "Install [Eclipse] for Android App on Windows (Android NDK)"
date: 2013-07-15 11:06
author: escrowdis
comments: true
tags: [Android, Eclipse, Programming, Win, Windows]
---
Before installing NDK,
you may have installed Android SDK and eclipse.

If your ndk is under "ndk r8x...",
you may take a look of [this](https://word.office.live.com/wv/WordView.aspx?FBsrc=https%3A%2F%2Fwww.facebook.com%2Fdownload%2Ffile_preview.php%3Fid%3D129239817285435%26time%3D1373881729%26metadata&amp;access_token=1247935184%3AAVIRl_MikmAwlV-YhjoxU0vONpVnWFRIWNK0x-yqivgUUg&amp;title=Windows+ver+Java+to+C+via+Eclipse.docx).

Here's my device:<br>
Windows 64 bit
<br>
[Eclipse IDE for Java](http://www.eclipse.org/downloads/">Eclipse IDE for Java)
<br>
[Android SDK](http://developer.android.com/sdk/index.html">Android SDK)
<br>
[Android NDK r8e](http://www.oracle.com/technetwork/java/javase/downloads/index.html)

(And all of them under **folder C**, better)

Due to the new version, we **DO NOT** need to download __cygwin__.

Open your project in eclipse, and open **"Project=>Properties"** and **"Builders=>New"**

In **"Main"**,<br>
Location: [path-of-ndk-builder.cmd]<br>
Working Directory: [your-project-path] ("Browse Workspace => (Your project)")

In **"Refresh"**,<br>
Click buttons shown below image and choose lib folder of your project (Specify Resources).

In **"Build Options"**,<br>
Click buttons shown below image and choose jni folder of your project (Specify Resources).

Congrats!!<br>
You can use it!

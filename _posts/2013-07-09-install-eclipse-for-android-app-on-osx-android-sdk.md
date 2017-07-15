---
#layout: post
title: "[Eclipse] Install Eclipse for Android App on OS X (Android SDK)"
date: 2013-07-09 05:27
author: escrowdis
comments: true
tags: [Android, android sdk, Eclipse, OS X, Programming]
---
STEPS
===
#### 1. Download "Eclipse IDE for Java" and decompress to open it
[Download link](http://www.eclipse.org/downloads/)
![]({{ site.url }}/images/posts/eclipse-ide-for-java.png)

#### 2. Download "Android SDK"
if you only need the android SDK or ADT bundle,
you can choose the button below "DOWNLOAD FOR OTHER PLATFORMS"

[Link](http://developer.android.com/sdk/index.html)
![]({{ site.url }}/images/posts/get-android-sdk.png)

#### 3. click "Help->Check for Updates"
#### 4. click "Help->Install New Software" and then "Add"
type<br>
Name: (as you want)<br>
Location: https://dl-ssl.google.com/android/eclipse/

![]({{ site.url }}/images/posts/install.png)
And get all the things into your PC

#### 5. Set the SDK location
Click **"Eclipse->Preferences->Android"** and
**"SDK Location"** folder is [android-sdks] folder.

![]({{ site.url }}/images/posts/preference.png)

and click **"Apply"**<br>
if you didn't find the target to apply, you may click
**"Window->Android SDK and AVD Manager"**<br>
change to the **"Available Packages"** to install Targets files
(recommend to install all)

![]({{ site.url }}/images/posts/1-1.png)

![]({{ site.url }}/images/posts/2-1.png)

And install the packages and Android API that you want to use. <br>
Remember to **restart** your computer,
or you may **UNABLE** to choose the CPU of your AVD. <br>
Then you can use it and Android virtual Device (AVD) as you want.

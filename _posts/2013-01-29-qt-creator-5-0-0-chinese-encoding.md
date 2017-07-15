---
#layout: post
title: "[Qt creator] 5.0.0 中文 編碼 解決 Chinese  Encoding Problem"
date: 2013-01-29 18:00
author: escrowdis
comments: true
tags: [5, Chinese, creator, Encoding, Programming, Qt, Qt creator, Qt Creator 5.0.0]
---

前言 Preface
====
今天打開程式原本想繼續努力<br>
但卻發現程式拉阿拉 key阿key都沒辦法做改變<br>
最後發現是<span style="color: red;">中文編碼器有問題！</span>

![error_encoder]({{ site.url }}/images/posts/error_encoder.jpg)

 它上面有顯示一行<br>
**錯誤： </b>無法用 ""UTF-8"-編碼來解碼 "mainwindow.cpp"。無法編輯。**
上網找阿找發現了一個以後可以避免再次發生這種問題的方法！
SOLUTIONS
====
Solution A:
----
在main.cpp內加入規定編碼器的code，如下圖<br>

 ![error_encoder_solution]({{ site.url }}/images/posts//error_encoder_solution-1-1024x214.jpg)

``
QTextCodec *codec = QTextCodec::codecForName("utf8");
QTextCodec::setCodecForCStrings(codec);
QTextCodec::setCodecForLocale(codec);
QTextCodec::setCodecForTr(codec);
``

但是無法解決我現在這個project的問題！()內部已經含有中文注釋)
因為我已經按下"選擇編碼"，中文已經被編成另外一種亂碼了XDDD
所以只好使用下下策

Solution B:
----
工具(T) → 外部(E) → Text → 使用記事本編輯<br>
將Code重新複製貼上  （因為記事本裡面中文字是好的@_@）

TIPS:
----
如果要看自己現在文字編碼器是什麼 請到<br>
工具(T) → 選項(O) → 文字編輯器(Text Editor) → 行為<br>
裡面右邊有 **檔案編碼** 就可以知道目前是用哪一種囉～

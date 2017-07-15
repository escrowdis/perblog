---
#layout: post
title: "[WordPress] 500 Internal Server Error on WordPress"
date: 2016-09-29 16:44
author: escrowdis
comments: true
tags: [500, 500 interval error, Tech issues, WordPress]
---
最近使用WordPress架個人網站，一開始總會想把所有好用的plug-in都裝進來，
但沒想到有一天網頁突然出現

**"Internal Server Error

The server encountered an interval error or misconfiguration...."**

了解後發現可能是
- phph memory limit問題
- .htaccess損毀
- plug-in或theme出現衝突

我先從最簡單的第2點下手:
#### 更名
用ftp登入網站資料端，應該一開始就可以看到".htaccess"檔案，把它**更名**讓系統找不到它(ex: .htaccess -> .htaccess.old)，重新連入WordPress後可以進入Admin area(一般看到的後台)，接下來就可以重設.htaccess [referece](https://www.elegantthemes.com/blog/tips-tricks/how-to-fix-the-500-internal-server-error-on-your-wordpress-website)

#### plug-in衝突
但我發現我的不行，我在猜想有可能是我裝過多的plug-in，所以我接著試第3點，其實[WordPress Troubleshooting](https://codex.wordpress.org/FAQ_Troubleshooting#How_to_deactivate_all_plugins_when_not_able_to_access_the_administrative_menus.3F)有教你如何排除

我採用ftp連入網站資料端，進去 "./wp-contents" 把裡面的"pligins"資料夾更名 (ex: plugins -> plugins.old)，再試著連入你網站的plugin網頁 (ex: www.wordpress.com/wp-admin/plugins.php)，就會發現所有plug-in都deactivated！接著把plugins.old改回plugins就可以回admin area重新個別啟動plug-in，就可以查出是哪些plug-in衝突囉！

---
#layout: post
title: "EOL - LF and CR/LF"
date: 2017-07-30 23:16
author: escrowdis
comments: true
tags: [CR, LF, Carriage Return, Line Feed, Teletype]
---

# Preface
I found that there's an additional symbol `^M`
when I tried to add a **commit.template** file to my repo on Windows.
**quick fix**: go to the dir of repo (where .git is) and type the command below to let git auto change CR/LF <-> LF.

`git config --global core.autocrlf true`

- - -

# History of EOL
## Teletype
I googled it and found that there are different definitions about **EOL (End Of Line)** which has lots of stories to tell...

Before terminal was invented,
there was a machine **Teletype Model 33** which can type 10 symbols in a second (see [how it works](https://www.youtube.com/watch?v=ObgXrIYKQjc)).

And it takes every 0.2 second while returning a carriage (like cursor) to the head of new line.
If you do NOT add other symbols during this time, maybe the teletype would keep typing the symbol in the wrong place.
So while waiting the carriage returning to the head of the line, people had decided to add 2 symbols during this **~0.2 second**:
- **CR (Carriage Return)**: `\r` ASCII: 0x0D
- **LF (Line Feed)**: `\n` ASCII: 0x0A

But in teletype, the **EOL = CR + LF + 2~3 NUL** to prevent unpredicted actions.  

## Terminal
After that, this idea was inherited into the terminal. But they soon had different voices on this issue due to the price of a storage was very high that time. If you use 2 symbols EOL in one million lines source code, it will have redundant waste of 1 million symbols, especially in kernel project.

So EOL became 2 parts now:
- Windows: `\r\n`
- UNIX: `\n`

This is why it has an additional symbol `^M` at the end of line when you opened a file edited on Windows. Otherwise, it becomes one line if you opened the file edited on UNIX/Mac.
P.S.: Do **NOT** be worried about this if you use high level language to develop program.

# More Reading
- [ASCII](https://zh.wikipedia.org/wiki/ASCII)
- [Encoding](http://www.ruanyifeng.com/blog/2007/10/ascii_unicode_and_utf-8.html)

- - -

Ref.:
- [知无涯之回车换行的故事](https://m.aliyun.com/yunqi/articles/27529)
- [關於linux和windows的CR, LF, CR/LF 回車 換行問題](http://fanli7.net/a/caozuoxitong/Windows/20110524/86455.html)

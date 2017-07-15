---
#layout: post
title: "Linux Useful Tools and commands 好用工具"
description:  "virtualenvwrapper, tmux, reptyr, screen, external ip, ldd"
date: 2016-10-28 08:23
author: escrowdis
comments: true
tags: [git, cmd, external ip, linux, reptyr, screen, Tech issues, tmux, virtualenv, virtualenvwrapper]
---
# Useful commands

## git
### Add things to **not last** commit
```git
git add <files-want-to-update>
git commit --fixup=<old-commit>
# if you have uncommited changes, do stash to store them up
git stash save tmp
git rebase --interactive --autosquash <old-commit>
# if you stashed something up
git stash pop tmp
```
### Edit **not last** commit message
`git rebase --interactive <old-commit>^`

### Add things to last commit
`git commit --amend`

## grep
### Find specific word/pattern in files
`grep -rnw 'dir/want/to/search' -e 'pattern'`

## sed
### !!! BE CAREFUL OF THIS COMMAND !!!
You should use `sed` to check the assumed result, and use `sed -i` later or
if you are sure what is going on
### Replace word/pattern with new pattern in file
`sed -i 's/<pattern>/<new-pattern>/g' <file-path>`<br>
ex: `sed -i 'i/hello/world/g' ./posts`<br>
If you have `/` inside pattern, use `\/` (just like `\n`)

### Add line in file
`sed -i '<line>i <line-want-to-add>' <file-path>`

### Delete line in file
`sed -i '/<pattern>/d' <file-path>`

##ldd
### Check what dynamic linking library
`ldd <binary exec file>`

##Else
### Get external IP
`wget http://ipinfo.io/ip -qO -`
(-q: quiet mode; -O: output file)

### kill unterminated process
`ps aux |  grep <program-name> | awk '{print $2}' | xargs kill -9`
(print $2 will print the PID)

## Check CPU details if you want to overclock
`cpufrequtils`

- - -

# 虛擬環境 Virtual environment
## virtualenvwrapper
### INSTALL
`pip install virtualenvwrapper`
### Add lines below into *~/.bashrc*
``` bash
# virtualenv-wrappper path
export WORKON_HOME=$HOME/.virtualenvs
export VIRTUALENVWRAPPER_PYTHON=/usr/bin/python3.5
export VIRTUALENVWRAPPER_VIRTUALENV=/usr/local/bin/virtualenv
source /usr/local/bin/virtualenvwrapper.sh
```

It's DONE! Now you can do as following,
### Create virtualenv
`mkvirtualenv <virtualenv-name>`
### Remove virtualenv
`rmvirtualenv <virtualenv-name>`
### Copy virtualenv
`cpvirtualenv <virtualenv-name>`
### Open the env
`workon <virtualenv-name>`
### Exit current env
`deactivate`
### List all environments
`lsvirtualenv`
### Show details of environment
`showvirtualenv <virtualenv-name>`
### For more information, please check the references.: [virtualwrapper](http://virtualenvwrapper.readthedocs.io/en/latest/command_ref.html)
, [virtualenvs](http://docs.python-guide.org/en/latest/dev/virtualenvs/)

- - -     

# 再也不用害怕事情做到一半ssh斷線要重來 <br>Don't Be Afraid of Get Disconnected During SSH
## tmux
- **C-b** means typing Ctrl+b together
- Type `tmux` or `tmux new -s <session-name>` to create session
- Create new pane on right side `C-b %`; create new pane bottom `C-b "`
- Switch pane `C-b <arrow-key>`
- Close pane `Ctrl-d` or `exit`
- Detach current session `C-b d`, deteach specific session `C-b D`
- List running session `tmux ls`
- Change session name `tmux rename-session -t <old> <new>`
- Attach session `tmux attach -t <session-name>`
- Ref.: 
    - [easy to use tmux](http://www.hamvocke.com/blog/a-quick-and-easy-guide-to-tmux/)
    - [tmux](http://man.openbsd.org/OpenBSD-current/man1/tmux.1)
    - [ref](http://hyperpolyglot.org/multiplexers)

## screen: 事情沒用完卻有事必須要斷開ssh連線？
- create session `screen -S <your_session>`
- reattach the session `screen -r <session_want_reattach>`
- list all sessions `screen -ls`
- detach and logout remote `screen -D <your_session>`
- scroll up 'n' down `C-a [ [Pg Up]/[Pg Dn]/[Arrow_key]`
- detach session `C-a D`
- Reboot will flush all the session =)
- ref.: [ref1](https://writesnow.net/2014/09/linux-screen%E6%8C%87%E4%BB%A4-%E7%99%BB%E5%87%BA%E8%80%8C%E4%B8%8D%E4%B8%AD%E6%96%B7%E4%BD%9C%E6%A5%AD%EF%BC%81/), [ref2](http://hyperpolyglot.org/multiplexers)

- - -

# UNDONE

## reptyr
- 了解中，能把現有的session抓過來 搭配screen用應該很棒
- http://serverfault.com/questions/55880/moving-an-already-running-process-to-screen
- https://www.cyberciti.biz/faq/show-all-running-processes-in-linux/

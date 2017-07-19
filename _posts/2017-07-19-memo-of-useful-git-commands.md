---
#layout: post
title: "Memo of Useful Git Commands"
date: 2017-07-19 23:30
author: escrowdis
comments: true
tags: [git]
---
# Git Useful commands
## Add things to **not last** commit
```git
git add <files-want-to-update>
git commit --fixup=<old-commit>
# if you have uncommited changes, do stash to store them up
git stash save tmp
git rebase --interactive --autosquash <old-commit>
# if you stashed something up
git stash pop tmp
```

## Edit **not last** commit message
```git
git rebase --interactive <old-commit>^
```

## Add things to last commit
```git
git commit --amend
```

TBD.

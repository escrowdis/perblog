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
```
git add <files-want-to-update>
git commit --fixup=<old-commit>
# if you have uncommited changes, do stash to store them up
git stash save tmp
git rebase --interactive --autosquash <old-commit>
# if you stashed something up
git stash pop tmp
```

## Edit **not last** commit message
```
git rebase --interactive <old-commit>^
```

## Add things to last commit
```
git commit --amend
```

## File name with and without capital
go to '.git/config', and set `ignorecase = false` to prevent there's always unstage changes. 

## Amend user and email after commit
`git commit --amend --author="[FName LName] <[email]>"`

## Extract commits' patches after specific commit (not inclusive, usually want to pack something to others)
`git format-patch [commit-hash]`

## Apply patch
`git am xxxx-<commit-title>.patch`

TBD.

---
layout: base
title: Git cheatsheet
---


## Autosquashing

IMPORTANT: Commit MESSAGE should be exactly the same as a previous commit message!

$ git commit -m "fixup! MESSAGE"
$ git rebase -i --autosquash HEAD^^


## Working with remotes

# Update the list of remote branches:
$ git remote update origin --prune

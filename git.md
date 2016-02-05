---
layout: base
title: Git cheatsheet
---


## Autosquashing

**IMPORTANT:** Commit message should be exactly the same as a previous commit message!
```sh
git commit -m "fixup! Commit message"
git rebase -i --autosquash HEAD^^
```

## Working with remotes
```sh
# Update the list of remote branches:
git remote update origin --prune
```

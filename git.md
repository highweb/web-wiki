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

## Submodules
```sh
# Sync .gitmodules data to .git/config:
git submodule sync --recursive

# Delete submodule:
git rm SUBMODULE
```

## Clear working directory
```sh
git reset --hard
git clean -d -x -f
```

## Stash including untracked files
```sh
$ git stash -u
```

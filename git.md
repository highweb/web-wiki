---
layout: base
title: Git cheatsheet
---


## Rebasing

```sh
git rebase -i --preserve-merges # -p
git pull --rebase -p <REPO> <BRANCH>

# Interactive rebase:
git pull --rebase=interactive -p <REPO> <BRANCH>

# Rebase current branch against another one:
git rebase --onto <BRANCH>
```

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
# Add:
$ git submodule add git@mygithost:billboard lib/billboard

# add submodule to track master branch
git submodule add -b master [URL to Git repo];

# update your submodule
git submodule update --remote
git submodule update --init --recursive

# Sync .gitmodules data to .git/config:
git submodule sync --recursive

# Delete submodule:
git submodule deinit <asubmodule>    
git rm <asubmodule>
# Note: asubmodule (no trailing slash)
# or, if you want to leave it in your working tree
git rm --cached <asubmodule>
rm -rf .git/modules/<asubmodule>
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

## Log
```sh
# Release notes style:
$ git log --pretty='• %s'
```

## Patching

```sh
# You can use Git to apply a patch to a project's repository:
git apply -v path/file.patch

# You can also use --index setting to track modified files:
git apply -v --index path/file.patch

# If you are not using git, or if the repo isn't a local checkout of the project you wish to patch:
patch -p1 < path/file.patch
```

https://csswizardry.com/2017/05/little-things-i-like-to-do-with-git/

---
layout: base
title: Unix shell
---

## wget

Download remote file by URL reproducing relative path locally:

wget -xnH URL


## ssh

Copy public key on the remote server:

ssh-copy-id REMOTE_USER@REMOTE_HOST


## git

Change author of last commit:

git commit --amend --author="Author Name <email@address.com>"

Add remote repository:

git remote add REP_NAME REP_URL
Merge two commits into one:

git rebase -i HEAD~N
Then mark as squash the commit to be merged into second one.

Show commit' author and committer:

git cat-file -p HEAD
Rename author and commiter of all commits:

git filter-branch --commit-filter \
'if [ "$GIT_AUTHOR_NAME" = "OLD_NAME" ];\
then \
export GIT_AUTHOR_NAME="NEW_NAME";\
export GIT_AUTHOR_EMAIL=NEW@EMAIL;\
export GIT_COMMITTER_NAME="NEW_NAME";\
export GIT_COMMITTER_EMAIL=NEW@EMAIL;\
fi;\
git commit-tree "$@"'


## find

Find file by name in the current directory:

find . -name 'FILENAME'


## chown

Change ownership of a symlink itself:

chown -h USER:GROUP SYMLINK


## rsync

Copy all contents of a directory to another directory without overwriting:

rsync -a --ignore-existing DIR1 DIR2
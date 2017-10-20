---
layout: base
title: Mac OS
---

```
# Enter in terminal to activate text replacement across all applications:
defaults write -g WebAutomaticTextReplacementEnabled -bool true
```

```
# Install Jekyll:
sudo gem install jekyll
```

```
Add the key in the keychain
# https://apple.stackexchange.com/questions/48502/how-can-i-permanently-add-my-ssh-private-key-to-keychain-so-it-is-automatically
# ssh-add -K ~/.ssh/[your-private-key]
$ ssh-add -K ~/.ssh/id_rsa
```

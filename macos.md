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

## Atom

Activate the command palette (ShiftCmdP on Mac, CtrlShiftP on Windows/Linux) and search for "convert space" or "convert tab". You should find these three commands are available:

Whitespace: Convert Spaces to Tabs
Whitespace: Convert Tabs to Spaces
Whitespace: Convert All Tabs to Spaces

https://stackoverflow.com/questions/41848002/how-to-replace-tabs-with-spaces-in-atom


## Gmail message as PDF

1. Click Show original.
2. Download.
3. Rename .txt > .eml.
4. Open .eml in Mail.
5. Export as PDF.

---
layout: base
title: NPM cheatsheet
---

```sh
# Init package:
npm init

# Non-flattend install:
npm install --legacy-bundling

# Ignore symlinks on Windows:
npm install --no-bin-links

# Reinstalling a package after just deleting the node module works with:
yarn install --check-files

# Install package globally:
yarn global add <PACKAGE>

# Using --peer or -P will install one or more packages in your peerDependencies.
yarn add <package...> [--peer/-P]
```

# Development:
    1. Pick one component to work on.
    2. Clone its repo somewhere locally.
    3. Go to this repo and run `yarn link`.
    4. Go to the project and run `yarn link` again.
    5. Now component repo is linked to the project repo allowing you to make and commit changes in both.

## Scripts

Apply a patch:
```json
"prepare": "git apply -v --directory=node_modules/blueimp-gallery patches/blueimp-gallery+2.32.0.patch && yarn --cwd=node_modules/blueimp-gallery build:jquery || exit 0"
```


npm scripts ignore errors
Simply adding: exit 0 to the end of the command did it!
https://stackoverflow.com/questions/30341113/npm-scripts-ignore-errors

## Utils

* https://github.com/ds300/patch-package

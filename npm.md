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

## Utils

* https://github.com/ds300/patch-package

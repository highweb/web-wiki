---
layout: base
title: Drush cheatsheet
---

## Install
```
# Install Drush globally:
$ composer global require drush/drush:7.x

# Upgrade Drush:
$ composer global require drush/drush:8.x
```

## Updates
```
# Update Drupal core codebase and database:
$ drush up drupal

# Update Drupal core codebase only:
$ drush upc drupal
```

## Backing up and restoring
```
# Restore website from backup (both files and database):
$ drush arr BACKUP.tar.gz --destination=DOCROOT --db-url=mysql://USER:PASSWORD@HOST/DATABASE
```

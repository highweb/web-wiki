# Composer

```sh
# Install w/o checking system modules:
$ composer install --ignore-platform-reqs

# Lock deps:
$ composer update --lock

# Add package with git src:
$ composer require vendor/package:1.x-dev --prefer-source

# Package with custom repo - add to `composer.json`:
"repositories": [
    {
      "type": "vcs",
      "url": "https://github.com/Codeception/YiiBridge",
    },
]
```

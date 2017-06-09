---
layout: base
title: Drupal howtos
---

## Nginx
```sh
# Static files:
try_files $uri $uri/ /index.php?q=$uri&$args;

# Edit /etc/php5/fpm/php.ini:
post_max_size = 8M
upload_max_filesize = 8M
...
$ service php5-fpm reload

# Edit /etc/nginx/<...>.conf:
client_max_body_size 8m;
...
$ service nginx reload

# Redirect a folder:
rewrite ^/images(|/.*)$ https://images.example.com$1 permanent;

# Conditional permanent redirect:
if ($host = 'from.com') {
 rewrite ^/(.*)$ https://to.com/$1 permanent;
}
```

## Views

Display a field in the standalone block on the same node page

View:	
Show: Content

Display: Block

 
Format:	
Format: Unformatted list

Show: Fields

Uncheck all settings

Uncheck all settings

Fields:	YOUR_FIELD	
Multiple field settings: Display all values in the same row

Style settings: Use field template

Filter criteria:	YOUR_FIELD is not empty	 
Contextual filters:	Content: Nid	Provide default value: Content ID from URL
Other:	Query settings	Distinct


## Robots.txt

Prevent robots.txt from overriding during Drupal update:

$ mv robots.txt sites/default/
$ ln -s sites/default/robots.txt
Now you can safely update Drupal, just don't forget to restore symbolic link:

$ rm robots.txt
$ ln -s sites/default/robots.txt


## Updates
```
# Update Drupal core codebase and database:
$ drush up drupal

# Update Drupal core codebase only:
$ drush upc drupal
```

## Exporting data

Install Views data export module.
Create view using this module.
Turn on batch export in the view settings.
Disable SQL rewriting in the view query settings.
Make sure the view does not require arguments (contextual filters).
$ drush views-data-export VIEW_KEY DISPLAY_KEY OUTPUT_FILE


## Rename ECK entity bundle

Manually create new bundle, clone fields and configuration.
Then:
UPDATE `eck_TYPE` SET `type` = 'NEW_BUNDLE' WHERE `type` = 'OLD_BUNDLE';

UPDATE `field_data_FIELD_1` SET `bundle` = 'NEW_BUNDLE' WHERE `bundle` = 'OLD_BUNDLE';
UPDATE `field_revision_FIELD_1` SET `bundle` = 'NEW_BUNDLE' WHERE `bundle` = 'OLD_BUNDLE';
...
UPDATE `field_data_FIELD_N` SET `bundle` = 'NEW_BUNDLE' WHERE `bundle` = 'OLD_BUNDLE';
UPDATE `field_revision_FIELD_N` SET `bundle` = 'NEW_BUNDLE' WHERE `bundle` = 'OLD_BUNDLE';


## Layout API (D8)

https://www.drupal.org/docs/8/api/layout-api/how-to-render-layouts
https://www.drupal.org/node/2578731


## Configuring HTTPS

In this example we run Drupal over HTTP and use CloudFlare as a proxy server under HTTPS.

In this case all you need is to edit settings.php:

// Use a proper protocol:
if (isset($_SERVER['HTTP_X_FORWARDED_PROTO']) && isset($_SERVER['HTTP_HOST'])) {
  $base_url = $_SERVER['HTTP_X_FORWARDED_PROTO'] . '://' . $_SERVER['HTTP_HOST'];
}

...

// Pass the real user IP:
if (isset($_SERVER['HTTP_X_FORWARDED_FOR'])) {
  $_SERVER['REMOTE_ADDR'] = $_SERVER['HTTP_X_FORWARDED_FOR'];
}


## Exportables (D8)

`config/install` - must-have configurations
`config/optional` - optional configurations (i.e. which depends on optional modules)

https://www.drupal.org/node/2453919


## Dev & debug

Using dd($form_state); within the callback function works beautifully.

On linux you can tail -f /tmp/drupal-debug.txt to see the $form_state in real time. (Or whatever the temp directory for your site is set to, often something like sites/yoursite.com/files/tmp.)

Also:
- https://www.drupal.org/project/devel_debug_log

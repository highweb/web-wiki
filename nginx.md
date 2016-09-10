---
layout: base
title: Nginx
---

```sh
# Check Nginx version:
$ nginx -v

# Protect by password:
$ sudo apt-get install apache2-utils
$ sudo htpasswd -c /etc/nginx/.htpasswd USERNAME
...
$ sudo nano /etc/nginx/...conf
...
auth_basic "Restricted";
auth_basic_user_file /etc/nginx/.htpasswd;
...

# Require auth for specific domain:
...
if ($host = 'example.com') {
  return 555;
}

error_page 555 = @auth;

location @auth {
	auth_basic "Restricted";
	auth_basic_user_file /etc/nginx-passwd/.htpasswd;
}
...

# Apply rule for specific domain:
if ($host = 'example.com') {
  ...
}

# Compile from sources:
$ sudo apt-get install build-essential zlib1g-dev libpcre3-dev libssl-dev libxslt1-dev libxml2-dev libgd2-xpm-dev libgeoip-dev libgoogle-perftools-dev libperl-dev
$ wget http://nginx.org/download/nginx-1.4.4.tar.gz
$ tar xvfvz nginx-1.4.4.tar.gz
$ cd nginx-1.4.4
$ ./configure --sbin-path=/usr/sbin/nginx --with-http_image_filter_module
$ make
$ sudo make install
```

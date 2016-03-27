---
layout: base
title: Nginx
---

```sh
# Check Nginx version:
$ nginx -v

# Compile from sources:
$ sudo apt-get install build-essential zlib1g-dev libpcre3-dev libssl-dev libxslt1-dev libxml2-dev libgd2-xpm-dev libgeoip-dev libgoogle-perftools-dev libperl-dev
$ wget http://nginx.org/download/nginx-1.4.4.tar.gz
$ tar xvfvz nginx-1.4.4.tar.gz
$ cd nginx-1.4.4
$ ./configure --sbin-path=/usr/sbin/nginx --with-http_image_filter_module
$ make
$ sudo make install
```

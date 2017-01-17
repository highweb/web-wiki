---
layout: base
title: Debian
---

## Installation

Before installing any software make sure you have up-to-date packages information:

sudo apt-get update


## Working with packages

List all packages installed:

sudo dpkg-query -l
sudo dpkg-query -l 'PACKAGE*'
Show orphaned packages:

sudo apt-get install deborphan
deborphan -a
Find packages to delete:

aptitude search ~iPACKAGE
Legend: i — installed, c — config files exist, p — not installed (uninstalled)

Remove package completely (with config files):

sudo apt-get remove PACKAGE
sudo apt-get purge PACKAGE


## Mail

Here we will configure our server to send mail via external SMTP server (i.e. smtp.yandex.ru).

Install exim4 first:

sudo apt-get install exim4
Then configure it:

sudo dpkg-reconfigure exim4-config

General type of mail configuration: mail sent by smarthost; no local mail
System mail name: HOSTNAME_OR_YOUR_DOMAIN
IP-addresses to listen on for incoming SMTP connections: keep default
Other destinations for which mail is accepted: leave blank
Visible domain name for local users: HOSTNAME_OR_YOUR_DOMAIN
IP address or host name of the outgoing smarthost: smtp.yandex.ru::587
Keep number of DNS-queries minimal (Dial-on-Demand)? No
Split configuration into small files? Yes
Root and postmaster mail recipient: leave blank
Specify your external SMTP credentials in /etc/exim4/passwd.client in the following format:

SMTP_SERVER:SERVER@EMAIL:PASSWORD
Finally configure headers rewriting in /etc/exim4/conf.d/rewrite/00_exim4-config_header (otherwise external SMTP will eventually reject your mail):

begin rewrite
*@* EMAIL@SERVER Ff
Update config, restart and test:

sudo update-exim4.conf
sudo service exim4 restart
echo "Test message" | sudo sendmail -v YOUR@EMAIL


## Users & groups

Change user id:
```
sudo usermod -u ID LOGIN

# Add user to a group (complimentary):
sudo usermod -a -G GROUP USER
```

## File access

Here we will configure remote SFTP access.

Create and configure sftponly group:

sudo addgroup sftponly
sudo nano /etc/ssh/sshd_config
```
Subsystem sftp internal-sftp

...

# This should be at the end of file:
Match group sftponly
    ChrootDirectory %h
    ForceCommand internal-sftp
    AllowTcpForwarding no
```

Create new SSH user without shell access:

sudo adduser <SFTP_LOGIN>
sudo adduser <SFTP_LOGIN> sftponly
sudo chown root:root /home/<SFTP_LOGIN>
sudo usermod -s /bin/false <SFTP_LOGIN>

```sh
# Reload SSH daemon:
service ssh reload
```

## Databases

To allow remote access to your MongoDB server comment this line in the /etc/mongodb.conf:
```
#bind_ip = 127.0.0.1
```
And restart MongoDB:

sudo service mongodb restart
Don't forget to allow 27017 port in the firewall!

MySQL

To allow remote access comment this line in `/etc/mysql/my.cnf`:
```
#bind-address = 127.0.0.1
```
Don't forget to allow 3306 port in the firewall!

Renaming:

SELECT User FROM mysql.user;
RENAME USER 'OLD_NAME'@'HOST' TO 'NEW_NAME'@'HOST';
DROP USER 'NAME'@'HOST'


## Languages

Install module via pip for specific python version:

sudo python3.4.0 -m pip install MODULE


## Web server
```
Basic authorization (Apache):

sudo nano APACHE_CONF_FILE
# Enable .htaccess
AllowOverride AuthConfig
sudo htpasswd -c ~/passwd LOGIN
sudo nano .htaccess
AuthType Basic
AuthName "Restricted Files"
# (Following line optional)
AuthBasicProvider file
AuthUserFile /home/USER/passwd
Require user LOGIN
sudo service apache2 restart
```

## Interesting facts

Word "Debian"

The word "Debian" was formed as a combination of two names — Debian founder name (Ian Murdock) and his then-girlfriend name (Debra Lynn).

Debra + Ian = Debian

Logo story

The origin of the Debian logo is based on a chin!

The first named Debian release was named Buzz, after Toy Story character Buzz Lightyear who had a swirl in his chin!

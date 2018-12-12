# change-localhost-URL
## change the localhost project URL

Today we are trying to change your project URL you can use it when you are working on a localhost
it is too easy and you only need to change two files
1) "host" in "C: \ Windows \ System32 \ drivers \ etc"
2) "httpd-vhost.conf" in "C: \ wamp64 \ bin \ apache \ apache2.4.27 \ conf \ extra" -> maybe you found it in another path but generally it should be there

## 1 _ host

```php
# Copyright (c) 1993-2009 Microsoft Corp.
#
# This is a sample HOSTS file used by Microsoft TCP/IP for Windows.
#
# This file contains the mappings of IP addresses to host names. Each
# entry should be kept on an individual line. The IP address should
# be placed in the first column followed by the corresponding host name.
# The IP address and the host name should be separated by at least one
# space.
#
# Additionally, comments (such as these) may be inserted on individual
# lines or following the machine name denoted by a '#' symbol.
#
# For example:
#
#      102.54.94.97     rhino.acme.com          # source server
#       38.25.63.10     x.acme.com              # x client host

# localhost name resolution is handled within DNS itself.
#	127.0.0.1       localhost
#	::1             localhost

	127.0.0.1       hello.dev
	::1             hello.dev
  
  ```
  
You should copy line 31 and 32 then uncomment it and write your custom URL instead of localhost in this case we use "hello.dev" 
  
## 2 _ httpd-vhost.conf
  
now you can you should change your file like this
  
## before
   
```php

# Virtual Hosts
#
<VirtualHost *:80>
  ServerName localhost
  ServerAlias localhost
  DocumentRoot "${INSTALL_DIR}/www"
  <Directory "${INSTALL_DIR}/www/">
    Options +Indexes +Includes +FollowSymLinks +MultiViews
    AllowOverride All
    Require local
  </Directory>
</VirtualHost>

```

## after
   
```php

# Virtual Hosts
#
<VirtualHost *:80>
  ServerName localhost
  ServerAlias localhost
  DocumentRoot "${INSTALL_DIR}/www"
  <Directory "${INSTALL_DIR}/www/">
    Options +Indexes +Includes +FollowSymLinks +MultiViews
    AllowOverride All
    Require local
  </Directory>
</VirtualHost>


<VirtualHost *:80>
  ServerName hitype.dev
  DocumentRoot "${INSTALL_DIR}/www/hello/public"
  <Directory "${INSTALL_DIR}/www/hello/public/">
    Options +Indexes +Includes +FollowSymLinks +MultiViews
    AllowOverride All
    Require local
  </Directory>
</VirtualHost>

```
in this example, I use a laravel project which name is hello

it is finished 
you should restart your localhost and then use new URL 
have a good time and enjoy form your life




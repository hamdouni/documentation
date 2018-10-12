---
title: Increase wordpress max file upload size
author: Brahim
type: post
date: 2014-12-05T14:42:56+00:00
url: /increase-wordpress-max-file-upload-size/
categories:
  - How to ?
  - Linux
tags:
  - linux
  - php
  - wordpress

---
On Ubuntu/Debian distro, edit the /etc/wordpress/htaccess and add this lines :

<pre>php_value upload_max_filesize 50M
php_value post_max_size 50M
php_value memory_limit 50M
</pre>
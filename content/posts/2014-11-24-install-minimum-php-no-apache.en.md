---
title: Install minimum php (no apache)
author: Brahim
type: post
date: 2014-11-24T13:46:42+00:00
url: /install-minimum-php-no-apache/
fb_author_post_id:
  - 746983758702752
facebook_status_messages:
  - 'a:1:{i:0;a:2:{s:7:"message";s:98:"Posted to <a href="https://www.facebook.com/746983758702752" target="_blank">Facebook Timeline</a>";s:5:"error";b:0;}}'
categories:
  - How to ?
  - Linux

---
To code with php, no need to install apache and other dependencies, especially as php has a builtin web server.

<pre>apt-get install php5-cli</pre>

Then use

<pre>php -S localhost:4444</pre>

and you&#8217;re done.
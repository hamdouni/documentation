---
title: 'mysql client : don’t show columns names and grid'
author: Brahim
type: post
date: 2016-05-30T08:33:23+00:00
url: /mysql-client-dont-show-columns-names-and-grid/
categories:
  - How to ?

---
Default mysql client behaviour is to show column names and grid when returning results  but how to get rid of this decorations ? <!--more-->

<pre>+-------+
| pv_id |
+-------+
|     1 |
|     2 |
|     3 |
+-------+</pre>

To keep only the data results without the decorations, use the -sN option on the mysql client like this :

<pre>mysql -sN ...</pre>

and you&#8217;ll get :

<pre>1
2
3
</pre>

Perfect for playing with the shell !
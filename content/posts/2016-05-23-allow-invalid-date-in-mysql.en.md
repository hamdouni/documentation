---
title: Allow invalid date in MySQL
author: Brahim
type: post
date: 2016-05-23T13:55:55+00:00
url: /allow-invalid-date-in-mysql/
categories:
  - How to ?
tags:
  - dev
  - mysql

---
Just in case you absolutely have to insert a date in MySQL that does&#8217;nt exist, eg 2014-02-30, you can run MySQL server in a special mode that authorizes such dates :

<pre>mysqld --sql-mode="ALLOW_INVALID_DATES"
</pre>

MySQL will only check that the month is in the range from 1 to 12 and the day is in the range from 1 to 31.
  
<a href="http://dev.mysql.com/doc/refman/5.7/en/sql-mode.html#sqlmode_allow_invalid_dates" target="_blank">see Mysql DOC </a>
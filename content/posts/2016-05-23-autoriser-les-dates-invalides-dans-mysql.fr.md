---
title: Autoriser les dates invalides dans MySQL
author: Brahim
type: post
date: 2016-05-23T13:55:55+00:00
url: /autoriser-les-dates-invalides-dans-mysql/
categories:
  - Comment faire ?
tags:
  - dev
  - mysql

---
Dans le cas où vous avez absolument besoin d&#8217;insérer une date dans MySQL, qui n&#8217;est pas valide, par exemple le 30 février 2014, vous pouvez exécuter le server MySQL dans un mode spécial pour autoriser ces dates :<!--more-->

<pre>mysqld --sql-mode="ALLOW_INVALID_DATES"
</pre>

MySQL vérifiera uniquement que le mois est compris entre 1 et 12 et le jour entre 1 et 31.
  
<a href="http://dev.mysql.com/doc/refman/5.7/fr/sql-mode.html#sqlmode_allow_invalid_dates" target="_blank">voir la doc Mysql </a>
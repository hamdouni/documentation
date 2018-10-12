---
title: "Comment réparer WordPress après modification de l'URL ?"
author: Brahim
type: post
date: 2008-01-10T22:23:23+00:00
url: /wordpress-mysql-et-url-cassee/
categories:
  - Comment faire ?
tags:
  - howto

---
Après avoir modifier l&#8217;url dans la page d&#8217;option WordPress, le site n&#8217;était plus accessible&#8230; Cela arrive lorsqu&#8217;on fait la modif avant de mettre en place le .htaccess avec la règle de rewriting, ou alors qu&#8217;on se plante sur l&#8217;url. Pour réparer, sans être obligé d&#8217;installer un phpmyadmin, voici les commandes mysql :

> mysql> show databases;
  
> mysql> use YOURDATABASE;
  
> mysql> update wp\_options set optionvalue=&#8217;http://THEGOODURL&#8217; where option\_name=&#8217;siteurl&#8217;;
---
title: Surveiller mysql pour pas cher
author: Brahim
type: post
date: 2013-12-10T18:02:44+00:00
url: /surveiller-mysql-pour-pas-cher/
post_to_facebook_timeline:
  - 1
categories:
  - Comment faire ?
  - Linux
tags:
  - howto
  - linux
  - ubuntu

---
<img class="aligncenter size-full wp-image-868" alt="processlist-refresh" src="http://brahim.hamdouni.com/wp-uploads/processlist-refresh.png" width="860" height="329" srcset="http://brahim.hamdouni.com/wp-uploads/processlist-refresh.png 860w, http://brahim.hamdouni.com/wp-uploads/processlist-refresh-300x114.png 300w" sizes="(max-width: 706px) 89vw, (max-width: 767px) 82vw, 740px" />

Voici une petite astuce pour surveiller ses serveurs mysql sans déployer d&#8217;outil particulier :

> mysqladmin -u root -p -i 5 processlist

L&#8217;option -i ou &#8211;sleep en version longue permet de spécifier une durée en seconde pour répeter la commande. Très pratique pour du dév en local et prend quasi pas de ressource.

&nbsp;
---
title: "Comment supprimer l'affichage des logs sur la console ?"
author: Brahim
type: post
date: 2005-08-08T08:09:27+00:00
url: /supprimer-laffichage-des-logs-sur-la-console/
categories:
  - Comment faire ?

---
Souvent, après une mise en place d&#8217;iptables, on se retrouve avec les traces sur la console.
  
Voici comment faire pour supprimer cette affichage.<!--more-->

Editer le fichier /etc/init.d/klogd

Mettre la variable KLOGD comme suit :

> KLOGD=&#8221;-c 4&#8243;

puis relancer klogd (sous debian) :

> /etc/init.d/klogd restart
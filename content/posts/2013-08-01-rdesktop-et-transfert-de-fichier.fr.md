---
title: Rdesktop et transfert de fichier
author: Brahim
type: post
date: 2013-08-01T22:44:22+00:00
url: /rdesktop-et-transfert-de-fichier/
fb_author_post_id:
  - 100001734042334_521352191265911
categories:
  - Comment faire ?
tags:
  - howto
  - Java
  - linux

---
> rdesktop -r disk:toto=/home/user/path your.server.com -r sound:local

Un client nous a demandé de migrer son application qui tournait sur une Debian vers une plateforme Windows en VM pour mutualiser ses coûts d&#8217;administration. Pas de grosse difficulté  puisque l&#8217;application avait été faite sous java en 2004 (presque 10 ans, ça nous rajeunit pas).

Bref, avec un linux, le transfert de fichier, c&#8217;est du piece of cake : ssh/sftp et tutti quanti. Mais avec Windows, comment fait-on si on a que du RDP ? Depuis un client Windows, on peut activer un partage de son disque local, mais avec un client Linux ? Et bien, rdesktop le gère très bien avec l&#8217;option -r :

> rdesktop -r disk:toto=/home/user/path your.server.com

Avec &#8220;toto&#8221; pour donner un nom au partage suivi du chemin vers le dossier sur la machine cliente qu&#8217;on veut partager, et bien sûr l&#8217;adresse du serveur distant à la fin. Une fois connecté  en RDP, dans le Windows, on peut aller sur le voisinage réseau et récupérer l&#8217;accès au partage avec l&#8217;adresse : \\tsclient\toto

Et voilà le transfert de fichier par simple copier/coller !

**update** à cause d&#8217;un bug, le partage disk ne fonctionne que si l&#8217;on partage aussi le son !?!? avec -r sound:local
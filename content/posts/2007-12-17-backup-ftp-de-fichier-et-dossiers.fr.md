---
title: Comment backuper une arborescence de fichiers et dossiers par FTP ?
author: Brahim
type: post
date: 2007-12-17T14:27:58+00:00
url: /backup-ftp-de-fichier-et-dossiers/
categories:
  - Comment faire ?
tags:
  - howto

---
Quand on a besoin de faire un backup d&#8217;une arborescence de fichiers et qu&#8217;on a que FTP comme service, il est possible d&#8217;utiliser la commande suivante :

> ncftpput -u USER -p PASSWORD -R SERVER LOCAL REMOTE :

  * USER : l&#8217;identifiant
  * PASSWORD : le mot de passe
  * SERVER : l&#8217;IP ou nom du serveur FTP
  * LOCAL : le dossier source
  * REMOTE : le dossier destinataire

L&#8217;option -R permet de faire le transfert en récursif, c&#8217;est à dire que les dossiers sont automatiquement créés, et c&#8217;est l&#8217;option killer par rapport au client FTP standard.

Et pour la récupération, rien ne vaut un

> wget -r ftp://USER:PASSWORD@SERVER/REMOTE

Je ne sais pas pourquoi mais la récup via ncftp bloque&#8230;
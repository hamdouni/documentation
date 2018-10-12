---
title: Comment réparer une clé usb vfat qui passe en read-only sous Linux ?
author: Brahim
type: post
date: 2007-12-12T11:07:09+00:00
url: /linux-cle-usb-vfat-read-only/
categories:
  - Comment faire ?

---
S&#8217;il n&#8217;est plus possible d&#8217;utiliser une clé usb sous linux avec le système qui bascule en read-only, et qu&#8217;on se retrouve avec ce genre de lignes dans le syslog :

> FAT: Filesystem panic (dev sdb1)
  
> fat\_get\_cluster: invalid cluster chain (i_pos 0)

un petit

> dosfsck -a /dev/sdb1

et ça repart. La commande répare le file system et récupére les fichiers.

&nbsp;

Si en plus, on souhaite formater la clé en lui donnant un label, c&#8217;est simple :

<p style="padding-left: 30px;">
   mkfs.vfat -n &#8216;Votre_label_ici&#8217; -I /dev/sdb1
</p>
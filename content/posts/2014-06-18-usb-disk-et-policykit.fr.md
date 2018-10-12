---
title: usb disk et policykit
author: Brahim
type: post
date: 2014-06-18T21:41:51+00:00
url: /usb-disk-et-policykit-fr/
fb_author_post_id:
  - 670098129724649
post_to_facebook_timeline:
  - 1
categories:
  - Comment faire ?
  - Linux
tags:
  - dbus
  - desktop
  - dwm
  - gnome-settings-daemon
  - linux
  - policykit
  - storage
  - ubuntu
  - usb

---
Lorsqu&#8217;on tente de monter un disque usb via son file manager (Thunar ou Nautilus), on peut avoir un message d&#8217;erreur &#8216;not authorized&#8217;. Lorsqu&#8217;on a un environnement de bureau à la Gnome ou KDE, toutes ces histoires de gestion des droits est pris en charge de façon transparente. Mais quand on veut avoir un environnement hyper léger, il y a des manipulations  à faire pour contourner certains problèmes. Voici la marche à suivre :<!--more-->

Créer un nouveau fichier de configuration policykit :

> sudo nano /etc/polkit-1/localauthority/50-local.d/55-myconf.pkla

Le numéro et l&#8217;extension .pkla sont important. Par contre, vous pouvez mettre ce que vous voulez à la place de &#8216;myconf&#8217;.
  
Et voilà le contenu de ce fichier :

> [Dealing with disks]
  
> Identity=unix-group:plugdev
  
> Action=org.freedesktop.udisks2.filesystem-mount;org.freedesktop.udisks2.eject-media;org.freedesktop.ud$
  
> ResultAny=yes
  
> ResultInactive=yes
  
> ResultActive=yes

Il faut redémarrer DBUS car c&#8217;est lui qui pilote le daemon polkitd :

> sudo restart dbus

Vous devez relancer gnome-settings-daemon si vous l&#8217;utilisez :

> gnome-settings-daemon -r &

Voilà, c&#8217;est fait ! Branchez un disque USB et naviguez dans les fichiers. Plus de message d&#8217;erreur !
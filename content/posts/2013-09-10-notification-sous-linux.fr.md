---
title: Notification sous Linux / DWM
author: Brahim
type: post
date: 2013-09-10T13:47:25+00:00
url: /notification-sous-linux/
post_to_facebook_timeline:
  - 1
categories:
  - Linux
tags:
  - linux

---
J&#8217;ai une configuration minimaliste sur mes ordis : GNU/Linux/Ubuntu pour la couche OS et [dwm][1] pour l&#8217;interface graphique. Pour avoir un minimum de confort sur le portable, j&#8217;aime bien être alerté quand la batterie arrive à 5%. Jusque là, j&#8217;utilisais xmessage qui ouvrait une fenêtre avec le message d&#8217;alerte. Mais une fenêtre qui s&#8217;ouvre brutalement sous dwm, un &#8220;[tiling window manager][2]&#8221; ça n&#8217;a pas le même effet que sur les windows managers classiques : c&#8217;est très intrusif, surtout en plein édition de code&#8230;<!--more-->

Bref, j&#8217;ai découvert &#8220;notify-send&#8221; qui permet d&#8217;exploiter le système de notification (j&#8217;utilise notify-osd). Il s&#8217;utilise très simplement en ligne de commande :

> notify-send &#8220;Hello le monde&#8221;

L&#8217;utilitaire se trouve dans le package &#8220;libnotify-bin&#8221; (à installer donc).

Petit mémo plus complet en suivant ce lien : <http://memo-linux.com/notify-send-outil-de-notification/>

<span style="text-decoration: underline;"><strong>Note complémentaire</strong></span> : en multi-screen, la notification ne va pas aller forcément sur l&#8217;écran avec le focus. Pour y remédier, il faut forcer le suivi du focus dans notify-osd en suivant les instructions suivantes :

  * Installer et lancer _dconf-editor_
  * Aller dans _/apps/notify-osd/multihead-mode_
  * Modifier _dont-focus-follow_ en **_focus-follow_**

_Thanks to <https://bugs.launchpad.net/ubuntu/+source/notify-osd/+bug/331369/comments/13>_

 [1]: http://dwm.suckless.org/ "Lien vers le site de dwm un tiled window manager "
 [2]: http://en.wikipedia.org/wiki/Tiling_window_manager "Wikipedia en anglais sur les Tiling Window Manager"
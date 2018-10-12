---
title: 'Forcer le nom de l’interface #wifi sous #Ubuntu 18.04'
author: Brahim
type: post
date: 2018-09-07T14:31:00+00:00
url: /forcer-le-nom-de-linterface-wifi-sous-ubuntu-18-04/
categories:
  - Comment faire ?
  - Linux
  - Partage
tags:
  - console
  - howto
  - linux
  - reseau
  - shell
  - ubuntu
  - udev
  - wifi

---
Avec Udev, il est possible de modifier le nom de l&#8217;interface wifi.

Tout d&#8217;abord, on doit récupérer l&#8217;adresse mac de la carte wifi.<!--more-->

<pre>$ ip link

1: lo: &lt;LOOPBACK,UP,LOWER_UP&gt; mtu 65536 qdisc noqueue state UNKNOWN mode DEFAULT group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
2: <span style="color: #ff0000;"><strong>wlp1s0</strong></span>: &lt;BROADCAST,MULTICAST,UP,LOWER_UP&gt; mtu 1500 qdisc mq state UP mode DORMANT group default qlen 1000
    link/ether <span style="color: #ff0000;"><strong>9c:b6:d0:8a:71:11</strong></span> brd ff:ff:ff:ff:ff:ff
</pre>

Ma carte wifi s&#8217;appelle wlp1s0 et sa mac address apparait juste après le mot clé &#8220;link/ether&#8221; : 9c:b6:d0:8a:71:11.

Maintenant, on va créer ou mettre à jour le fichier udev dans le dossier /etc/udev/rules.d avec quelque chose comme suit :

<pre>$ cat /etc/udev/rules.d/60-persistent-net.rules

SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<strong><span style="color: #ff0000;">9c:b6:d0:8a:71:11</span></strong>", ATTR{type}=="1", NAME="<strong><span style="color: #ff0000;">wlan0</span></strong>"</pre>

Il vous faudra les droits root (utiliser sudo). Modifier la mac address, choisissez le nom qui vous convient puis rebooter.

Vérifier que tout est conforme avec :

<pre>$ ip link

1: lo: &lt;LOOPBACK,UP,LOWER_UP&gt; mtu 65536 qdisc noqueue state UNKNOWN mode DEFAULT group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
2: <strong><span style="color: #ff0000;">wlan0</span></strong>: &lt;BROADCAST,MULTICAST,UP,LOWER_UP&gt; mtu 1500 qdisc mq state UP mode DORMANT group default qlen 1000
    link/ether 9c:b6:d0:8a:71:11 brd ff:ff:ff:ff:ff:ff
</pre>
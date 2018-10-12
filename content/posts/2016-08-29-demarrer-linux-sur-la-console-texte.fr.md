---
title: Démarrer Linux sur la console texte
author: Brahim
type: post
date: 2016-08-29T08:41:27+00:00
url: /demarrer-linux-sur-la-console-texte/
categories:
  - Comment faire ?
  - Linux
tags:
  - console
  - démarrage
  - howto
  - linux
  - texte

---
Pour se débarraser du démarrage graphique sur Linux, on peut modifier sa configuration grub :<!--more-->

<pre># modifier la configuration grub
sudo vi /etc/default/grub

# supprimer les options splash, quiet, ... de la variable GRUB_CMDLINE_LINUX_DEFAULT
GRUB_CMDLINE_LINUX_DEFAULT="text"

# sauvegarder et relancer grub
sudo update-grub
</pre>
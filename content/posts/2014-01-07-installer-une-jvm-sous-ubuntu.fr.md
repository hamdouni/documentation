---
title: Installer une jvm sous Ubuntu avec update-alternatives
author: Brahim
type: post
date: 2014-01-07T08:50:24+00:00
url: /installer-une-jvm-sous-ubuntu/
fb_author_post_id:
  - 593076244093505
categories:
  - Comment faire ?
  - Java
  - Linux
tags:
  - howto
  - Java
  - linux

---
<span style="line-height: 1.5em;"><img class="alignleft size-thumbnail wp-image-879" alt="logo java" src="http://brahim.hamdouni.com/wp-uploads/java-150x150.jpg" width="150" height="150" />Après avoir récupéré </span><a style="line-height: 1.5em;" title="Oracle JDK Download" href="http://www.oracle.com/technetwork/java/javase/downloads/index.html" target="_blank">le tar.gz du jdk depuis chez Oracle </a><span style="line-height: 1.5em;">et décompressé dans le dossier /usr/lib/jvm, il faut utiliser la commande suivante pour l&#8217;installer comme alternatives :</span>

> sudo update-alternatives &#8211;install /usr/bin/java java /usr/lib/jvm/java-7-oracle/bin/java 1000
> 
> <!--more-->

En paramètres dans l&#8217;ordre : l&#8217;alias de la commande &#8220;java&#8221;, le nom symbolique du groupement d&#8217;alternatives ici &#8220;java&#8221; (dans le cas où on gère plusieurs jvm, on devra toujours utiliser ce nom pour ajouter les alternatives),  l&#8217;emplacement de l’exécutable (à ajuster selon la jvm utilisée) et enfin la priorité (ici 1000).

Pour sélectionner la bonne jvm, on peut utiliser la commande :

> sudo update-alternatives &#8211;config java

A réitérer pour javac, javap,javadoc &#8230; si nécessaire.
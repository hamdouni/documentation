---
title: Comment avoir un shell ZSHRC sous Windows ?
author: Brahim
type: post
date: 2005-09-06T10:44:38+00:00
url: /zshrc-et-windows/
categories:
  - Comment faire ?

---
Il est possible d&#8217;utiliser des outils traditionnellement dévolus au monde *NIX sur des plateformes Windows (c), grâce aux différents portages existants. Celui que j&#8217;utilise dèss que j&#8217;ai la malchance de travailler sur l&#8217;OS de Redmond, est le &#8220;[Gnu utilities for Win32][1]&#8220;. On y trouve ZSH, qui porte le nom de SH dans l&#8217;archive. <!--more-->

Le fichier de configuration de ZSH est &#8220;zshrc&#8221; et doit se trouver dans le HOME. Pour trouver le HOME, lancer ZSH (en double-cliquant sur &#8220;sh&#8221;) puis taper &#8220;env&#8221; pour avoir la liste des variables d&#8217;environnement à la recherche de la ligne :

> `HOME=C:/Documents and Settings/username`

Dans le fichier zshrc, vous pourrez mettre toutes les commandes nécessaire au bon fonctionnement de votre shell. Pour ma part, j&#8217;y mets le path vers les binaires et mes alias comme suit :

> `export PATH="P:/app/bin/;P:/app/jdk/bin/;P:/app/ant/bin/;$PATH" export JETTY_HOME="P:/app/jetty/" export JAVA_HOME="P:/app/jdk/" alias ll="ls -lsaF"`

 [1]: http://unxutils.sourceforge.net/
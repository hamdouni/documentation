---
title: Comment générer un fichier excel depuis Java, BSH et Hsqldb ?
author: Brahim
type: post
date: 2007-10-27T15:03:18+00:00
url: /csv-excel-java-bsh-hsqldb-et-companie/
categories:
  - Comment faire ?

---
## Objectif :

Générer un fichier excel contenant des informations issues de diverses sources au format Excel et CSV exportés depuis une base de données.

## Problèmes :

  1. Il faut pouvoir lire et écrire au format Excel
  2. Les données sont croisées via des clés que l&#8217;on retrouve dans les fichiers, mais souvent, il faut croiser 2 critères d&#8217;un même fichier pour récupérer la bonne donnée. Faire une recherche brute dans les fichiers CSV serait trop couteux.

## Solutions :

Pour (1), j&#8217;utilise la lib [jxls][1].
  
Pour (2), j&#8217;utilise la fonctionnalité [TEXT TABLE][2] de [hsqldb][3] qui permet d&#8217;utiliser des tables SQL mappés sur des fichiers CSV.
  
Les traitements sont à la charge de [bsh][4]. Le tout est orchestré par [ant][5].

 [1]: http://jxls.sourceforge.net/
 [2]: http://hsqldb.org/doc/guide/ch06.html
 [3]: http://hsqldb.org/
 [4]: http://www.beanshell.org/
 [5]: http://ant.apache.org/
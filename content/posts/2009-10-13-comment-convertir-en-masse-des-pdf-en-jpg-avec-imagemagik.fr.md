---
title: Comment convertir en masse des PDF en JPG avec ImageMagik
author: Brahim
type: post
date: 2009-10-13T09:34:19+00:00
url: /comment-convertir-en-masse-des-pdf-en-jpg-avec-imagemagik/
categories:
  - Comment faire ?
tags:
  - convert
  - DPI
  - ImageMagik
  - JPEG
  - JPG
  - linux
  - PDF
  - ubuntu

---
J&#8217;avais un grand nombre de PDF à convertir en JPG pour être intégré en GED. Des PDF qui devaient rester imprimable après coup, donc qui devaient garder un haut niveau de densité (au moins 300 dpi).

Avec ImageMagik, et plus précisément &#8220;convert&#8221; ainsi que quelques commandes shell sous linux, le tour était joué :

> for i in \`ls *.PDF\`; do f=\`basename $i .PDF\`; convert -density 300 $i $f.jpg; done

Comment ça marche ?

  1. Une boucle &#8220;for&#8221; sur tous les fichiers avec l&#8217;exention PDF
  2. Un découpage du nom du fichier pour enlever l&#8217;extension : basename $i .PDF
  3. La conversion avec préservation des 300 dpi : convert -density 300

Et voilà !
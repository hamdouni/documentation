---
title: 'Vidéo background [FR]'
author: Brahim
type: post
date: 2014-05-06T13:40:21+00:00
url: /video-background-fr/
post_to_facebook_timeline:
  - 1
categories:
  - Comment faire ?
tags:
  - HTML5

---
> La mode n&#8217;est plus aux photos géantes en fond de page. Maintenant, c&#8217;est au tour des vidéos !

Comme ça, vous voulez carrément afficher une vidéo comme fond de votre site web ? Grâce à HTML5 et CSS3, c&#8217;est super simple. Suivez le guide !<!--more-->

Jetez d&#8217;abord un oeil sur le résultat : <a title="Video Background Effect" href="http://hamdouni.github.io/video-background" target="_blank">Démo &#8220;Les routes du paradis&#8221;</a>. Chouette, non ?

Commençons par l&#8217;html :

<pre>&lt;video src="votre-video.mp4"&gt;&lt;/video&gt;
&lt;div&gt; votre texte ici &lt;/div&gt;</pre>

Au tour du css :

<pre>video {
  z-index: -999;
  position: fixed;
  min-height: 100%;
  min-width: 100%;
}</pre>

Le z-index force la vidéo à rester au fond de la page (le -999 correspond à la profondeur). Tout ce qui aura un index plus grand, apparaîtra au dessus.

position:fixed est obligatoire pour être certain que la superposition se fasse avec tous les éléments que vous ajouterez après.

Enfin, les min height et width tags à 100% font que la vidéo prendra toute la place disponible.

Pour centrer le texte horizontalement et verticalement, il faut ajouter le css suivant :

<pre>html, body { width: 100%; height: 100%; }
body {display:table;}
div {display: table-cell; vertical-align: middle; text-align: center;}</pre>

Et voilà !

Cette méthode fonctionne sur les navigateurs principaux : je l&#8217;ai testé sur Firefox, Chrome et Safari. Et cela marche aussi sur IE9 !
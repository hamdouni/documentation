---
title: 'Speech tasks : une webapp avec reconnaissance vocale'
author: Brahim
type: post
date: 2014-06-30T15:58:25+00:00
url: /speech-tasks-une-webapp-avec-reconnaissance-vocale/
fb_author_post_id:
  - 676023825798746
facebook_status_messages:
  - 'a:1:{i:0;a:2:{s:7:"message";s:98:"Posted to <a href="https://www.facebook.com/676023825798746" target="_blank">Facebook Timeline</a>";s:5:"error";b:0;}}'
post_to_facebook_timeline:
  - 1
categories:
  - Comment faire ?
  - Fun
tags:
  - JavaScript

---
**[màj du 1/7/14 : version française]** Grâce à <a title="annyang reconnaissance vocale en JS" href="https://www.talater.com/annyang/" target="_blank">annyang</a>, la librairie javascript de reconnaissance vocale de Tal Alter, on peut aisément ajouter le pilotage par la voix à ses applications web. Voilà une démo de ce que j&#8217;ai pu faire pour ajouter cette fonctionnalité à une appli de TODO que j&#8217;avais faites pour tester <a title="Angular Light" href="http://angularlight.org/" target="_blank">Angular Light</a> :<!--more-->

<p style="text-align: center;">
  <a title="Demo Speech tasks" href="http://barim.us/speechtasks/index_FR.html" target="_blank">La démo c&#8217;est par ici </a>
</p>

<p style="text-align: left;">
  Si vous avez un micro, l&#8217;application commencera par vous demander de l&#8217;autoriser à y accéder. Ensuite, vous pouvez donner des ordres en français, par exemple :
</p>

  * _**tâche**_ emmener la voiture au garage
  * _**tâche**_ récupérer le livre à la librairie
  * _**annuler**_
  * _**supprimer tout**_

Vous verrez la liste évoluer en fonction de vos ordres 🙂 Pour info, l&#8217;app utilise le LocalStorage pour sauvegarder vos tâches, donc la prochaine fois que vous retournez dessus (avec le même navigateur), votre liste réapparaît. C&#8217;est magique ! Testé et approuvé avec Chrome.
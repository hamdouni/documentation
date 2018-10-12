---
title: Comment intégrer Firefox et Thunderbird ?
author: Brahim
type: post
date: 2007-12-18T14:36:34+00:00
url: /integration-firefox-thunderbird/
categories:
  - Comment faire ?
tags:
  - howto

---
<p align="left">
  Après avoir fait le ménage sur mon Ubuntu, et plus particulièrement après avoir désinstallé tout un tas de packages gnome, j&#8217;ai perdu la liaison entre Firefox et Thunderbird : un clic sur un lien depuis Thunderbird n&#8217;ouvrait plus Firefox, et vice-et-versa, impossible d&#8217;avoir un mailto: qui ouvre Thunderbird.
</p>

Pour réparer dans Firefox, il faut :

  * cd ~/.mozilla/firefox/{des caractères.default}
  * ouvrir ou créer s&#8217;il n&#8217;existe pas le fichier &#8220;user.js&#8221;
  * ajouter à la fin la ligne : user_pref(&#8220;network.protocol-handler.app.mailto&#8221;,&#8221;/usr/bin/thunderbird&#8221;);

Ajuster selon l&#8217;emplacement de l&#8217;exécutable Thunderbird.

Pour réparer dans Thunderbird, il faut :

  * cd ~/.mozilla-thunderbird/{des caractères.default}
  * ouvrir ou créer s&#8217;il n&#8217;existe pas le fichier &#8220;user.js&#8221;
  * ajouter à la fin la ligne : user_pref(&#8220;network.protocol-handler.app.http&#8221;, &#8220;/usr/bin/firefox&#8221;);

Ajuster selon l&#8217;emplacement de l&#8217;exécutable Firefox.
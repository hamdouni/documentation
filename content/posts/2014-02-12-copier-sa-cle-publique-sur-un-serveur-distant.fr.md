---
title: Copier sa clé publique sur un serveur distant
author: Brahim
type: post
date: 2014-02-12T14:25:38+00:00
url: /copier-sa-cle-publique-sur-un-serveur-distant/
fb_author_post_id:
  - 609973789070417
post_to_facebook_timeline:
  - 1
categories:
  - Comment faire ?
  - Linux
tags:
  - howto
  - linux
  - sécurité

---
Pour faciliter l&#8217;administration de machines distantes sous Linux, c&#8217;est mieux de ne pas gérer de mot de passe et d&#8217;utiliser des clés de sécurité.

Mais une fois qu&#8217;on a créé sa clé avec la commande keygen, c&#8217;est très facile de la recopier sur le serveur distant en une seule commande :<!--more-->

> ssh-copy-id -i votrecle.pub compte@serveurdistant.dom

Le premier paramètre est le chemin jusqu&#8217;au fichier contenant votre clé publique (par exemple ~/.ssh/id_dsa.pub) que vous avez créé avec la commande ssh-keygen.

Le second paramètre est le serveur distant avec le compte sur ce serveur. La commande vous demandera le mot de passe du compte pour s&#8217;assurer que c&#8217;est bien à vous.

Ensuite, vous pouvez vous connecter directement au serveur distant avec :

> ssh compte@serveurdistant.doom

Aucun mot de passe ne vous sera demandé. Yes !
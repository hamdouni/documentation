---
title: Comment utiliser Skype et la Logitech Quick Messenger sous Ubuntu 9.04
author: Brahim
type: post
date: 2009-08-27T13:16:16+00:00
url: /comment-utiliser-skype-et-la-logitech-quick-messenger-sous-ubuntu-9-04/
categories:
  - Comment faire ?
  - Matériel
tags:
  - howto
  - linux
  - logitech
  - quickam messenger
  - quickcam
  - ubuntu
  - webcam

---
En essayant de réhabiliter un vieux PC avec la dernière Ubuntu (Jaunty 9.04), je me suis confronté à un souci de configuration de ma webcam avec Skype : les gens avec qui je travaille sont sur Skype et ne sont pas informaticiens (juste pour éviter les &#8220;mais skype c&#8217;est mal, faut utiliser xxx&#8221; &#8211; mettre votre logiciel libre préféré à la place des xxx)

Skype reconnait bien ma webcam : une Logitech Quickcam Messenger. Mais l&#8217;image obtenu dans l&#8217;outil de test est brouillée. Cela ressemble à une espèce de neige qu&#8217;on avait sur les télés qui n&#8217;étaient pas réglées sur la bonne fréquence (la bonne vieille VHF/UHF avant le numérique et le tripe play pour les plus jeunes). Sauf que la neige est verte au lieu du nostalgique gris d&#8217;antan. Bref, pour en revenir à la webcam, c&#8217;est irritant que ça ne marche pas du premier coup avec Skype alors que cela fonctionne parfaitement avec d&#8217;autres logiciels (Cheese par ex.)

Un petit &#8220;lsusb&#8221; dans la console m&#8217;indique :

> Bus 002 Device 004: ID 046d:08da Logitech, Inc. QuickCam Messanger

Tiens ? C&#8217;est indiqué &#8220;Messanger&#8221; alors qu&#8217;il s&#8217;agit d&#8217;une &#8220;Messenger&#8221;. Sûrement une faute de typo dans la base de données matériels.

Mais avec l&#8217;id &#8220;046d:08da&#8221; aucun doute possible. Hop, mon Firefox, Google et quelques secondes plus tard, je lit que Skype s&#8217;appuie sur la librairie de vidéo pour linux (v4l) en version 1. Or, par défaut c&#8217;est la version 2 qui est activée dans Ubuntu Jaunty 9.04. Heureusement, Ubuntu intègre encore la v1 pour des raisons de compatibilité (bien vu).

La solution pour faire marcher tout ça ensemble passe par une &#8220;surcharge&#8221; de la variable d&#8217;environnement avant l&#8217;appel de skype pour forcer skype à utiliser l&#8217;ancienne lib :

> LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype

Ok, alors pour ne pas à avoir à retaper ça tout le temps, il suffit de mettre la commande dans un script shell. Exemple pour moi qui ai un dossier &#8220;bin&#8221; dans mon home :

> echo LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so /usr/bin/skype > ~/bin/skype
> 
> chmod u+x ~/bin/skype

Comme mon dossier &#8220;bin&#8221; est déclaré dans la variable &#8220;PATH&#8221; en premier, c&#8217;est donc le skype de mon &#8220;bin&#8221; qui sera exécuté au lieu du &#8220;skype&#8221; installé.

_source : <a title="Sur Bugzilla en anglais : Bug 11741 -  Webcam: Logitech QuickCam Communicate won't work with 2.6.27  " href="http://bugzilla.kernel.org/show_bug.cgi?id=11741" target="_blank">http://bugzilla.kernel.org/show_bug.cgi?id=11741</a>_
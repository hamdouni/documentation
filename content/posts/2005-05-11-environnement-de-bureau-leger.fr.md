---
title: Comment alléger son bureau Linux ?
author: Brahim
type: post
date: 2005-05-11T12:44:56+00:00
url: /environnement-de-bureau-leger/
categories:
  - Comment faire ?

---
Cet article a pour objet la mise en place d&#8217;un environnement de bureau graphique sous Linux utilisant peu de ressources systèmes.
  
Il vise à donner une alternative acceptable face aux mastodontes que sont [KDE][1] ou [GNOME][2], sur des configurations matérielles &#8220;dépassées&#8221;.
  
Les outils utilisés sont : ROX-Filer, Oroborus, FBPanel.
  
<!--more-->L&#8217;une des applications les plus utilisées sur des systèmes dits &#8220;utilisateur&#8221; (en opposition aux serveurs) est l&#8217;environnement de bureau. Cette application est l&#8217;interface principale et permet l&#8217;accés aux autres applications via différents composants :

  * le menu permet d&#8217;accéder à la plupart des commandes disponibles sur le système
  * la barre des tâches donne une vue sur les applications actives
  * les icônes du bureau sont des raccourcies vers des dossiers, fichiers ou applications
  * la zone de notification (tray icon), comme la barre des tâches mais en plus compact, permet de voir mais également de piloter les tâches travaillant en arrière plan (antivirus, messager,&#8230;)

Notons également des composants fonctionnels non immédiatement visibles comme le copier/coller ou le drag&drop. Sous Linux, l&#8217;ensemble de ces composants, et bien plus encore, se trouve dans les 2 applications de référence dans ce domaine : KDE et GNOME. Cependant, ces derniers ont une tendance à consommer des ressources importantes, empéchant leur utilisation sur des machines dépassées.
  
Pourtant, en choisissant d&#8217;autres composants, il est possible d&#8217;obtenir un environnement de travail utilisable sur ce genre de machines. Les composants choisis sont les suivants :

  * ROX-Filer gére les icônes du bureau et propose un gestionnaire de fichier efficace
  * Oroborus est le gestionnaire de fenêtre
  * FBPanel contient un menu, des boutons raccourcies, une barre des tâches et une zone de notification

Pour un environnement encore plus léger et si l&#8217;on peut se passer des icônes du bureau, il n&#8217;est pas nécessaire d&#8217;installer ROX-Filer. Comment faire ? D&#8217;abord installer les différentes applications. Par exemple, sous Debian (à partir de testing) :

> sudo apt-get install oroborus fbpanel rox-filer

Accéptez d&#8217;installer tous les paquets dépendants nécessaires. Ensuite, suivez la configuration par application :

**Xinit/Xsession**
  
Suivant que vous lanciez votre environnement graphique à la main via &#8220;startx&#8221; ou par un gestionnaire de session comme &#8220;gdm&#8221; ou &#8220;xdm&#8221;, le fichier à modifier est respectivement ~/.xinitrc ou ~/.xsession. Pour ma part, ne faisant pas de distinction entre ces deux modes, j&#8217;ai créé un fichier .xsession sur lequel j&#8217;ai aliasé le .xinitrc. Ainsi, quelle que soit le mode de lancement d&#8217;X, je retrouve la même configuration.
  
Pour cela, éditez dans votre home, le fichier .xsession pour qu&#8217;il ressemble à ce qui suit :

> rox -pbureau & oroborus & exec fbpanel

Si vous le souhaitez, vous pouvez ajouter en début de ce fichier d&#8217;autres applications à lancer au démarrage, comme suit :

> gaim & xscreensaver -nosplash & rox -pbureau & oroborus & exec fbpanel

pour lancer &#8220;gaim&#8221; et l&#8217;économiseur d&#8217;écran. Pour créer l&#8217;alias .xinitrc, faites comme suit :

> ln -s ~/.xsession ~/.xinitrc

**Oroborus**
  
Copiez le fichier de configuration dans votre dossier personnel :

> cp /usr/share/oroborus/defaults ~/.oroborusrc

En éditant ce fichier, vous pouvez modifier l&#8217;aspect et certains comportement d&#8217;Oroborus, par exemple, pour se rapprocher de ce qu&#8217;on trouve couramment :

> theme=/usr/share/oroborus/themes/windows scheme=/usr/share/oroborus/schemes/windows double\_click\_action=maximize click\_to\_focus=true

**Rox**
  
Quand vous aurez redémarrer votre environnement graphique, vous obtiendrez une icône &#8220;home&#8221; qui pointera sur votre dossier par défaut. En double cliquant dessus, vous ouvrez Rox-filer qui est le gestionnaire de fichier de Rox. Naviguer jusqu&#8217;aux fichiers souhaités et faites les glisser de la fenêtre Rox-filer vers le fond de l&#8217;écran.
  
Rox est capable d&#8217;utiliser d&#8217;autres icônes que celle par défaut. Cliquez sur une icône avec le bouton droit et choisisez dans le menu qui apparait, sous le nom du fichier, &#8220;fixer icone&#8221;. Ensuite, faites glisser un fichier icône dans le cadre qui apparait.
  
Vous trouverez, en annexes, le site de la jolie collection d&#8217;icône Nuvola de David Vignoni.

**Fbpanel** **
  
** Fbpanel s&#8217;affiche en bas de votre écran avec un bouton menu, quelques raccourcies pour lancer des programmes, une barre des tâches, un zone de notification (tray icon) et une horloge. Vous pouvez personnaliser le contenu de Fbpanel en créant le dossier .fbpanel dans votre dossier personnel et y recopier le fichier de configuration &#8220;default&#8221; qui se trouve sur &#8220;/etc/fbpanel/&#8221; ****

> cp /etc/fbpanel/default ~/.fbpanel/

En l&#8217;éditant, vous trouverez les différentes sections controlant Fbpanel.

Annexes

> Site d&#8217;Oroborus : [http://www.oroborus.org][3]
  
> Icônes Nuvola de David Vignoni : <http://www.icon-king.com/>
  
> Site de Rox Filer : <http://rox.sourceforge.net>
  
> Site de Fbpanel : [http://fbpanel.sourceforge.net][4]

 [1]: http://kde.org
 [2]: http://gnome.org
 [3]: http://www.oroborus.org/
 [4]: http://fbpanel.sourceforge.net/
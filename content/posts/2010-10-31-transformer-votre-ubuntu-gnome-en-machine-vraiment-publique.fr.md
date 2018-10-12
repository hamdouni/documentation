---
title: Transformer votre Ubuntu Gnome en machine vraiment publique
author: Brahim
type: post
date: 2010-10-31T17:54:28+00:00
url: /transformer-votre-ubuntu-gnome-en-machine-vraiment-publique/
categories:
  - Comment faire ?
tags:
  - gnome
  - howto
  - linux
  - ubuntu

---
Un ami m&#8217;a demandé le nécessaire pour rendre son Ubuntu Gnome complétement public, c&#8217;est-à-dire qu&#8217;aucun mot de passe ne soit demandé. Je pensais que ce serait simple à priori. Et bien il en n&#8217;est rien. Voici un petit mémo des étapes à suivre pour rendre son Ubuntu Gnome complétement libre d&#8217;accès !

## Virer le mot de passe de connexion

Il est possible de se connecter automatiquement sans demander de mot de passe. Pour cela, il faut modifier le paramétrage de la fenêtre de connexion : aller dans le menu **Système**, puis **Administration** et sélectionner l&#8217;entrée **Fenêtre de connexion**.

[<img class="aligncenter size-full wp-image-400" title="Paramètres de la fenêtre de connexion" src="http://brahim.hamdouni.com/wp-uploads//Capture-Paramètres-de-la-fenêtre-de-connexion.png" alt="Paramètres de la fenêtre de connexion" width="461" height="257" srcset="http://brahim.hamdouni.com/wp-uploads/Capture-Paramètres-de-la-fenêtre-de-connexion.png 461w, http://brahim.hamdouni.com/wp-uploads/Capture-Paramètres-de-la-fenêtre-de-connexion-300x167.png 300w" sizes="(max-width: 461px) 100vw, 461px" />][1]

Cliquez sur le bouton &#8220;Déverrouiller&#8221; et saisissez votre mot de passe lorsqu&#8217;on vous le demande. Vous aurez alors la possibilité de sélectionner la case **&#8220;Se connecter automatiquement&#8221;**, puis cliquez sur le bouton **Fermer**.

La prochaine fois que vous allumez l&#8217;ordinateur, vous arriverez automatiquement sur le bureau d&#8217;Ubuntu sans avoir indiqué votre mot de passe. Mais ce n&#8217;est pas finit : si vous avez un accès par Wifi, Ubuntu va vous demander de saisir votre mot de passe pour déverrouiller l&#8217;accès Internet. L&#8217;étape suivante explique comment se débarrasser de cette corvée.

## Dégager le mot de passe pour le Wifi

Lorsqu&#8217;on rentre une clé wifi, Ubuntu, et plus précisément le gestionnaire de bureau Gnome, sauvegarde cette clé wifi dans un trousseau de clés afin de vous éviter de le taper à chaque fois. L&#8217;accès à ce trousseau est protégé afin d&#8217;éviter qu&#8217;une autre personne y ait accès. Mais lorsqu&#8217;on met en place la connexion automatique de l&#8217;étape précédente, Gnome considère que l&#8217;accès au trousseau n&#8217;est pas sûr et vous demande votre mot de passe pour ouvrir votre accès Internet. C&#8217;est gentil de se préoccuper de notre sécurité, mais en l&#8217;occurrence, là c&#8217;est voulu de ne pas protéger l&#8217;accès puisqu&#8217;on fait confiance à tous les utilisateurs. On va donc demander à Gnome de ne plus nous embêter, en spécifiant un mot de passe vide pour le trousseau. Pour l&#8217;ouvrir, allons dans le menu **Application**, puis **Accessoires** et sélectionnez **Mots de passe et clés de chiffrement**.

<img class="aligncenter size-full wp-image-401" title="Mots de passe et clés de chiffrement" src="http://brahim.hamdouni.com/wp-uploads//Capture-Mots-de-passe-et-clés-de-chiffrement.png" alt="Mots de passe et clés de chiffrement" width="640" height="476" srcset="http://brahim.hamdouni.com/wp-uploads/Capture-Mots-de-passe-et-clés-de-chiffrement.png 640w, http://brahim.hamdouni.com/wp-uploads/Capture-Mots-de-passe-et-clés-de-chiffrement-300x223.png 300w" sizes="(max-width: 640px) 100vw, 640px" />

Cliquez avec le bouton droit de votre souris sur **Mots de passe : login** et sélectionner **Modifier le mot de passe**. Saisissez alors votre mot de passe dans **Ancien mot de passe**, mais laissez vide les 2 autres champs et cliquez sur le bouton **Valider**.

Un message va vous avertir que l&#8217;opération n&#8217;est pas sûre. Ne vous inquiétez pas et cliquez sur le bouton **Utilisez un stockage non sûr**. Refermez les fenêtres, Ubuntu ne vous demandera plus de mot de passe&#8230; enfin presque. Si vous avez un économiseur d&#8217;écran, il est possible que l&#8217;écran se verrouille et vous oblige à saisir votre mot de passe. L&#8217;étape suivante vous explique comment s&#8217;en affranchir.

## Sortir de l&#8217;économiseur d&#8217;écran sans mot de passe

Cette étape est simple : allez dans le menu **Système** puis **Préférences** et choisissez **Économiseur d&#8217;écran**.

<img class="aligncenter size-full wp-image-402" title="Préférences de l'économiseur d'écran" src="http://brahim.hamdouni.com/wp-uploads//Capture-Préférences-de-léconomiseur-décran.png" alt="Préférences de l'économiseur d'écran" width="616" height="515" srcset="http://brahim.hamdouni.com/wp-uploads/Capture-Préférences-de-léconomiseur-décran.png 616w, http://brahim.hamdouni.com/wp-uploads/Capture-Préférences-de-léconomiseur-décran-300x250.png 300w" sizes="(max-width: 616px) 100vw, 616px" />

Décocher la case **Verrouiller l&#8217;écran quand l&#8217;économiseur d&#8217;écran est actif** puis cliquez sur le bouton **Fermer**.

Vous n&#8217;aurez plus à saisir de mot de passe lorsque l&#8217;économiseur d&#8217;écran s&#8217;active. Mais, ce n&#8217;est pas encore la fin de l&#8217;histoire. Lorsque l&#8217;ordinateur se met en veille (batterie faible ou mise en veille volontaire) et que vous le rallumez, il va commencer par vous demander votre mot de passe. On peut aussi changer ça en suivant la dernière étape.

## Retour direct après une mise en veille ou une hibernation

L&#8217;ultime étape est aussi la plus complexe car il n&#8217;y a pas, à ma connaissance, de façon directe pour le faire. Pour y arriver, il faut lancer l&#8217;outil de paramétrage de Gnome et fouiller dedans pour modifier certaines options. Commençons par lancer l&#8217;outil : maintenez la touche **alt** et appuyer sur la touche **F2**.

[<img class="alignnone size-full wp-image-403" title="Lancer une application" src="http://brahim.hamdouni.com/wp-uploads//Capture-Lancer-une-application.png" alt="Lancer une application" width="572" height="142" srcset="http://brahim.hamdouni.com/wp-uploads/Capture-Lancer-une-application.png 572w, http://brahim.hamdouni.com/wp-uploads/Capture-Lancer-une-application-300x74.png 300w" sizes="(max-width: 572px) 100vw, 572px" />][2]

Le lanceur d&#8217;application s&#8217;ouvre : saisissez **gconf-editor** et cliquez sur le bouton **Lancer**.

[<img class="alignnone size-full wp-image-404" title="Éditeur de configuration" src="http://brahim.hamdouni.com/wp-uploads//Capture-Éditeur-de-configuration-lock.png" alt="Éditeur de configuration" width="547" height="428" srcset="http://brahim.hamdouni.com/wp-uploads/Capture-Éditeur-de-configuration-lock.png 547w, http://brahim.hamdouni.com/wp-uploads/Capture-Éditeur-de-configuration-lock-300x234.png 300w" sizes="(max-width: 547px) 100vw, 547px" />][3]

Descendez l&#8217;arborescence comme suit : d&#8217;abord **apps** puis **gnome-power-management** et enfin **lock**.
  
Décochez toutes les cases sur la partie droite, comme dans la copie d&#8217;écran ci-dessous et refermez la fenêtre.

Cette fois, c&#8217;est bon, on ne vous demandera plus de mot de passe&#8230; enfin, presque 🙂

Dans le cas où vous avez des tâches administratives à faire, comme mettre à jour les applications, on vous le demandera encore. Mais là, c&#8217;est une autre affaire !

 [1]: http://brahim.hamdouni.com/wp-uploads//Capture-Paramètres-de-la-fenêtre-de-connexion.png
 [2]: http://brahim.hamdouni.com/wp-uploads//Capture-Lancer-une-application.png
 [3]: http://brahim.hamdouni.com/wp-uploads//Capture-Éditeur-de-configuration-lock.png
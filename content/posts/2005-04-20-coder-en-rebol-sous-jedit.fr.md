---
title: Comment coder en Rebol sous Jedit ?
author: Brahim
type: post
date: 2005-04-20T11:17:10+00:00
url: /coder-en-rebol-sous-jedit/
categories:
  - Comment faire ?

---
Jedit peut-être utilisé pour coder en Rebol. Il intègre en standard une colorisation syntaxique, et moyennant quelques manipulations, permet d&#8217;utiliser l&#8217;interpréteur Rebol. <!--more-->

Voici ma configuration :
  
&#8211; Debian testing
  
&#8211; JVM : Sun 1.4.2
  
&#8211; Jedit : 4.2
  
&#8211; Rebol : console et view

Je pars du principe que tout est installé sur votre machine, et que les exécutables &#8220;rebol&#8221; (pour la console) et &#8220;rebolview&#8221; (pour view) sont dans votre PATH.

Dans Jedit,
  
1. installer le plugin &#8220;console&#8221; :
  
Menu Plugins > Plugins Manager > Install
  
2. ajouter un gestionnaire rebol :
  
Mettre le fichier [rebol.xml][1] dans le dossier ~/.jedit/console/commando
  
3. paramétrer rebol :
  
Menu Plugins > Plugins Options Ouvrir &#8220;Console&#8221; et cliquer sur &#8220;Compile & Run&#8221;
  
Dans la colonne &#8220;mode&#8221;, chercher la ligne avec &#8220;rebol&#8221;.
  
Dans la colonne &#8220;Compiler&#8221; et &#8220;Interpreter&#8221;, choisir &#8220;rebol&#8221; puis valider.
  
Cliquer sur &#8220;General&#8221; sous &#8220;Console&#8221; et cocher &#8220;Commando tool bar&#8221; pour avoir une barre de raccourcie.

Un bouton &#8220;rebol&#8221; apparait sur l&#8217;interface principal de Jedit.
  
A chaque fois que vous cliquez, une fenêtre apparait vous permettant de spécifier la &#8220;target&#8221; (view ou console) et le &#8220;output directory&#8221; qui est le dossier où doit être lancé le programme rebol (par défaut, là où se trouve le fichier source).
  
Une fenêtre &#8220;shell&#8221; s&#8217;ouvre exécutant le code rebol.

 [1]: http://hamdouni.com/files/rebol.xml
---
title: "Comment contourner l'erreur d'Eclipse quand on installe Jetty Launcher ?"
author: Brahim
type: post
date: 2006-03-17T15:59:18+00:00
url: /eclipse-jetty-launcher/
categories:
  - Comment faire ?

---
<a href="http://jettylauncher.sourceforge.net/" target="_blank">Jetty Launcher</a> est un plugin qui permet de piloter Jetty depuis Eclipse. La version 1.3.0 de Jetty Launcher ne fonctionne pas directement avec Eclipse version 3.1.0 : en suivant la procédure pour l&#8217;utiliser, le message d&#8217;erreur suivant apparait dans l&#8217;Error Log (via menu Window / Show View) :
  
<!--more--> Problems occurred when invoking code from plug-in: &#8220;org.eclipse.jface&#8221;.

Pour y remédier, il faut déjarer le plugin dans le dossier Eclipse idoine. Par exemple :
  
cd /usr/lib/eclipse/plugins mkdir com.iw.plugins.jettyLauncher\_1.3.0 cd com.iw.plugins.jettyLauncher\_1.3.0 unzip ../com.iw.plugins.jettyLauncher_1.3.0.jar

Une fois fait, supprimer le jar
  
rm ../com.iw.plugins.jettyLauncher_1.3.0.jar

Relancer Eclipse et suiver les instructions d&#8217;utilisation de jettyLauncher.
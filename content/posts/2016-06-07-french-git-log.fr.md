---
title: French Git Log
author: Brahim
type: post
date: 2016-06-07T09:25:33+00:00
url: /french-git-log/
categories:
  - Comment faire ?

---
<img class="size-full wp-image-1501 aligncenter" src="http://brahim.hamdouni.com/wp-uploads/french-git.png" alt="french git example" srcset="http://brahim.hamdouni.com/wp-uploads/french-git.png 782w, http://brahim.hamdouni.com/wp-uploads/french-git-300x135.png 300w, http://brahim.hamdouni.com/wp-uploads/french-git-768x345.png 768w, http://brahim.hamdouni.com/wp-uploads/french-git-600x269.png 600w, http://brahim.hamdouni.com/wp-uploads/french-git-624x280.png 624w" sizes="(max-width: 706px) 89vw, (max-width: 767px) 82vw, 740px" /><!--more-->

<pre>git log --pretty='format:%Cblue%h%Creset %ad %Cred%&lt;(8,trunc)%an%Creset%Cgreen%d%Creset %s' --date=short</pre>

Utiliser un &#8220;pretty format&#8221; pour afficher l&#8217;historique de Git avec des couleurs et des columns à taille fixe :

%Cblue &#8230; %Creset
:   indique le début et la fin d&#8217;une portion colorée. Le rouge (red) et le vert (green) sont aussi utilisables.

%h
:   format court du hash du commit

%ad
:   format court de la date du commit avec l&#8217;option complémentaire &#8211;date=short

%<(8,trunc)
:   fixe la taille du prochain élément à 8 caractères (complété d&#8217;espace à droite si nécessaire ou coupé si trop long)

%an
:   le nom de l&#8217;auteur du commit

%d
:   nom de la référence (branch, tag, &#8230;)

%s
:   commentaire du commit
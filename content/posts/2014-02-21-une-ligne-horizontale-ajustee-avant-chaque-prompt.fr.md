---
title: Une ligne horizontale ajustée avant chaque PROMPT
author: Brahim
type: post
date: 2014-02-21T11:43:41+00:00
url: /une-ligne-horizontale-ajustee-avant-chaque-prompt/
fb_author_post_id:
  - 613950228672773
categories:
  - Comment faire ?
  - Linux
tags:
  - howto
  - linux

---
Ce serait chouette d&#8217;arriver à afficher une ligne horizontale dans le terminal, avant chaque commande : ça permettrait de séparer visuellement les résultats d&#8217;exécution.<figure id="attachment_932" style="width: 735px" class="wp-caption aligncenter">

<img class="size-full wp-image-932 " alt="Capture du 2014-02-21 12:04:47" src="http://brahim.hamdouni.com/wp-uploads/Capture-du-2014-02-21-120447.png" width="735" height="425" srcset="http://brahim.hamdouni.com/wp-uploads/Capture-du-2014-02-21-120447.png 735w, http://brahim.hamdouni.com/wp-uploads/Capture-du-2014-02-21-120447-300x173.png 300w" sizes="(max-width: 735px) 100vw, 735px" /><figcaption class="wp-caption-text">C&#8217;est trop puissant le shell ! 😀</figcaption></figure> 

<!--more-->Evidemment, on veut un truc plus évolué que d&#8217;afficher un nombre de fois fixe le même caractère car notre fenêtre peut avoir une largeur quelconque. Exclues les solutions du type :

<pre>echo --------------------</pre>

En googlant, on trouve facilement plusieurs solutions, et après quelques tests et simplifications, je finis par cette commande :

<pre>export PROMPT_COMMAND="printf '%*s' `tput cols` | tr ' ' '_' "</pre>

  * printf &#8216;%*s&#8217; : affiche un nombre d&#8217;espace déterminé par le paramètre suivante (tput)
  * tput cols : donne le nombre de colonne du terminal. On le met entre anti-guillement pour qu&#8217;il soit évalué (et ça va générer le problème, cf plus bas)
  * tr &#8216; &#8216; &#8216;_&#8217; : remplace les espaces par des undescores depuis la chaîne reçue via le pipe

Ça fonctionne presque parfaitement. Lorsqu&#8217;on lance le terminal, la ligne horizontale prend bien la largeur. Mais lorsqu&#8217;on change la taille de la fenêtre, la largeur n&#8217;est pas ajustée, et le résultat est moche :<figure id="attachment_937" style="width: 611px" class="wp-caption aligncenter">

<img class="size-full wp-image-937 " alt="Capture du 2014-02-21 12:26:55" src="http://brahim.hamdouni.com/wp-uploads/Capture-du-2014-02-21-122655.png" width="611" height="430" srcset="http://brahim.hamdouni.com/wp-uploads/Capture-du-2014-02-21-122655.png 611w, http://brahim.hamdouni.com/wp-uploads/Capture-du-2014-02-21-122655-300x211.png 300w" sizes="(max-width: 611px) 100vw, 611px" /><figcaption class="wp-caption-text">Vous avez remarqué le trait qui se poursuit sur les lignes suivantes ?    
C&#8217;est très moche, hein ?</figcaption></figure> 

Cette effet est du à l&#8217;ordre d&#8217;évaluation du shell : au moment où PROMPT\_COMMAND est créée, toutes les variables sont d&#8217;abord évaluées. Si on regarde le contenu de PROMPT\_COMMAND, on comprend mieux le problème :

<pre>$ echo $PROMPT_COMMAND
 printf '%*s' 237 | tr ' ' '_'</pre>

La commande tput est évaluée, et sa valeur vient alimenter statiquement PROMPT_COMMAND. Mais on peut contourner ce comportement, en obligeant l&#8217;évaluation systématique de tput. Voilà une solution :

<pre>#PRINT LINE BEFORE EACH PROMPT
 print_line() {
 printf '%*s\n' `tput cols` | tr ' ' '_'
 }
 export PROMPT_COMMAND="print_line"</pre>

L&#8217;astuce consiste à passer par une fonction (ici print_line) qui est évaluée à chaque appel. Il ne reste plus qu&#8217;à insérer ce bout de code dans votre .bashrc et voilà !
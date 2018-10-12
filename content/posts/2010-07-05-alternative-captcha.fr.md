---
title: Alternative au Captcha
author: Brahim
type: post
date: 2010-07-05T19:53:58+00:00
url: /alternative-captcha/
categories:
  - Ergonomie
  - Invention
tags:
  - Ergonomie
  - IHM
  - Invention

---
Le [captcha][1] ? C&#8217;est ce test qu&#8217;on vous demande de réussir pour prouver que vous n&#8217;êtes pas un robot lorsque vous remplissez un formulaire. La plupart du temps, on nous demande de recopier un texte complétement déformé ou brouillé. C&#8217;est enquiquinant et pas toujours évident d&#8217;arriver à décrypter le texte.

<p style="text-align: center;">
  <img class="size-medium wp-image-341 aligncenter" title="Google Captcha" src="http://brahim.hamdouni.com/wp-uploads/google-captcha-300x123.png" alt="" width="300" height="123" srcset="http://brahim.hamdouni.com/wp-uploads/google-captcha-300x123.png 300w, http://brahim.hamdouni.com/wp-uploads/google-captcha.png 346w" sizes="(max-width: 300px) 100vw, 300px" />
</p>

<p style="text-align: center;">
  <p>
    Du coup, quand je vois d&#8217;autre façon de traiter le sujet, j&#8217;applaudis. Et là, c&#8217;est le cas chez <a title="Le site de &quot;They make apps&quot; en anglais" href="http://theymakeapps.com/">&#8220;They Make Apps&#8221;</a>, un site de référencement de développeurs qui a introduit une manière originale de séparer le bon grain de l&#8217;ivraie.
  </p>
  
  <p>
    C&#8217;est sur le formulaire d&#8217;inscription que cela se passe :
  </p>
  
  <p style="text-align: center;">
    <a href="http://brahim.hamdouni.com/wp-uploads//theymakeapps-captcha.png"><img class="size-medium wp-image-346  aligncenter" title="Captcha They make apps" src="http://brahim.hamdouni.com/wp-uploads//theymakeapps-captcha-166x300.png" alt="Captcha chez They make apps" width="166" height="300" srcset="http://brahim.hamdouni.com/wp-uploads/theymakeapps-captcha-166x300.png 166w, http://brahim.hamdouni.com/wp-uploads/theymakeapps-captcha.png 231w" sizes="(max-width: 166px) 100vw, 166px" /></a>
  </p>
  
  <p>
    Vous voyez le truc tout en bas ?
  </p>
  
  <p>
    Au lieu de cliquer sur un vulgaire bouton pour valider le formulaire, le site vous propose tout simplement de faire glisser le curseur jusqu&#8217;à la position &#8220;SUBMIT&#8221; (soumettre). Notez la pointe d&#8217;humour des concepteurs avec leur &#8220;Hi Robot!&#8221; (bonjour robot) quand le curseur est à zéro 🙂
  </p>
  
  <p>
    Cela bloquera certainement un bon paquet de robots circulant sur la toile mais cela ne résistera pas à une attaque ciblée. En effet, simuler le glissement en javascript en forçant la position du curseur directement sur la position &#8220;SUBMIT&#8221; ne doit pas être bien sorcier.
  </p>
  
  <p>
    Mais, saluons tout de même cette élégante tentative !
  </p>

 [1]: http://fr.wikipedia.org/wiki/Captcha "Définition sur Wikipédia"
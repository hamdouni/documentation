---
title: "Comment utiliser la barre d'adresse comme champ de recherche dans Firefox ?"
author: Brahim
type: post
date: 2008-01-07T10:18:55+00:00
url: /firefox-utiliser-la-barre-dadresse-comme-champ-de-recherche/
categories:
  - Comment faire ?
tags:
  - howto

---
Quand on tapes un ou plusieurs mots dans la barre d&#8217;adresse, et que Firefox n&#8217;identifie pas une url bien formée, il va tenter une recherche sur le service Google &#8220;I&#8217;m Feeling Lucky&#8221; : en gros, il essaye de faire coincider les mots tapés avec un nom de domaine existant.

Mais il peut être plus intéressant d&#8217;effectuer une recherche classique. L&#8217;astuce ci-dessous modifie le comportement de Firefox pour pouvoir effectuer une recherche Google depuis la barre d&#8217;adresse.

( Extrait de la faq <http://www.mozilla.org/support/firefox/tips#beh_search> )

> By default, if you enter a search term in the address field and press Enter, a Google &#8220;I&#8217;m Feeling Lucky&#8221; search is performed, and you&#8217;re taken to the first result of that search directly. If you prefer to see the standard search result list instead, use [about:config][1] to change the value of the preference keyword.URL to http://www.google.com/search?btnG=Google+Search&q=
> 
> Of course, you could also change to a completely different search engine by changing the string to something else. The default search string is: &#8220;http://www.google.com/search?btnI=I%27m+Feeling+Lucky&q=&#8221;.

 [1]: http://www.mozilla.org/support/firefox/edit#aboutconfig
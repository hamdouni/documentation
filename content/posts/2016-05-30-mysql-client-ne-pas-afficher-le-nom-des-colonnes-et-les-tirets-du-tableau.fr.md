---
title: 'mysql client : ne pas afficher le nom des colonnes et les tirets du tableau'
author: Brahim
type: post
date: 2016-05-30T08:33:23+00:00
url: /mysql-client-ne-pas-afficher-le-nom-des-colonnes-et-les-tirets-du-tableau/
categories:
  - Comment faire ?

---
Le client mysql affiche les résultats sous forme d&#8217;un tableau dessiné avec des caractères ascii comme l&#8217;exemple ci-dessous, mais comment faire si on veut le résultat brut sans fioriture ?<!--more-->

<pre>+-------+
| pv_id |
+-------+
|     1 |
|     2 |
|     3 |
+-------+</pre>

Si l&#8217;on veut n&#8217;avoir que les résultats sans la décoration autour, vous pouvez utiliser l&#8217;argument -sN à l&#8217;exécution du client :

<pre>mysql -sN ...</pre>

et vous obtiendrez alors :

<pre>1
2
3
</pre>

C&#8217;est juste ce qu&#8217;il faut pour intégrer les résultats dans un script shell !
---
title: Comment diminuer les déconnexions PPTP intempestives ?
author: Brahim
type: post
date: 2007-02-09T17:01:08+00:00
url: /deconnexion-pptp/
categories:
  - Comment faire ?

---
A la mise en place de pptp sous Linux/Debian, j&#8217;ai constaté des déconnexions fréquentes, sans explications claires. Pptp test régulièrement la ligne avec les clients, et s&#8217;il constate un time-out, il coupe l&#8217;accés.
  
Il est possible d&#8217;augmenter le time-out pour diminuer les déconnexions, et plus particulièrement sur des lignes à faible débit. Pour cela, sur le serveur, visualisez le fichier de configuration de pptpd :

> cat /etc/pptpd.conf

et repérez la ligne définissant le fichier d&#8217;option. Sur ma configuration :

> ppp /usr/sbin/pppd **option /etc/ppp/pptpd-options** debug &#8230;

Editez le fichier d&#8217;options, par exemple avec vi &#8220;/etc/ppp/pptpd-options&#8221;

> lock
  
> mtu 1450
  
> mru 1450
  
> debug
  
> nobsdcomp
  
> proxyarp
  
> auth
  
> ipcp-accept-local
  
> ipcp-accept-remote
  
>  **lcp-echo-failure 10
  
> lcp-echo-interval 6
  
>** ms-dns 10.0.0.2
  
> deflate 0

**lcp-echo-failure** est le nombre de paquet en échec avant interuption. **lcp-echo-interval** est le nombre de seconde entre 2 tests. En passant ces paramètres à 10 paquets toutes les 6 secondes, j&#8217;ai fortement diminué les déconnexions dans ma configuration. Vous devez ajuster ces paramètres selon vos besoins.
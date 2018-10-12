---
title: 'Invisible code sticks forever [EN]'
author: Brahim
type: post
date: 2015-08-24T05:30:57+00:00
url: /invisible-code-sticks-forever/
wp-to-buffer-success:
  - 1
categories:
  - Fun
tags:
  - Javascript
  - web

---
A few months ago, I read [an article about brain training by learning a new language][1] : very interesting story about William Alexander who failed to learn french but strenghten his brain trying to.

But this is not the subject of this post. As I finished to read the article, I tried to reach <a href="http://williamalexander.com/" target="_blank">William Alexander&#8217;s website</a> and was redirected to a crappy chineese online store. I immediately thought he was hacked and after reading the page source code, I find this piece of script :

<pre>&lt;script type="text/javascript"&gt;
var language = navigator.browserLanguage?navigator.browserLanguage:navigator.language;
if (language.indexOf('en') &gt; -1) document.location.href = 'javascript:void(0)';
else
document.location.href = 'http://www.line-kopi.com';
&lt;/script&gt;</pre>

What&#8217;s going on here ? The code checks the browser language and redirects to the fraudulent site only if the language is anything other than english ! So, every time some non-english dude complains to William about this problem, William tries the site and accesses it successfully and just forget about it&#8230; The malicious code can stay here for months,  with just a little trick but very annoying result !

And for the record, I, of course, alerted William and he removed the malicious code &#8230;

 [1]: undefined "undefined"
---
title: Stretched background with IE8
author: Brahim
type: post
date: 2014-07-17T16:43:54+00:00
url: /stretched-background-with-ie8/
fb_author_post_id:
  - 684221404978988
categories:
  - How to ?

---
_Side note : Microsoft has dropped support for IE8 last april 2014 🙁_

There are still some clients that want their webapp to work perfectly on IE8. They can&#8217;t make all their clients move to the newest browsers. But some times, it can drive you nuts to achieve simple things. Our problem was about a background image in a div that doesn&#8217;t want to strech. Just some css will do it for all other browsers, but not for IE8. It needs a special &#8220;filter&#8221; like this :

<pre><code class="css">
.logondesktop { filter:progid:DXImageTransform.Microsoft.AlphaImageLoader( enabled=true, src='http://lorempixel.com/1200/800/', sizingMethod='scale');}
</code></pre>

_<a title="MSDN" href="http://msdn.microsoft.com/en-us/library/ms532969(v=vs.85).aspx" target="_blank">More info on this filter at Microsoft</a>_

Here we add a nice background (thanks to <a title="Nice fake image contents" href="http://lorempixel.com" target="_blank">Lorem Pixel</a>) to the &#8216;logondesktop&#8217; element. Ok, that made the trick. But, wait ?!? What happen to my links and form input inside the div ? There are no more clickable !!!

Damned IE8, another bug&#8230; Now, dig again to find a fix. Hopefully, it was easy. The div content must be relatively positioned. So the html looks like

<pre><code class="html">
&lt;div class="logondesktop"&gt;
  &lt;div class="logon"&gt;
    &lt;a href="#"&gt;CLICK ME IF YOU DARE!&lt;/a&gt;
  &lt;/div&gt;
&lt;/div&gt;
</code></pre>

And the css to fix the IE8 bug :

<pre><code class="css">
.logon { position: relative; }
</code></pre>

See an example here (open with IE8) : <a title="Example" href="http://fiddle.jshell.net/hamdouni/w4BBE/show/#" target="_blank">http://fiddle.jshell.net/hamdouni/w4BBE/show</a>
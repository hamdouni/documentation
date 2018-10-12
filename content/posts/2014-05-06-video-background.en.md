---
title: 'Video background [EN]'
author: Brahim
type: post
date: 2014-05-06T13:40:21+00:00
url: /video-background-en/
post_to_facebook_timeline:
  - 1
categories:
  - How to ?
tags:
  - background
  - css
  - css3
  - html
  - HTML5
  - video

---
> Forget large background image for your web site. Now, comes video time.

So you want to put a nice video as background of your site but don&#8217;t know how to do ? &#8220;Fear you must not&#8221; said <a title="Yoda's fear leads to anger etc... video" href="http://www.youtube.com/watch?v=kFnFr-DOPf8" target="_blank">Yoda</a> as it&#8217;s really simple.

First, have <a title="Video Background Effect" href="http://hamdouni.github.io/video-background" target="_blank">a look at the effect in action</a>. Nice, isn&#8217;t it ?

First thing first, the html :

<pre>&lt;video src="your-video.mp4"&gt;&lt;/video&gt;
&lt;div&gt; your fantastic text here &lt;/div&gt;</pre>

Now, the css magic :

<pre>video {
  z-index: -999;
  position: fixed;
  min-height: 100%;
  min-width: 100%;
}</pre>

The z-index indicates that the video layer is in the background. Everything with a higher index will appear above.

The position fixed is mandatory, to make sure the overlay plays well.

Finally, ensure that the video dimension takes all space available, with the min height and width tags to 100%.

If you would like to have your text centered horizontally and vertically, just add this css :

<pre>html, body { width: 100%; height: 100%; }
body {display:table;}
div {display: table-cell; vertical-align: middle; text-align: center;}</pre>

And that&#8217;s all !

This method works on all major browser : I tested it on Firefox, Chrome and Safari. It also works unmodified on IE9 !
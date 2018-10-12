---
title: Cheyenne server and POST size limit
author: Brahim
type: post
date: 2016-10-03T13:49:50+00:00
url: /cheyenne-server-and-post-size-limit/
categories:
  - How to ?
tags:
  - cheyenne
  - howto

---
By default, in Cheyenne, the header size limit for a post request is 102&#8217;400.
  
If you want to ajust this limit you can define the post-mem-limit parameter in the global context or in a specific webapp.
  
For example, to double the initial limit in the httpd.cfg, :

    ...
    default [
    	root-dir %./www/
    	default [%index.html %index.rsp]
    	post-mem-limit 408'800
    ]
    ...
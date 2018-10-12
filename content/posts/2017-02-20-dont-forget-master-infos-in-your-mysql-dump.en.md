---
title: Don’t forget master infos in your MySQL dump
author: Brahim
type: post
date: 2017-02-20T16:54:46+00:00
url: /dont-forget-master-infos-in-your-mysql-dump/
categories:
  - How to ?
tags:
  - dev
  - howto
  - mysql

---
<img class="size-thumbnail wp-image-1670 alignright" src="http://brahim.hamdouni.com/wp-uploads/512px-Database-mysql-replication-150x150.png" alt="" width="150" height="150" />I tried to resync a slave MySQL after it disconnected from the master. But the binary log was already deleted on master, so the only solution was to restore from the last backup. To avoid lock tables on the master and remember the binary log name and position to put them on the slave configuration, there is a tip to take care of all that : the &#8220;&#8211;master-data&#8221; option in mysqldump.<!--more-->

    
    mysldump --master-data -l -q yourbase > backup.sql
    

This will add all information needed on the slave side : just stop the slave before restoring the dump, and restart it after.

    
    mysql yourbase -e "stop slave"
    mysql yourbase < backup.sql
    mysql yourbase -e "start slave"
    mysql yourbase -e "show slave status \G"
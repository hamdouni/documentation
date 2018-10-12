---
title: MySQL export to csv
author: Brahim
type: post
date: 2016-10-12T12:32:05+00:00
url: /mysql-export-to-csv/
categories:
  - How to ?
tags:
  - dev
  - howto
  - mysql

---
To export a mysql results in CSV format, use the syntax below : 

    SELECT field1, field2, ...
    FROM table
    WHERE condition
    INTO OUTFILE '/tmp/toto.csv'
    FIELDS TERMINATED BY ';'
    ENCLOSED BY '"'
    LINES TERMINATED BY '\n' ;
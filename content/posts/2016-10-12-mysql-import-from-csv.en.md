---
title: MySQL import from csv
author: Brahim
type: post
date: 2016-10-12T12:36:56+00:00
url: /mysql-import-from-csv/
categories:
  - How to ?
tags:
  - dev
  - howto
  - mysql

---
To import a local CSV file into MySQL, use the syntax below :

    
    LOAD DATA LOW_PRIORITY LOCAL INFILE '/path/tofile.csv'
    INTO TABLE database.table
    FIELDS TERMINATED BY ';' OPTIONALLY ENCLOSED BY '"' ESCAPED BY '"' LINES TERMINATED BY '\n' IGNORE 1 LINES
    (`field1`,`field2`,...)
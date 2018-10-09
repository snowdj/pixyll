---
published: true
layout: post
category: Database
tags:
  - SAS
  - Oracle
  - Python
---
## Ways to connect to Oracle Database




/*
Usage Note 41616: Sample of LIBNAME statement and SQL Pass-Through code to connect to Oracle database using SAS/ACCESS® Interface to Oracle
*/

libname oralib oracle user=scott password=tiger path='DESKTOP-5A8MM7P:1521';


proc sql;
connect to oracle(user=scott password=tiger path='DESKTOP-5A8MM7P:1521');
create table work.baseball5 as
select * from connection to oracle
(select * from baseball2);
quit;

https://vincentarelbundock.github.io/Rdatasets/datasets.html

https://archive.ics.uci.edu/ml/datasets.html?area=&att=&format=&numAtt=&numIns=&sort=nameUp&task=&type=text&view=table

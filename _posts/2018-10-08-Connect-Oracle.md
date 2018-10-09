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




## Python

python-cx_Oracle

cx_Oracle version 7.0
cx_Oracle is a Python extension module that enables access to Oracle Database. It conforms to the Python database API 2.0 specification with a considerable number of additions and a couple of exclusions. See the homepage for a feature list.

cx_Oracle 7 has been tested with Python version 2.7, and with versions 3.5 and higher. You can use cx_Oracle with Oracle 11.2 and higher client libraries (including Oracle 18.3). Oracle's standard client-server version interoperability allows connection to both older and newer databases, for example Oracle 18.3 client libraries can connect to Oracle Database 11.2.

https://github.com/oracle/python-cx_Oracle


## SAS

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

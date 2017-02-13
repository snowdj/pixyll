---
published: true
layout: post
title: Import pnnl data into mysql
category: sql
tags:
  - sql
  - database
  - pnnl
---

## \*.Sql file loaded into mysql

I got pnnl data which has sql and csv format. In order to restore the data scheme and structure. I would like to import them into sqlite and then I can access them with R or python without mysql server. 

However, I try different sh file of mysql2sqlite3.sh, but none of them works for pnnl data. I am wondering it must be some setting issus.

I then installed mysql server and workbench. It allows me to import \*.sql, but it gave me an error. "database unkown".

I checked the \*.sql, and it includes a statement that will create the database if it does not exit.

It might be related to some permision issues.

From this post, I got it working. 

http://stackoverflow.com/questions/859313/error-importing-sql-dump-into-mysql-unknown-database-cant-create-database

http://stackoverflow.com/questions/18841654/mysql-import-database







 [MySQL Tutorial](https://www.youtube.com/watch?v=yPu6qV5byu4&t=163s).

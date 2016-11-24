---
published: true
layout: post
date: '2016-08-24 11:30:00 +0800'
summary: Using python to access sql database.
categories: sql
title: Python and SQL
tags:
  - sql
  - python
---


## Sqlalchemy

##### Engines and Connection Strings

Earlier, we used the connection string of 'sqlite:///:memory:'. In this string, sqlite is the vendor, and :memory: is the path to the file that represents memory (RAM). We can also connect to SQLite files by providing a relative or full path to the file just as we would from the shell prompt. For example, sqlite:///demographics.db would connect to a SQLite file named demographics.db in the local directory. You can learn a lot more about connection strings in the [SQLAlchemy documentation](http://docs.sqlalchemy.org/en/latest/core/engines.html#database-urls).

Now, create another engine that connects to a local SQLite file named census.sqlite and print the names of the tables it contains using the table_names() method. Note that when you just want to print the table names, you do not need to use engine.connect() after creating the engine.


Instructions
 - Import create_engine from the sqlalchemy module.
 - Create an engine for the census.sqlite file.
 - Print the output from the table_names() method on the engine.
 
 

{% highlight python %}

# Import create_engine

from sqlalchemy import create_engine

# Create an engine that connects to the census.sqlite file: engine

engine = create_engine('sqlite:///census.sqlite')

# Print table names

print(engine.table_names())

{% endhighlight  %}




##### Autoloading Tables from a Database

SQLAlchemy can be used to automatically load tables from a database using something called **reflection**. Reflection is the process of reading the database and building the metadata based on that information. It's the opposite of creating a Table by hand and is very useful for working with existing databases. To perform reflection, we need to import the Table object from the SQLAlchemy package. Then we use the _Table_ object to read our table from the engine and _autoload_ the columns. Using the Table object in this manner looks like we are using a function.

Try to reflect the _census_ table available on your _engine_ into the census variable. The metadata has already been loaded for you.

Instructions

Import the Table object from sqlalchemy.

Use the Table object with the arguments: the name of the table, metadata, whether autoload is True, and the engine to autoload from.

Print the repr of the census object.


```python
# Import Table
from sqlalchemy import Table

# Reflect census table from the engine: census
census = Table('census', metadata, autoload= True, autoload_with= engine )

# Print repr
print(repr(census) )

```





##### Viewing Table Details

With our table reflected, we can begin to learn more about the columns and structure of our table. It is important to get an understanding of our database by examining the column names. This can be done by using the _columns_ attribute and accessing the `keys()` method. For example, `census.columns.keys()` would return a list of column names on the census table.

Following this, we can use the metadata container to find out more details about the reflected table such as the columns and their types. For example, we can get the metadata of our _census_ table on the `metadata.tables` dictionary with `metadata.tables['census']`. This output should match the details from print(repr(census)) in the previous exercise.

Instructions

Reflect the census table.

Print a list of column names on the census table.

Print the repr of the census table metadata


```python
# Reflect census table from the engine: census
census = Table('census', metadata, autoload= True, autoload_with= engine )

# Print columns names
print(census.columns.keys())

# Print full table metadata
print( repr(metadata.tables['census']) )
```






```
<script.py> output:
    ['state', 'sex', 'age', 'pop2000', 'pop2008']
    Table('census', MetaData(bind=None), Column('state', VARCHAR(length=30), table=<census>), Column('sex', VARCHAR(length=1), table=<census>), Column('age', INTEGER(), table=<census>), Column('pop2000', INTEGER(), table=<census>), Column('pop2008', INTEGER(), table=<census>), schema=None)
```





## Python and spl

[Intro to Relational Databases](https://classroom.udacity.com/courses/ud197/lessons/3415228765/concepts/34221585900923)


```python
import sqlite3

conn = sqlite3.connect('emaildb.sqlite')
cur = conn.cursor()
#%%
cur.execute('''
DROP TABLE IF EXISTS Counts''')

cur.execute('''
CREATE TABLE Counts (email TEXT, count INTEGER)''')
#%%
fname = raw_input('Enter file name: ')
if ( len(fname) < 1 ) : fname = 'mbox-short.txt'
fh = open(fname)
for line in fh:
    if not line.startswith('From: ') : continue
    pieces = line.split()
    email = pieces[1]
    print( email)
    cur.execute('SELECT count FROM Counts WHERE email = ? ', (email, ))
    row = cur.fetchone()
    if row is None:
        cur.execute('''INSERT INTO Counts (email, count) 
                VALUES ( ?, 1 )''', ( email, ) )
    else : 
        cur.execute('UPDATE Counts SET count=count+1 WHERE email = ?', 
            (email, ))
    # This statement commits outstanding changes to disk each 
    # time through the loop - the program can be made faster 
    # by moving the commit so it runs only after the loop completes
    conn.commit()
#%%
    
    
cur.execute('''
DROP TABLE IF EXISTS Counts''')

cur.execute('''
CREATE TABLE Counts (org TEXT, count INTEGER)''')
 

fname = 'mbox.txt'
fh = open(fname)
   
#%%

for line in fh:
    if not line.startswith('From: ') : continue
    pieces = line.split()
    email = pieces[1]
    print( email)
    mail = email.split("@")
    org = mail[1]
    cur.execute('SELECT count FROM Counts WHERE org = ? ', (org, ))
    row = cur.fetchone()
    if row is None:
        cur.execute('''INSERT INTO Counts (org, count) 
                VALUES ( ?, 1 )''', ( org, ) )
    else : 
        cur.execute('UPDATE Counts SET count=count+1 WHERE org = ?', 
            (org, ))
  

    
    
    
conn.commit()   
#%%    
# https://www.sqlite.org/lang_select.html
sqlstr = 'SELECT org, count FROM Counts ORDER BY count DESC LIMIT 70'

print
print ("Counts:")
for row in cur.execute(sqlstr) :
    print( str(row[0]), row[1])


#cur.execute('''
#SELECT org, count FROM Counts ORDER BY org DESC LIMIT 30''')

#%%
conn.commit()  
cur.close()
```



### Selecting data from a Table: raw SQL
100xp
Using what we just learned about SQL and applying the execute() method on our connection, we can leverage a raw SQL query to query all the records in our census table. Then we use the fetchall() method on execute() to get our results.

In this exercise, you will use a traditional SQL query. In the next exercise, you will move to SQLAlchemy and begin to understand its advantages.


**Instructions**
Build a SQL statement to query all the columns from census and store it in stmt.
Use the execute() and fetchall() methods on our connection and store the result in results. Remember that execute() comes before fetchall().
Print results.


```python
# Build select statement for census table: stmt
stmt = 'select * from census'

# Execute the statement and print the results
results = print(connection.execute(stmt).fetchall())

# Print Results
print(results)


```


###Selecting data from a Table with SQLAlchemy

You might have noticed in the previous exercise that SQLAlchemy provides a nice abstraction from the complexities that can occur when using traditional SQL. It also provides a nice "Pythonic" way of interacting with databases. This is one of the key benefits of using SQLAlchemy over traditional SQL: Rather than dealing with the differences between specific dialects of traditional SQL such as MySQL or PostgreSQL, we can leverage the Pythonic framework of SQLAlchemy to streamline our workflow and more efficiently query our data. For this reason, it is worth learning SQLAlchemy even if you may be familiar with traditional SQL.

Let's write another select statement; however, this time using the select() statement from the sqlalchemy module to get all the records from our census table. The SQLAlchemy select() statements expects a list of tables or columns as the only required argument.

Table and MetaData have already been imported.

**Instructions**
Import select from the sqlalchemy module.
Reflect the census table using the Table() object and the metadata.
Create a query using the select() statement to retrieve the census table.
Print stmt to see the actual SQL query being created.
Print all the records from the census table using the execute() method on the connection and use fetchall() to get the results.


```python
from sqlalchemy import Table, MetaData
# Import select
from sqlalchemy  import select
metadata = MetaData()
# Reflect census table via engine: census
census = Table('census', metadata, autoload = True, autoload_with = engine)

# Build select statement for census table: stmt
stmt = select([census])

# Print the emitted statement to see the SQL emitted
print(stmt)

# Execute the statement and print the results
print(connection.execute(stmt).fetchall())
```


### Handling a ResultSet

Recall the differences between a ResultProxy and a ResultSet:

ResultProxy: The object returned by the execute() method. It can be used in a variety of ways to get the data returned by the query.
ResultSet: The actual data asked for in the query when using a fetch method such as fetchall() on a ResultProxy.
This separation between the ResultSet and ResultProxy allows us to fetch as much or as little data as we desire.

A query returns a ResultSet when a fetch method such as fetchall() is called on an executed query, and we can use Python to access all the data within it by column name and by list style indexes. For example, you can get the first row of the results by using results[0]. With that first row, you can then get data from the first column by either using first_row[0] or by column name such as first_row['column_name'].

**Instructions**
Using the ResultProxy results, save the first row as first_row and print it.
Print the value of the first column in first_row.
Print the value of the state column in first_row.

```python
# Get the first row of the results by using an index: first_row
first_row = results[0]

# Print the first row of the results
print(first_row)

# Print the first column of the row by using an index
print(first_row[0])

# Print the state column of the row by using its name
print(first_row['state'])

```



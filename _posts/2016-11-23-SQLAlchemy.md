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

<script.py> output:
    ['state', 'sex', 'age', 'pop2000', 'pop2008']
    Table('census', MetaData(bind=None), Column('state', VARCHAR(length=30), table=<census>), Column('sex', VARCHAR(length=1), table=<census>), Column('age', INTEGER(), table=<census>), Column('pop2000', INTEGER(), table=<census>), Column('pop2008', INTEGER(), table=<census>), schema=None)






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

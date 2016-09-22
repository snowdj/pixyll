---
published: false
layout: post
---
## Python: import data


[datacamp](https://campus.datacamp.com/courses/importing-data-in-python-part-1/introduction-and-flat-files-1?ex=5)


## Importing text files line by line

For large files, we may not want to print all of their content to the shell: you may wish to print only the first few lines. Enter the readline() method, which allows you to do this. When a file called file is open, you can print out the first line by executing file.readline(). If you execute the same command again, the second line will print, and so on.

In the introductory video, Hugo also introduced the concept of a context manager. He showed that you can bind a variable file by using a context manager construct:

> with open('huck_finn.txt') as file:

While still within this construct, the variable file will be bound to open('huck_finn.txt'); thus, to print the file to the shell, all the code you need to execute is:

> with open('huck_finn.txt') as file:
> 	print(file.read())




- Flat files consist of rows and each row is called a record. 
- A record in a flat file is composed of fields or attributes, each - of which contains at most one item of information. 
Flat files are pervasive in data science. 

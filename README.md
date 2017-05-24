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
[like]:[#like]
[limit]:[#limit]
[not-between]:[#not-between]
[order]:[#order-by]
[select]:[#select]
[where]:[#where]






## Querying

###  AS
```
SELECT firstName AS name FROM tablename
```
### GROUP BY
```

```
### LIKE
```
SELECT * FROM <insert table name> WHERE  first_name LIKE "B%"
```

### LIMIT
```
SELECT * FROM tablename LIMIT startNumber, endNumber
```

### NOT BETWEEN
```
SELECT * FROM <insert table name> WHERE (number NOT BETWEEN 1 and 20)
```

### ORDER BY
```
SELECT * FROM  <insert table name> ORDER by <insert property name>
```

### SELECT
```
SELECT <insert column name> FROM <insert table name>
```

### WHERE
```
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

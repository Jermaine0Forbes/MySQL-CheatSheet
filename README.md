# SQL-Reminder
I have a terrible memory so this is a cheat sheet


- [ADD][add]
- ALTER TABLES
- [AS][as]
- [AVG][avg]
- [CONCAT()][concat]
- CONCAT_WS()
- CREATE DATABASE
- CREATE TABLE
- [DATE][date]
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
- [SUM][sum]
- TRUNCATE
- UPDATE tablename SET column = value
- [WHERE][where]

[add]:#add
[as]:#as
[avg]:#avg
[concat]:#concat
[date]:#date
[group]:#group_by
[like]:#like
[limit]:#limit
[not-between]:#not-between
[order]:#order-by
[select]:#select
[sum]:#sum
[where]:#where

#### Table: pokemon
```sql
+----+------------+---------+------+--------+---------+------------+
| id | name       | type    | hp   | attack | defense | trainer_id |
+----+------------+---------+------+--------+---------+------------+
|  1 | ghastly    | ghost   |   85 |     35 |      15 |          1 |
|  2 | bulbasaur  | grass   |  110 |     65 |      85 |          2 |
|  3 | weedle     | bug     |   75 |     87 |      35 |          3 |
|  4 | abra       | psychic |   85 |     45 |      90 |          4 |
|  5 | charmander | fire    |  100 |    130 |      56 |          4 |
+----+------------+---------+------+--------+---------+------------+

```

#### Table: trainer
```sql
+----+-------------------+------+
| id | name              | age  |
+----+-------------------+------+
|  1 | Ash Ketchup       |   14 |
|  2 | Gary              |   16 |
|  3 | Waldo             |   37 |
|  4 | George  Jefferson |   63 |
+----+-------------------+------+

```



## Querying

### ADD
```sql
	alter table <insert table name >  add age int(3) default "18"
```
Exp: adds a new column called age that can hold a maximum of three digits
and the default value will be 18
- ALTER TABLES

###  AS
Rename a column name as something else
```sql
select firstName as name from tablename
```
### AVG()
- Returns the average number based on the column rows
- http://bit.ly/2r2FDqO
```sql
	select <insert table name >  add age int(3) default "18"
```

### CREATE DATABASE
```sql
```

### CREATE TABLE
```sql
```

### CONCAT()
```sql
```

### CONCAT_WS()
```sql
```

### DATE()

- The typical date format is this (2017-5-28 07:58:30) what the date functions does
		is it grabs just the date alone. So this function is only useful if you have a datetime
		value and you want to convert it to just a date

-http://bit.ly/2qqpOLU

```sql
select date(2017-5-28 07:58:30) 
```

### DELETE FROM tablename
```sql
```
### DESCRIBE
```sql
```
### DROP DATABASE
```sql
```

### DROP TABLES
```sql
```

### exit
- exits out the mysql cli

### EXPLAIN
```sql
```

### FORMAT()


### INSERT INTO (column) VALUES(value)
```sql
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

### MD5()
```sql
```

### NOT BETWEEN
-  This expression returns values where the property number does not have 1-20.
        The number property is a made up example, it can be data property that has numbers
        enabled like for example weight, or income. Whatever data property that is a
        number can use the NOT BETWEEN
```sql
SELECT * FROM <insert table name> WHERE (number NOT BETWEEN 1 and 20)
```

### NOW()
```sql
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

### RAND()
```sql
```

### REPLACE INTO
```sql
```
### SHA1()


### SELECT

```sql
SELECT <insert column name> FROM <insert table name>
```
Exp: displays all the values by the specific column name that you requested

```sql
SELECT <insert column name> FROM <insert table name>
```
Exp: displays all the columns for the table name

### SHOW DATABASES
```sql
```

### SHOW TABLES
```sql
```

### SHOW COLUMNNS FROM
```sql
```

### SHOW WARNINGS
```sql
```

### SUM()
- You should know what this function does
```sql
 select 
```

### TRUNCATE
```sql
```

### UPDATE 
```sql
SELECT tablename SET column = value
```

### WHERE

```sql
SELECT <insert column name> FROM <insert table name> WHERE <insert conditions>
```










































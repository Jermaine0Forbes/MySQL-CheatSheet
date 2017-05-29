# SQL-Reminder
I have a terrible memory so this is a cheat sheet


- [ADD][add]
- ALTER TABLES
- [AS][as]
- [AVG][avg]
- [CASE()][case]
- [CHANGE COLUMN][chCo]
- [COALESCE()][coal]
- [CONCAT()][concat]
- CONCAT_WS()
- [COUNT()][count]
- CREATE DATABASE
- CREATE TABLE
- [DATE()][date]
- DELETE from tablename  
- DESCRIBE
- DROP DATABASE
- DROP TABLES
- [ELSE()][else]
- [ENUM][enum]
- exit
- [EXPLAIN][exp]
- FORMAT()
- [GREATEST()][great]
- [GROUP BY][group]
- [IF][if]
- [IFNULL()][inull]
- [INDEX][index]
- INSERT INTO (column) VALUES(value)
- [MAX()][max]
- MD5()
- [NOT BETWEEN][not-between]
- NOW()
- [LEAST()][least]
- [LIKE][like]
- [LIMIT][limit]
- [ORDER BY][order]
- RAND()
- [RENAME TO][renam]
- REPLACE INTO
- [SELECT][select] 
- [SET][set] 
- SHA1()
- SHOW COLUMNNS from
- SHOW DATABASES
- SHOW TABLES
- [SHOW TABLE STATUS][sts]
- SHOW WARNINGS
- [SUM()][sum]
- TRUNCATE
- [UNIX_TIMESTAMP][unix]
- UPDATE tablename SET column = value
- [WHERE][where]

[add]:#add
[as]:#as
[avg]:#avg
[case]:#case
[chCo]:#change-column
[coal]:#coalesce
[concat]:#concat
[count]:#count
[date]:#date
[else]:#else
[enum]:#enum
[exp]:#explain
[great]:#greatest
[group]:#group_by
[if]:#if
[inull]:#ifnull
[index]:#index
[least]:#least
[like]:#like
[limit]:#limit
[max]:#max
[not-between]:#not-between
[order]:#order-by
[renam]:#rename-to
[select]:#select
[set]:#set
[sts]:#show-table-status
[sum]:#sum
[unix]:#unix-timestamp
[where]:#where

#### Table: pokemon
```sql
+----+------------+---------+------+--------+---------+------------+
| id | name       | type    | hp   | attack | defense | trainer_id |
+----+------------+---------+------+--------+---------+------------+
|  1 |  ghastly   | ghost   |   85 |     35 |      15 |          1 |
|  2 | bulbasaur  | grass   |  110 |     65 |      85 |          2 |
|  3 | weedle     | bug     |   75 |     87 |      35 |          3 |
|  4 | abra       | psychic |   85 |     45 |      90 |          4 |
|  5 | charmander | fire    |  100 |    130 |      56 |          4 |
|  6 | psyduck    | water   |   90 |     75 |      66 |          3 |
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
alter table pokemon  add speed int(3) default "18";
```
Exp: adds a new column called age that can hold a maximum of three digits
and the default value will be 18
- ALTER TABLES

###  AS
Rename a column name as something else
```sql
select name as pokemon from pokemon
```
### AVG()
- Returns the average number based on the column rows
- http://bit.ly/2r2FDqO
```sql
select <insert table name >  add age int(3) default "18"
```
### CASE
```sql
```

### CHANGE COLUMN
```sql
```

### CREATE DATABASE
```sql
```

### CREATE TABLE
```sql
```

### COALESCE
```sql
```

### CONCAT()
```sql
```

### CONCAT_WS()
```sql
```

### COUNT
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

### DELETE from tablename
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


### ELSE
```sql
```

### ENUM 
- Creates an array of values that can only be used in a specific column
- https://blog.udemy.com/mysql-enum/
```sql
```

### EXPLAIN
- Show the data types of columns
```sql
explain trainer;
```

### FORMAT()
```sql
```

### IF()
```sql
```

### IFNULL()
```sql
```

### INDEX
- Makes querying a lot easier because sql will look for the index value first.
	It is also essential to index a record/value  if you a creating foreign keys

### INSERT INTO (column) VALUES(value)
- Adds rows/data into table
```sql
insert into pokemon (name, type, hp, attack, defense, trainer_id) values ("psyduck", "water", 90, 75, 66, 3);
```

### GREATEST()
```sql

```

### GROUP BY
```sql

```

### HAVING
```sql

```

### LEAST()
```sql

```


### LIKE
- This expression searches for data rows where the property first name starts
with a capital B. And returns all the rows that have that
```sql
select * from trainer where  name like "A%"
```

### LIMIT
- Limits the number of documents that you receive from the query
- You can have a start and end number or you can one number that will output then number of documents
```sql
select * from tablename limit startNumber, endNumber
```
Exp: This selects from tablename that will receive rows from the startNumber to the endNumber

### MAX()
```sql
```

### MD5()
```sql
```

### NOT BETWEEN
-  This expression returns values where the property number does not have 1-20.
        The number property is a made up example, it can be data property that has numbers
        enabled like for example weight, or income. Whatever data property that is a
        number can use the NOT BETWEEN
```sql
select * from <insert table name> where (number not between 1 and 20)
```

### NOW()
```sql
```

### ORDER BY
 -  this expression will order the rows of data based on the property name
        if the property is a number it will go from 0 - infinity. And if it is a
        string it will go from a-z.
```sql
select * from  trainer order by name
```

```sql
select * from  trainer order by age DESC/ASC
```
Exp: orders the rows from ACS = alphabetic or numeric order, or DESC the reverse

### RAND()
```sql
```

### RENAME TO()
```sql
```

### REPLACE INTO
```sql
```

### SHA1()
```sql
```

### SELECT

```sql
select name , age  from trainer
```
Exp: displays all the values by the specific column name that you requested

```sql
select * from pokemon
```
Exp: displays all the columns for the table name

### SET
- Similar to enum but you can have multiple values into one row

### SHOW DATABASES
```sql
```

### SHOW TABLES
```sql
```

### SHOW COLUMNNS from
```sql
```

### SHOW TABLE STATUS
```sql
```

### SHOW WARNINGS
```sql
```

### SUM()
- You should know what this function does
```sql
select sum(attack) as all_pokemon_attack_power from pokemon;
```

### TRUNCATE
```sql
```

### UNIX_TIMESTAMP
```sql
```

### UPDATE 
```sql
update pokemon set name = "magmar" where id = 5;
```

### WHERE

```sql
select hp , attack , defense from pokemon where name = "abra";
```


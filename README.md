# Table of Contents
I have a terrible memory so this is a cheat sheet


- [ADD][add]
- [ALTER TABLE][alter]
- [AS][as]
- [AVG][avg]
- [CASE()][case]
- [CHANGE][change]
- [COALESCE()][coal]
- [CONCAT()][concat]
- CONCAT_WS()
- [COUNT()][count]
- [CREATE DATABASE][creD]
- [CREATE TABLE][creT]
- [DATE()][date]
- DELETE from tablename  
- DESCRIBE
- DROP DATABASE
- DROP TABLES
- DROP column
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
[alter]:#alter-table
[as]:#as
[avg]:#avg
[case]:#case
[change]:#change
[creD]:#create-database
[creT]:#create-table
[coal]:#coalesce
[concat]:#concat
[count]:#count
[date]:#date
[else]:#else
[enum]:#enum
[exp]:#explain
[great]:#greatest
[group]:#group_by
[home]:#table-of-contents
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
+----+------------+---------+-----+--------+---------+-------+------------+
| id | name       | type    | hp  | attack | defense | speed | trainer_id |
+----+------------+---------+-----+--------+---------+-------+------------+
|  1 | ghastly    | ghost   |  30 |     35 |      30 |    80 |          1 |
|  2 | bulbasaur  | grass   | 110 |     65 |      85 |    27 |          2 |
|  3 | weedle     | bug     |  75 |     87 |      35 |    50 |          3 |
|  4 | abra       | psychic |  85 |     45 |      90 |    60 |          4 |
|  5 | charmander | fire    | 100 |    130 |      56 |    46 |          1 |
|  6 | psyduck    | water   |  90 |     75 |      66 |    33 |          3 |
|  7 | ekans      | poison  |  35 |     60 |      44 |    55 |          4 |
|  8 | geodude    | rock    |  40 |     80 |     100 |    20 |          5 |
|  9 | staryu     | water   |  30 |     45 |      55 |    85 |          3 |
| 10 | dragonair  | dragon  |  61 |     84 |      65 |    70 |          2 |
+----+------------+---------+-----+--------+---------+-------+------------+

```

#### Table: trainers

```sql
+----+------------+-----------+-----+-----+---------------------+
| id | first_name | last_name | age | sex | trainer_registered  |
+----+------------+-----------+-----+-----+---------------------+
|  1 | Ash        | Ketchup   |  14 | m   | 2017-07-02 22:07:46 |
|  2 | Gary       | Mustard   |  16 | m   | 2017-07-02 22:08:43 |
|  3 | Misty      | Stone     |  15 | f   | 2017-07-02 22:10:15 |
|  4 | Jessie     | Magenta   |  27 | f   | 2017-07-02 22:10:15 |
|  5 | Brock      | Therock   |  24 | m   | 2017-07-04 15:14:39 |
+----+------------+-----------+-----+-----+---------------------+

```
#### Table: records

```sql
+----+------------+--------+-------------+-------------------------+
| id | trainer_id | status | opponent_id | description             |
+----+------------+--------+-------------+-------------------------+
|  1 |          1 | win    |           4 | Ash whooped that ass... |
|  2 |          5 | Loss   |           2 | Dragonair dominated ... |
|  3 |          4 | Win    |           3 | Jessie surmounted mi... |
+----+------------+--------+-------------+-------------------------+

```
#### Table: journal

```sql
+----+------------+------------------------------------+-------------------------+---------------------+
| id | trainer_id | title                              | body                    | date                |
+----+------------+------------------------------------+-------------------------+---------------------+
|  1 |          1 | I'm going to be the greatest       | Man, I'm going to be... | 2017-07-04 15:58:53 |
|  2 |          2 | Ash is such a  boob                | Ash, my evil rival e... | 2017-07-04 15:58:53 |
|  3 |          3 | I will not be defined by my gender | I will not let any m... | 2017-07-04 15:58:53 |
|  4 |          4 | I'm so tired                       | I'm so tired of chas... | 2017-07-04 15:58:53 |
|  5 |          5 | Shh! don't tell nobody             | I am secretly gay!! ... | 2017-07-04 15:58:53 |
+----+------------+------------------------------------+-------------------------+---------------------+
'

```


## Querying

### ADD
```sql
alter table pokemon  add speed int(3) default "18";
```
Explanation: adds a new column called age that can hold a maximum of three digits
and the default value will be 18

[go back to table of contents][home]


### ALTER TABLE

```sql
alter table trainers  drop age , drop sex ;
```
Explanation: drops the columns age and sex from trainers

[go back to table of contents][home]

###  AS
Rename a column name as something else
```sql
select name as pokemon from pokemon
```
[go back to table of contents][home]

### AVG()
- Returns the average number based on the column rows
- http://bit.ly/2r2FDqO
```sql
select avg(age) as average_age from trainer
```
Explanation: Averages the number of a column

[go back to table of contents][home]


### CASE
- Essentially it is the switch statement for mysql
```sql
 select name , age, (case when age > 20 then 1 else 0 end ) as boolean from trainer;
```
Explanation: shows three columns (name, age, boolean), and boolean will return 1 if age > 20
, or it will be 0 if the age is lesser than 20

[go back to table of contents][home]


### CHANGE

```sql
alter table journal change date date default date;
```
Explanation: Changes the date column datatype to date

[go back to table of contents][home]


### CREATE DATABASE
```sql
 create database Pokemon
```
Explanation: creates a new database called Pokemon

[go back to table of contents][home]

### CREATE TABLE
```sql
 create table journal (
 id int not null auto_increment unsigned,
 primary key (id),
 trainer_id int unsigned,
 index(trainer_id),
 status varchar(5),
 opponent_Id int unsigned,
 index(opponent_id),
 description text
 );
```
Explanation: creates a new table and you can specifiy what columns you want in the table

[go back to table of contents][home]

### COALESCE
```sql
```
Explanation:

[go back to table of contents][home]

### CONCAT()
```sql
```
Explanation:

[go back to table of contents][home]

### CONCAT_WS()
```sql
```
Explanation:

[go back to table of contents][home]

### COUNT
```sql
```
Explanation:

[go back to table of contents][home]

### DATE()

- The typical date format is this (2017-5-28 07:58:30) what the date functions does
		is it grabs just the date alone. So this function is only useful if you have a datetime
		value and you want to convert it to just a date

- http://bit.ly/2qqpOLU

```sql
select date(2017-5-28 07:58:30) as current_date
```
Explanation:

[go back to table of contents][home]

### DELETE from tablename
```sql

```
Explanation:

[go back to table of contents][home]

### DESCRIBE
```sql

```
Explanation:

[go back to table of contents][home]

### DROP DATABASE
```sql

```
Explanation:

[go back to table of contents][home]

### DROP TABLES
```sql

```
Explanation:

[go back to table of contents][home]

### exit
- exits out the mysql cli

Explanation:

[go back to table of contents][home]

### ELSE
```sql

```
Explanation:

[go back to table of contents][home]

### ENUM
- Creates an array of values that can only be used in a specific column
- https://blog.udemy.com/mysql-enum/
```sql
```
Explanation:

[go back to table of contents][home]

### EXPLAIN
- Show the data types of columns
```sql
explain trainers;
```
Explanation:

[go back to table of contents][home]

### FORMAT()
```sql

```
Explanation:

[go back to table of contents][home]

### IF()
```sql

```
Explanation:

[go back to table of contents][home]

### IFNULL()
```sql

```
Explanation:

[go back to table of contents][home]

### INDEX
- Makes querying a lot easier because sql will look for the index value first.
	It is also essential to index a record/value  if you a creating foreign keys
```sql
create table pokemon (
id int not null unsigned auto_increment,
name varchar(40),
type varchar(20),
attack int(3),
defense int(3),
trainer_id int unsigned,
index(trainer_id)
)
```

### INSERT INTO (column) VALUES(value)
- Adds rows/data into table
```sql
insert into pokemon (name, type, hp, attack, defense, trainer_id) values ("psyduck", "water", 90, 75, 66, 3);
```
Explanation:

[go back to table of contents][home]

### GREATEST()
```sql

```
Explanation:

[go back to table of contents][home]

### GROUP BY
```sql

```
Explanation:

[go back to table of contents][home]

### HAVING
```sql

```
Explanation:

[go back to table of contents][home]

### LEAST()
```sql

```
Explanation:

[go back to table of contents][home]


### LIKE
- This expression searches for data rows where the property first name starts
with a capital B. And returns all the rows that have that
```sql
select * from trainer where  name like "A%"
```
Explanation:

[go back to table of contents][home]

### LIMIT
- Limits the number of documents that you receive from the query
- You can have a start and end number or you can one number that will output then number of documents
```sql
select * from tablename limit startNumber, endNumber
```
Explanation: This selects from tablename that will receive rows from the startNumber to the endNumber

[go back to table of contents][home]

### MAX()
```sql

```
Explanation:

[go back to table of contents][home]

### MD5()
```sql

```
Explanation:

[go back to table of contents][home]

### NOT BETWEEN
-  This expression returns values where the property number does not have 1-20.
        The number property is a made up example, it can be data property that has numbers
        enabled like for example weight, or income. Whatever data property that is a
        number can use the NOT BETWEEN
```sql
select * from pokemon where (attack not between 30 and 70)
```
Explanation:

[go back to table of contents][home]

### NOW()
- Gives you the current time in datetime format. Example: (2017-5-29 09:16:12)
```sql
insert into
```
Explanation:

[go back to table of contents][home]

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
Explanation: orders the rows from ACS = alphabetic or numeric order, or DESC the reverse

[go back to table of contents][home]


### RAND()
```sql

```
Explanation:

[go back to table of contents][home]

### RENAME TO()
```sql

```
Explanation:

[go back to table of contents][home]

### REPLACE INTO
```sql

```
Explanation:

[go back to table of contents][home]

### SHA1()
```sql

```
Explanation:

[go back to table of contents][home]

### SELECT

```sql
select name , age  from trainer
```
Explanation: displays all the values by the specific column name that you requested

```sql
select * from pokemon
```
Explanation: displays all the columns for the table name

[go back to table of contents][home]

### SET
- Similar to enum but you can have multiple values into one row

```sql

```
Explanation:

[go back to table of contents][home]

### SHOW DATABASES
```sql

```
Explanation:

[go back to table of contents][home]

### SHOW TABLES
```sql

```
Explanation:

[go back to table of contents][home]

### SHOW COLUMNS from
```sql

```
Explanation:

[go back to table of contents][home]

### SHOW TABLE STATUS
```sql

```
Explanation:

[go back to table of contents][home]

### SHOW WARNINGS
- well ... it shows warning messages
```sql
```

### SUM()
- You should know what this function does
```sql
select sum(attack) as all_pokemon_attack_power from pokemon;
```
Explanation:

[go back to table of contents][home]


### TRUNCATE
```sql

```
Explanation:

[go back to table of contents][home]

### UNIX_TIMESTAMP
```sql

```
Explanation:

[go back to table of contents][home]

### UPDATE
- Updates a certain value in a column
```sql
update pokemon set name = "magmar" where id = 5;
```

### WHERE
- Specifies what particular column will be effected
```sql
select hp , attack , defense from pokemon where name = "abra";
```

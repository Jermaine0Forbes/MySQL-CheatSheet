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
- [CONCAT_WS()][concat-ws]
- [COUNT()][count]
- [CREATE][create]
- [DATE()][date]
- [DELETE][delete]
- [DESCRIBE][describe]
- [DROP][drop]
- [ELSE()][else]
- [ENUM][enum]
- [exit][exit]
- [EXPLAIN][exp]
- [FORMAT()][format]
- [GREATEST()][great]
- [GROUP BY][group]
- [HAVING][have]
- [IF][if]
- [IFNULL()][inull]
- [INDEX][index]
- [INSERT][insert]
- [MAX()][max]
- [MD5()][md5]
- [NOT BETWEEN][not-between]
- [NOW()][now]
- [LEAST()][least]
- [LIKE][like]
- [LIMIT][limit]
- [ORDER BY][order]
- [RAND()][rand]
- [RENAME TO][renam]
- [REPLACE INTO][replace]
- [SELECT][select]
- [SET][set]
- [SHA1()][sha]
- [SHOW][show]
- [SUM()][sum]
- [TRUNCATE][trunc]
- [UNIX_TIMESTAMP][unix]
- [UPDATE][update]
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
[concat-ws]:#concat_ws
[count]:#count
[create]:#create
[date]:#date
[delete]:#delete
[describe]:#describe
[drop]:#drop
[else]:#else
[enum]:#enum
[exit]:#exit
[exp]:#explain
[format]:#format
[great]:#greatest
[group]:#group_by
[have]:#having
[home]:#table-of-contents
[if]:#if
[inull]:#ifnull
[index]:#index
[insert]:#insert
[least]:#least
[like]:#like
[limit]:#limit
[max]:#max
[md5]:#md5
[now]:#now
[not-between]:#not-between
[order]:#order-by
[rand]:#rand
[renam]:#rename-to
[replace]:#replace-into
[select]:#select
[set]:#set
[sha]:#sha1
[show]:#show
[sum]:#sum
[trunc]:#truncate
[unix]:#unix-timestamp
[update]:#update
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
 alter table trainers change sex sex varchar(6);

```
Explanation: changes the column sex to contain 6 characters instead
of the original data type only holding 1 character

[go back to table of contents][home]


### CREATE

#### CREATE TABLE
```sql
 create table records (
 	id int unsigned auto_increment not null,
 	primary key (id),
 	trainer_id int unsigned,
 	index(trainer_id),
 	status varchar(5),
 	opponent_id int unsigned,
 	index(opponent_id),
 	description text
 );
```
Explanation: Creates a table called records and adds in
the columns

#### CREATE DATABASE
```sql

 create database Pokemon;
```
Explanation: creates a database called Pokemon

[go back to table of contents][home]


### COALESCE
- coalesce can take in multiple columns within the function and
it goes down each row until one of the column has a null value.
Once it a row has a null value it will switch to the next column until
a row has a null value.
```sql
 +----+--------------+------+------+--------+
| id | name         | age  | sex  | weight |
+----+--------------+------+------+--------+
|  1 | jacob ruler  |   24 | m    |   NULL |
|  3 | jane fonda   |   37 | NULL |    142 |
|  4 | nick gordon  | NULL | m    |    194 |
|  5 | yulia swartz |   22 | f    |    126 |
+----+--------------+------+------+--------+

 select name , coalesce(age,sex) as result from user;

 +--------------+--------+
| name         | result |
+--------------+--------+
| jacob ruler  | 24     |
| jane fonda   | 37     |
| nick gordon  | m      |
| yulia swartz | 22     |
+--------------+--------+

```
Explanation: I had to make up a table to show how it works. So there is a
table called user that has name, age, sex, and weight. Some of these rows have
null, so when you coalesce age and sex from user it will first look for ages
and if a row has null value for age it will switch to sex.

[go back to table of contents][home]

### CONCAT()
```sql
 select concat(first_name, " ", last_name) as name from trainers;

 +----------------+
| name           |
+----------------+
| Ash Ketchup    |
| Gary Mustard   |
| Misty Stone    |
| Jessie Magenta |
| Brock Therock  |
+----------------+

```
Explanation: Combines columns together to create a new field. For example,
the first name , the last name, and whitespace " ". Created the name field.

[go back to table of contents][home]

### CONCAT_WS()
```sql
   select concat_ws('--', first_name, last_name,sex) as title from trainers;

+--------------------+
| title              |
+--------------------+
| Ash--Ketchup--m    |
| Gary--Mustard--m   |
| Misty--Stone--f    |
| Jessie--Magenta--f |
| Brock--Therock--m  |
+--------------------+


```
Explanation: The first parameter is the string that you are going to use to seperate
the column values from each other. In this example, I just used "--"

[go back to table of contents][home]

### COUNT
```sql
	select count(name) as all_the_pokemon from pokemon;
```
Explanation: Counts all the rows from a specific column;

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

### DELETE
- deletes a row from a table

```sql
 delete from pokemon where name = "mewto";

```
Explanation: deletes any row from pokemon where the name
equals mewto

[go back to table of contents][home]

### DESCRIBE
- shows the schema structure of a table;
```sql
 describe records;
 +-------------+------------------+------+-----+---------+----------------+
| Field       | Type             | Null | Key | Default | Extra          |
+-------------+------------------+------+-----+---------+----------------+
| id          | int(10) unsigned | NO   | PRI | NULL    | auto_increment |
| trainer_id  | int(10) unsigned | NO   | MUL | NULL    |                |
| status      | varchar(5)       | NO   |     | NULL    |                |
| opponent_id | int(10) unsigned | NO   | MUL | NULL    |                |
| description | text             | NO   |     | NULL    |                |
+-------------+------------------+------+-----+---------+----------------+

```
Explanation: its not rocket science, you will get this

[go back to table of contents][home]

### DROP

#### DROP DATABASE
- self explanatory
```sql
	drop database Pokemon;
```
Explanation: not rocket science

#### DROP TABLES
- self explanatory
```sql
	drop table journal;
```
Explanation: simple


#### DROP COLUMN

- self explanatory
```sql
 alter table trainers drop column sex
```
Explanation: removes column sex from the trainers table;

[go back to table of contents][home]


### ELSE
- the last option for the if or case function.
Apparently you can create functions in mysql so I have to wait
until I start learning how to do that

```sql

 select first_name as name , (if sex= "m" then "male" else "female") as sex from trainers;

```
Explanation: if the sex of the trainer is m then insert the string male,
else put the string female

[go back to table of contents][home]

### ENUM
- Creates an array of values that can only be used in a specific column
- https://blog.udemy.com/mysql-enum/
- You can insert the value of the enum by the positions number
```sql

  alter table trainers add race enum ('white', 'black', 'asian', 'mixed') default 'asian';

```
Explanation: Adds a new column to the table called race and it can only have
4 different values inserted into it. You can also insert the value by number.
For example: if you wanted to insert white you will be put the number 1

[go back to table of contents][home]


### exit
- exits out the mysql cli

Explanation: self explanatory

[go back to table of contents][home]

### EXPLAIN
- Show the data types of columns
```sql
  explain trainers;
```
Explanation: If this is not similar, then this exactly like the describe command
you essentially see the schema structure of the table

[go back to table of contents][home]

### FORMAT()
- determines how many decimal places will be presented in the value and also rounds
the value
```sql
    +----+-----------+-----------+-------+
    | id | weight_kg | height_km | name  |
    +----+-----------+-----------+-------+
    |  1 |   5.44311 |   0.00046 | fido  |
    |  2 |  10.88620 |   0.00091 | tiger |
    |  3 |  16.32930 |   0.00167 | alex  |
    +----+-----------+-----------+-------+

    select name , format(weight_kg, 3) as kilogram from dog;

    +-------+----------+
    | name  | kilogram |
    +-------+----------+
    | fido  | 5.443    |
    | tiger | 10.886   |
    | alex  | 16.329   |
    +-------+----------+

```
Explanation: I created a table called dog where the columns have the name of the dog,
the weight in kilograms, and the height in kilometers. With the format function, it only
shows 3 decimal places of the weight of the dogs

[go back to table of contents][home]

### IF()
- the if function has 3 parameters if( expression, true, false)
```sql
    select  name , hp , if(attack < 50, 'too weak', attack) as attack from pokemon limit 5;

    +------------+-----+----------+
    | name       | hp  | attack   |
    +------------+-----+----------+
    | ghastly    |  30 | too weak |
    | bulbasaur  | 110 | 65       |
    | weedle     |  75 | 87       |
    | abra       |  85 | too weak |
    | charmander | 100 | 130      |
    +------------+-----+----------+

```
Explanation: if the attack column of a row is less than 50, then put too weak. Other than
that, put the regular value.

[go back to table of contents][home]

### IFNULL()
```sql
+----+-----------------+------+------+--------+
| id | name            | age  | sex  | weight |
+----+-----------------+------+------+--------+
|  1 | jacob ruler     |   24 | m    |   NULL |
|  3 | jane fonda      |   37 | NULL |    142 |
|  4 | nick gordon     | NULL | m    |    194 |
|  6 | miranda johnson |   17 | f    |   NULL |
|  7 | alex pennester  |   63 | NULL |    243 |
+----+-----------------+------+------+--------+

select name , ifnull(age, sex) from user limit 5;

+-----------------+-----------------+
| name            | ifnull(age,sex) |
+-----------------+-----------------+
| jacob ruler     | 24              |
| jane fonda      | 37              |
| nick gordon     | m               |
| miranda johnson | 17              |
| alex pennester  | 63              |
+-----------------+-----------------+

```
Explanation: this is pretty much **coalesce**. I do not see much of a difference.

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

### INSERT
- Adds rows/data into table
```sql
insert into pokemon (name, type, hp, attack, defense, trainer_id) values ("psyduck", "water", 90, 75, 66, 3);
```
Explanation:

[go back to table of contents][home]

### GREATEST()
```sql
 select name, attack, defense, speed, greatest(attack, defense, speed) as best from pokemon;

 +------------+--------+---------+-------+------+
| name       | attack | defense | speed | best |
+------------+--------+---------+-------+------+
| ghastly    |     35 |      30 |    80 |   80 |
| bulbasaur  |     65 |      85 |    27 |   85 |
| weedle     |     87 |      35 |    50 |   87 |
| abra       |     45 |      90 |    60 |   90 |
| charmander |    130 |      56 |    46 |  130 |
| psyduck    |     75 |      66 |    33 |   75 |
| ekans      |     60 |      44 |    55 |   60 |
| geodude    |     80 |     100 |    20 |  100 |
| staryu     |     45 |      55 |    85 |   85 |
| dragonair  |     84 |      65 |    70 |   84 |
+------------+--------+---------+-------+------+

```
Explanation: Chooses the greatest number based on the columns you add in the parameter

[go back to table of contents][home]

### GROUP BY
- group tells sql what column you are going to group the multiple values to
and orders them in that manner. So lets say there is a customer named "bob"
 and he made multiple purchases to a store name "macy's". If I wanted to show
 the multiple purchases that were made by bob, I would group it by bob
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


    +----+------------+-----------+
    | id | first_name | last_name |
    +----+------------+-----------+
    |  1 | Ash        | Ketchup   |
    |  2 | Gary       | Mustard   |
    |  3 | Misty      | Stone     |
    |  4 | Jessie     | Magenta   |
    |  5 | Brock      | Therock   |
    +----+------------+-----------+

    select concat(t.first_name, " ", t.last_name) as trainers, count(p.name) no_pokemon from
    trainers as t left join pokemon as p on t.id = p.trainer_id group by trainers;

    +----------------+------------+
    | trainers       | no_pokemon |
    +----------------+------------+
    | Ash Ketchup    |          2 |
    | Brock Therock  |          1 |
    | Gary Mustard   |          2 |
    | Jessie Magenta |          2 |
    | Misty Stone    |          3 |
    +----------------+------------+


```
Explanation: group by is like group_concat(distinct), whatever values that are connected to a
specific column will be grouped together in one virtual column. In this example, I grouped all
the pokemon that belong to a specific trainer so that you will know how many pokemon on trainer
possesses

[go back to table of contents][home]

### HAVING
- having is the equivalent to the where command, but this command is only necessary if you
are doing group by
```sql
    select concat(t.first_name, " ", t.last_name) as trainers, count(p.name) no_pokemon from
    trainers as t left join pokemon as p on t.id = p.trainer_id  
    group by trainers  having no_pokemon >2;

    +-------------+------------+
    | trainers    | no_pokemon |
    +-------------+------------+
    | Misty Stone |          3 |
    +-------------+------------+


```
Explanation: this is similar to the group by example, except it only retrieves no_pokemon column
that has more than 2 pokemon

[go back to table of contents][home]

### LEAST()
- I am going to assume that this function is similar to the greatest function.
Essentially, you several columns that have number values, and the function will look
lowest value and insert it into the virtual column
```sql

    select name , attack, speed, defense, least(attack, speed, defense) as weakest from pokemon;

    +------------+--------+-------+---------+---------+
    | name       | attack | speed | defense | weakest |
    +------------+--------+-------+---------+---------+
    | ghastly    |     35 |    80 |      30 |      30 |
    | bulbasaur  |     65 |    27 |      85 |      27 |
    | weedle     |     87 |    50 |      35 |      35 |
    | abra       |     45 |    60 |      90 |      45 |
    | charmander |    130 |    46 |      56 |      46 |
    | psyduck    |     75 |    33 |      66 |      33 |
    | ekans      |     60 |    55 |      44 |      44 |
    | geodude    |     80 |    20 |     100 |      20 |
    | staryu     |     45 |    85 |      55 |      45 |
    | dragonair  |     84 |    70 |      65 |      65 |
    +------------+--------+-------+---------+---------+

```
Explanation: finds the weakest attribute of the pokemon and displays it

[go back to table of contents][home]


### LIKE
- This expression searches for data rows where the property first name starts
with a capital B. And returns all the rows that have that
```sql
select * from trainer where  name like "A%"
```
Explanation: retrieves the rows that have an "A" in them

[go back to table of contents][home]

### LIMIT
- Limits the number of documents that you receive from the query
- You can have a start and end number or you can one number that will output then number of documents
```sql
select * from tablename limit startNumber, endNumber
```


```sql
    select * from pokemon limit 5, 10;
```
Explanation: This selects from tablename that will receive rows from the startNumber to the endNumber

[go back to table of contents][home]

### MAX()
- finds the highest number from a variety of values and displays it.
```sql
    select max(defense) as highest_defense_of_all_pokemon from pokemon;

    +--------------------------------+
    | highest_defense_of_all_pokemon |
    +--------------------------------+
    |                            100 |
    +--------------------------------+

```
Explanation: I got the highest defense from all the pokemon

[go back to table of contents][home]

### MD5()
- The value returns a binary string of 32 hex digits
```sql
    select md5("hello new world");

    +----------------------------------+
    | md5("hello new world")           |
    +----------------------------------+
    | 6dc422ea4e83e014c4456706c72730f6 |
    +----------------------------------+

```
Explanation: Turns a string into an encrypted string of numbers and words

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
    select now();

    +---------------------+
    | now()               |
    +---------------------+
    | 2017-07-26 22:59:01 |
    +---------------------+

```
Explanation: Gives you the current date and time

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
- generates a random number between 0 - 1
```sql
    select rand();
    +--------------------+
    | rand()             |
    +--------------------+
    | 0.3061164843906802 |
    +--------------------+

```
```sql
    select id, name, type, trainer_id from pokemon order by rand();

    +----+------------+---------+------------+
    | id | name       | type    | trainer_id |
    +----+------------+---------+------------+
    |  7 | ekans      | poison  |          4 |
    |  6 | psyduck    | water   |          3 |
    |  8 | geodude    | rock    |          5 |
    | 10 | dragonair  | dragon  |          2 |
    |  3 | weedle     | bug     |          3 |
    |  4 | abra       | psychic |          4 |
    |  9 | staryu     | water   |          3 |
    |  2 | bulbasaur  | grass   |          2 |
    |  1 | ghastly    | ghost   |          1 |
    |  5 | charmander | fire    |          1 |
    +----+------------+---------+------------+

```
Explanation: In this example, if you use order by you can generate rows in random
order .

[go back to table of contents][home]

### RENAME TO
- as far as I know, "rename to" only renames tables
```sql
    rename table pokemon to pocket_monsters
```
Explanation: I simply renamed the tables;

[go back to table of contents][home]

### REPLACE INTO
- replace into is similar to insert into, except if you are inserting new data and there is a primary key
that already exists  then the old row will be replaced by the new data
row.
```sql
     replace into pokemon values(7, "koffing","poison",35,60,44,55,4);

    +----+------------+---------+-----+--------+---------+-------+------------+
    | id | name       | type    | hp  | attack | defense | speed | trainer_id |
    +----+------------+---------+-----+--------+---------+-------+------------+
    |  1 | ghastly    | ghost   |  30 |     35 |      30 |    80 |          1 |
    |  2 | bulbasaur  | grass   | 110 |     65 |      85 |    27 |          2 |
    |  3 | weedle     | bug     |  75 |     87 |      35 |    50 |          3 |
    |  4 | abra       | psychic |  85 |     45 |      90 |    60 |          4 |
    |  5 | charmander | fire    | 100 |    130 |      56 |    46 |          1 |
    |  6 | psyduck    | water   |  90 |     75 |      66 |    33 |          3 |
    |  7 | koffing    | poison  |  35 |     60 |      44 |    55 |          4 |
    |  8 | geodude    | rock    |  40 |     80 |     100 |    20 |          5 |
    |  9 | staryu     | water   |  30 |     45 |      55 |    85 |          3 |
    | 10 | dragonair  | dragon  |  61 |     84 |      65 |    70 |          2 |
    +----+------------+---------+-----+--------+---------+-------+------------+

```
Explanation: I replaced the old name of the row that had the id of 7, from ekans to
koffing. replace into replaces values of an existing primary key or adds a new one.

[go back to table of contents][home]

### SHA1()
- similar to md5, it creates an encrpyted string based on the string you provided
```sql
    select sha1("test");
    +------------------------------------------+
    | sha1("test")                             |
    +------------------------------------------+
    | a94a8fe5ccb19ba61c4c0873d391e987982fbbd3 |
    +------------------------------------------+

```
Explanation: this shit is totally useless, so don't worry about it.

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
- Similar to enum but you can have multiple values into one row, and the multiple
values are ordered based on the values before it.

```sql
    create table colors(
    id serial,
    color set('red','blue','yellow','green')
    );

    insert into colors (color) values (1),(2),(3),(4),(5),(6),(7),(8),(9),(10),(11),(12);

    select * from colors;

    +----+-----------------+
    | id | color           |
    +----+-----------------+
    |  1 | red             |
    |  2 | blue            |
    |  3 | red,blue        |
    |  4 | yellow          |
    |  5 | red,yellow      |
    |  6 | blue,yellow     |
    |  7 | red,blue,yellow |
    |  8 | green           |
    |  9 | red,green       |
    | 10 | blue,green      |
    | 11 | red,blue,green  |
    | 12 | yellow,green    |
    +----+-----------------+


```
Explanation: As you see here the set data type allows you have multiple values stored into
one list number. And to be honest it is very confusing so don't worry about it. Avoid this stupid shit at all costs

[go back to table of contents][home]

### SHOW

### SHOW DATABASES
```sql
    show databases;
```
Explanation: simple

[go back to table of contents][home]

#### SHOW TABLES
```sql
    show tables;
```
Explanation: shows the tables in the database that you are in

[go back to table of contents][home]

#### SHOW COLUMNS from
```sql
  show columns from journal
```
Explanation: This is pretty much "explain journal"

[go back to table of contents][home]

#### SHOW TABLE STATUS
```sql
    show table status
```
Explanation: show all the tables specs like the engine being used, and some other shit.
I don't know if I will need use of this anytime soon

[go back to table of contents][home]

#### SHOW WARNINGS
- well ... it shows warning messages
```sql
    show warnings
```
Explanation: if there were any warnings when doing sql executions you will be able to see
them with this command

[go back to table of contents][home]

### SUM()
- You should know what this function does
```sql
select sum(attack) as all_pokemon_attack_power from pokemon;
```
Explanation: adds up all the attack power numbers from the pokemon

[go back to table of contents][home]


### TRUNCATE
- if this is talking about the number function, then it allows you to shorten the decimal
places. truncate(number, decimal places)
```sql

    +----+----------+
    | id | number   |
    +----+----------+
    |  1 |  5.43200 |
    |  2 |  8.23520 |
    |  3 | 12.12980 |
    +----+----------+

    select id, truncate(number,2) as num from decimals;

    +----+-------+
    | id | num   |
    +----+-------+
    |  1 |  5.43 |
    |  2 |  8.23 |
    |  3 | 12.12 |
    +----+-------+

```
Explanation: With the truncate function it cuts off the remaining decimals places and does not
round them up

[go back to table of contents][home]

### UNIX_TIMESTAMP
- will return the unix timestamp in seconds as an unsigned integer since '1970-01-01 00:00:00' UTC
```sql

    select unix_timestamp();

    +------------------+
    | unix_timestamp() |
    +------------------+
    |       1501778012 |
    +------------------+


```
Explanation: Gives you the amount of seconds that has passed since 1970

[go back to table of contents][home]

### UPDATE
- Updates a certain value in a column
```sql
update pokemon set name = "magmar" where id = 5;
```
Explanation: changes the name to the pokemon that has the id of 5

[go back to table of contents][home]


### WHERE
- Specifies what particular column will be effected
```sql
select hp , attack , defense from pokemon where name = "abra";
```
[go back to table of contents][home]


# MYSQL HOW TO

## Database
- [how to change the database engine][engine]

## Errors

## Foreign Key

- [how to create a foreign key][foreign-key]

## Importing/Dumping
- [how to import a database ][import]
- [how to dump a mysql database][dump]

## Joins

- [how to create a simple join][simple-join]
- [the "ON" keyword][on-join]
- [the "USING" keyword][using-join]

## Privileges
- [how to show all the privileges of a user][privilege-user]


## Settings
- [how to determine if timezone data is loaded into your mysql][timezone-check]
- [how to change the timezone in mysql ][change-timezone]
- [how to restart mysql][restart-mysql]

## Stored Prodedure
- [how to dump a stored procedure with a database][store-dump]

## Tables
- [how to clear data from a table][clear-table]

## Triggers
- [the trigger structure][trigger-structure]
- [how to change data before inserting][change-data]
- [how to create a trigger][trigger]



## Users

- [how to create a user and grant privileges][create-user]
- [how to change permissions and privileges for a user][permission]
- [how to list out all the users][list-users]

## Views
-[how to create a view][create-view]

## Stuff I need to do eventually

- how to set a variable
- how to do an after trigger
- how to install timezones into sql
- is sharding possible in mysql?
- when to use unique keys
-  how to do normalization properly
- how to use mysql workbench

[store-dump]:#how-to-dump-a-stored-procedure-with-a-database
[list-users]:#how-to-list-all-the-users
[create-view]:#how-to-create-a-view
[clear-table]:#how-to-clear-data-from-a-table
[trigger-structure]:#the-trigger-structure
[using-join]:#the-using-keyword
[on-join]:#the-on-keyword
[simple-join]:#how-to-create-a-simple-join
[restart-mysql]:#how-to-restart-mysql
[change-timezone]:#how-to-change-the-timezone-in-mysql
[timezone-check]:#how-to-determine-if-timezone-data-is-loaded-into-your-mysql
[privilege-user]:#how-to-show-all-the-privileges-of-a-user
[import]:#how-to-import-a-database
[change-data]:#how-to-change-data-before-inserting
[engine]:#how-to-change-the-database-engine
[create-user]:#how-to-create-a-user-and-grant-privileges
[trigger]:#how-to-create-a-trigger
[home]:#mysql-how-to
[dump]:#how-to-dump-a-mysql-database
[user]:#how-to-create-a-user
[permission]:#how-to-change-permissions-and-privileges-for-a-user
[foreign-key]:#how-to-create-a-foreign-key

---

### HOW TO DUMP A STORED PROCEDURE WITH A DATABASE

<details>
<summary>
View Content
</summary>

:link: **Reference**
- [Dumping MySQL Stored Procedures, Functions and Triggers](http://www.ducea.com/2007/07/25/dumping-mysql-stored-procedures-functions-and-triggers/)
---

:exclamation: **Note:** This command does not only save procedures it saves other
things like functions, and triggers

---

```
mysqldump <other mysqldump options> --routines outputfile.sql
```

</details>

[go back :house:][home]


### HOW TO LIST ALL THE USERS

<details>
<summary>
View Content
</summary>

**reference**
- [fast web host](https://www.fastwebhost.in/blog/mysql-list-users-how-to-list-mysql-user-accounts-via-command-line/)

```sql
SELECT User FROM mysql.user;
```

</details>


[go back :house:][home]

### HOW TO CREATE A VIEW

<details>
<summary>
View Content
</summary>

**reference**
- [thenewboston](https://www.youtube.com/watch?v=luO2MWjUqe4)
- [mysqltutorial](http://www.mysqltutorial.org/create-sql-views-mysql.aspx)

**My definition:**  Create a temporary table that retrieves a specific query that
was assigned to the view.

```sql
 CREATE VIEW tenCusts AS SELECT id , name, age, money FROM customers LIMIT 10;
```

</details>

[go back :house:][home]



### HOW TO CLEAR DATA FROM A TABLE

<details>

<summary>
View Content
</summary>

```
TRUNCATE TABLE insert_table;

```

</details>

[go back :house:][home]


### THE TRIGGER STRUCTURE

<details>

<summary>
View Content
</summary>

```sql
DELIMITER $$
CREATE TRIGGER  trigger_name
[BEFORE|AFTER] [INSERT|UPDATE|DELETE] ON table_name
FOR EACH ROW [FOLLOWS|PRECEDES] existing_trigger_name
BEGIN
…
END$$
DELIMITER ;

```

</details>

[go back :house:][home]


### THE USING KEYWORD

<details>

<summary>
View Content
</summary>

The USING(column_list) clause names a list of columns that must exist in both tables.

#### Creating the tables

```sql
create table companies(
    comp_id serial,
    name varchar(35)
);


create table consoles(
	cons_id serial,
	name varchar(35),
	 comp_id bigint(20) unsigned,
	 index(comp_id),
	constraint fk_console
	foreign key fk_console(comp_id) references Test.companies(comp_id)
	on update cascade
	on delete cascade
);

create table games(
	gam_id serial,
	name varchar(50),
	 cons_id bigint(20) unsigned,
	index(cons_id),
	price decimal(5,2),
	constraint fk_game
	foreign key fk_game(cons_id) references Test.consoles(cons_id)
	on update cascade
	on delete cascade
);


```

#### Inserting the data

```sql

insert into Test.companies (name) values
("Nintendo"),
("Playstation"),
("Microsoft");



insert into Test.consoles(name, comp_id) values
("Xbox 360" ,3),
("Playstation 4" , 2),
("3DS",1);


insert into Test.consoles(name, cons_id, price) values
("dead island" ,1,40),
("god of war 4" , 2, 60),
("witcher 3" , 2, 60),
("monster hunter:stories" , 3, 40),
("legend of zelda: a link between worlds" , 3, 40),
("dragon quest 7" , 3, 30);


```

#### Retrieving a table with USING keyword

```sql
SELECT g.gam_id as id ,  g.name as game,  c.name as company , co.name as console
FROM Test.consoles as co inner join Test.companies as c using(comp_id)
inner join Test.games as g  using(cons_id);


+----+----------------------------------------+-------------+---------------+
| id | game                                   | company     | console       |
+----+----------------------------------------+-------------+---------------+
|  1 | dead island                            | Microsoft   | Xbox 360      |
|  2 | god of war 4                           | Playstation | Playstation 4 |
|  3 | witcher 3                              | Playstation | Playstation 4 |
|  4 | monster hunter: stories                | Nintendo    | 3DS           |
|  5 | legend of zelda: a link between worlds | Nintendo    | 3DS           |
|  6 | dragon quest 7                         | Nintendo    | 3DS           |
+----+----------------------------------------+-------------+---------------+


```



</details>

[go back :house:][home]


### THE ON KEYWORD

<details>

<summary>
View Content
</summary>

**references**
- [Understanding JOINs in MySQL and Other Relational Databases](https://www.sitepoint.com/understanding-sql-joins-mysql-database/)

The **on** keyword compares the compares the primary key of one table to the foreign key of a
another


```sql
SELECT t.id as id, CONCAT(t.first_name, " " , t.last_name)  as name , group_concat(p.name) as pokemon
FROM Pokemon.trainers as t inner join Pokemon.pokemon as p

// This is comparing  trainers id to the pokemon trainer_id
ON t.id = trainer_id group by id;

```

</details>

[go back :house:][home]



### HOW TO CREATE A SIMPLE JOIN

<details>
<summary>View Content</summary>

**reference**
- [w3schools](https://www.w3schools.com/sql/sql_join.asp)

The join command connects tables together with the foreign key constraint


#### Getting the Pokemon's name, id, and the trainers first and last name

```sql

SELECT p.id AS id,  p.name  AS name, CONCAT(t.first_name, " ", t.last_name) AS trainer
FROM Pokemon.pokemon AS p
INNER JOIN Pokemon.trainers AS t ON p.trainer_id = t.id;



+----+------------+----------------+
| id | name       | trainer        |
+----+------------+----------------+
|  1 | ghastly    | Ash Ketchup    |
|  2 | bulbasaur  | Gary Mustard   |
|  3 | weedle     | Misty Stone    |
|  4 | abra       | Jessie Magenta |
|  5 | charmander | Ash Ketchup    |
|  6 | psyduck    | Misty Stone    |
|  7 | ekans      | Jessie Magenta |
|  8 | geodude    | Brock Therock  |
|  9 | staryu     | Misty Stone    |
| 10 | dragonair  | Gary Mustard   |
+----+------------+----------------+


```


#### Getting the trainers id, full name, and the pokemon they have


```sql
SELECT t.id as id, CONCAT(t.first_name, " " , t.last_name)  as name , group_concat(p.name) as pokemon
FROM Pokemon.trainers as t inner join Pokemon.pokemon as p
on t.id = trainer_id group by id;


+----+----------------+-----------------------+
| id | name           | pokemon               |
+----+----------------+-----------------------+
|  1 | Ash Ketchup    | ghastly,charmander    |
|  2 | Gary Mustard   | bulbasaur,dragonair   |
|  3 | Misty Stone    | staryu,psyduck,weedle |
|  4 | Jessie Magenta | ekans,abra            |
|  5 | Brock Therock  | geodude               |
+----+----------------+-----------------------+


```




</details>

[go back :house:][home]




### HOW TO CREATE A FOREIGN KEY


<details>
<summary>View Content</summary>

**reference**
- [mysqltutorial](http://www.mysqltutorial.org/mysql-foreign-key/)
- [w3schools](https://www.w3schools.com/sql/sql_foreignkey.asp)

#### If you are altering a table

1. create the first two  tables that will be referenced

````sql

create table customers(
id serial,
name varchar(45),
sex tinyint(1) default 0
)

create table menu(
id serial,
name varchar(25),
price decimal(4,2)
)



````

2. Next create the table the that will hold the id's of the parent tables.
**Remember** to create an index for the foreign key columns **and** make sure the datatypes are similar.
For example, if a primary key has `bigint(20) unsigned` you have to make sure your foreign key has the same value

```sql

create table orders(
id serial,
cust_id bigint(20) unsigned,
index(cust_id),
menu_id bigint(20) unsigned,
index(menu_id),
created_at datetime default current_timestamp
)


```

3. Now create the foreign keys by altering the table and adding them in

```sql

alter table orders
add constraint fk_menu
foreign key fk_menu(menu_id) references menu(id)
on delete cascade
on update cascade;


alter table orders
add constraint fk_cust
foreign key fk_cust(cust_id) references customers(id)
on delete cascade
on update cascade;

```

4. And that is pretty much it


#### If you are creating a table


1. create the first two  tables that will be referenced

````sql

create table customers(
id serial,
name varchar(45),
sex tinyint(1) default 0
)

create table menu(
id serial,
name varchar(25),
price decimal(4,2)
)



````

2. This time you will create orders while adding foreign keys to both tables

```sql

create table orders(
id serial,
cust_id bigint(20) unsigned,
index(cust_id),
menu_id bigint(20) unsigned,
index(menu_id),
constraint fk_cust
foreign key fk_cust(cust_id) references customers(id)
on update cascade
on delete cascade,
constraint fk_menu
foreign key fk_menu(menu_id) references menu(id)
on update cascade
on delete cascade
);


```


</details>

[go back :house:][home]


### HOW TO RESTART MYSQL

<details>
<summary>View Content</summary>

**reference**
:link: [coolest guides](https://coolestguidesontheplanet.com/start-stop-mysql-from-the-command-line-terminal-osx-linux/)

````
 /etc/init.d/mysql restart
````

</details>

[go back :house:][home]

### HOW TO CHANGE THE TIMEZONE IN MYSQL

<details>
<summary>View</summary>

1. check the current time

````
select now();
````

2. now add this command and value `+8:00` based on how much hours need to
be added or taken away

```
SET GLOBAL time_zone = '+8:00';
```
**Note:** this will only work when you are in mysql, after you leave the timezone
will reset back to the original timezone

</details>

[go back :house:][home]


### HOW TO DETERMINE IF TIMEZONE DATA IS LOADED INTO YOUR MYSQL

1. add this in your sql

```
SELECT CONVERT_TZ('2012-06-07 12:00:00', 'GMT', 'America/New_York');
```

2. if the result comes back null then you don't have it installed

[go back :house:][home]

### HOW TO SHOW ALL THE PRIVILEGES OF A USER

**references**
- [SHOW GRANTS Syntax](https://dev.mysql.com/doc/refman/5.7/en/show-grants.html)

```
SHOW GRANTS FOR 'jeffrey'@'localhost';
```

[go back :house:][home]

### HOW TO IMPORT A DATABASE

**reference**
- [How to import an SQL file using the command line in MySQL?](https://stackoverflow.com/questions/17666249/how-to-import-an-sql-file-using-the-command-line-in-mysql?rq=1)

1. create the database that you are trying to import

```
mysql -u jermaine -p

//inside mysql

create database portfolio;

exit;

```

2. now import the database into the newly created database

```
mysql -u jermaine -p <database name> < <insert path name>
```


[go back :house:][home]

### HOW TO CHANGE DATA BEFORE INSERTING
**reference**
- [MySQL automatic conversion on lowercase](https://stackoverflow.com/questions/12795021/mysql-automatic-conversion-on-lowercase)

```sql
// Let's say that you want to make sure that every name that is
// inserted becomes uppercase

// first create the table

create table people (id serial, name varchar(100));

// next create the trigger where you will set the new name to use uppercase function
delimiter $$
create trigger uppercase
before insert on people
for each row
set new.name = upper(new.name);
end $$

// when you insert the data

insert into people (name) values ('josh')

// it will output JOSH

```


[go back to home][home]

### HOW TO CHANGE THE DATABASE ENGINE
**reference**
- [How to change the database engine](https://www.siteground.com/kb/how_to_change_the_database_engine_of_a_mysql_database_table/)

```sql
alter table my_table engine = MyISAM

OR

alter table my_table engine = InnoDB
```
[go back to home][home]

### HOW TO CREATE A TRIGGER
There are so many different ways to create a trigger. Essentially,
the trigger will execute an action that you have set when you created
whether information is inserted, updated, or deleted is dependent upon
your created trigger. I will show a couple of examples of triggers. And
hopefully, I will understand this when I will look at this later


#### AFTER INSERT
```sql
create table customers (id serial, name varchar(100), account decimal(5,2));

insert into customers (name,account) values ('john',500.28);

create table orders (id serial, name varchar(40), amount decimal(5,2) );

delimiter $
	create trigger trigger_exchange
		after insert on orders
		 for each row
		 	begin
		 		update customers
				set account = account - new.amount
				where cust_id = new.cust_id;
			end $

insert into customers (name,amount) values ('burger', 10.28);

// the customer john's account will now show 490 instead 500.28 because of the trigger
```

#### AFTER INSERT EX:2

```sql
create table customers (id serial, name varchar(100));

create table orders (id serial, name varchar(40), item varchar(45) amount decimal(5,2) );

DELIMITER $$
 CREATE TRIGGER order_trigger
	AFTER INSERT ON customers
		FOR EACH ROW
			BEGIN
				SET @rand = FLOOR((RAND()*2)+1);
                SET @item = CASE WHEN @rand = 1  THEN "burger" WHEN @rand = 2  THEN "taco" ELSE  "salad"  END;
                SET @amount = @rand * FLOOR(RAND()*3);
                
				INSERT INTO orders (item, amount, customer_id) VALUES (@item, @amount, new.id);
		END;$$

DELIMITER ;
insert into customers (name) values ('jermaine forbes');

// This will show in the orders table: {id: 1, name: "jermaine forbes", item: "taco", amount:2.00 , customer_id:1}
```

#### BEFORE INSERT
```sql
create table customers (id serial, name varchar(100));

DELIMITER $$
 CREATE TRIGGER reverse_name_trigger
	BEFORE INSERT ON customers
		FOR EACH ROW
			BEGIN
				SET new.name = REVERSE(new.name);
	END;$$

DELIMITER ;

INSERT INTO customers (name) VALUES ("jessica mendez");

// outputs: {id: 1, name:"zednem acissej" } 
```
[go back to home][home]

### HOW TO CHANGE PERMISSIONS AND PRIVILEGES FOR A USER
<details>
<summary>
View content
</summary>
**reference**
- [How to Create a New User](https://www.digitalocean.com/community/tutorials/how-to-create-a-new-user-and-grant-permissions-in-mysql)

#### TYPES OF PERMISSIONS

Permissinon|Description
-|-
**all privleges**|as we saw previously, this would allow a MySQL user all access to a designated database (or if no database is selected, across the system)
**create**|allows them to create new tables or databases
**delete**|allows them to delete rows from tables
**update**|allow them to update table rows
**insert**|allows  them to insert rows into tables
**drop**|allows them to them to delete tables or databases
**select**|allows them to use the Select command to read through databases
**grant option**|allows them to grant or remove other users' privileges


```sql
// the formula to grant permissions

GRANT [type of permission] ON [database name].[table name] TO ‘[username]’@localhost;
```

```sql
// the formula to revoke permissions

REVOKE [type of permission] ON [database name].[table name] FROM ‘[username]’@‘localhost’;
```


</details>


[go back to :house:][home]


### HOW TO CREATE A USER AND GRANT PRIVILEGES
0. [How to Create a New User](https://www.digitalocean.com/community/tutorials/how-to-create-a-new-user-and-grant-permissions-in-mysql)

1. log into mysql
```
create user 'username'@'localhost' identified by 'password';
```
2. give the user all privileges
```
grant all privileges on *.* to 'username'@'localhost';
```
3. reload the privileges so that it can take effect
```
flush privileges;
```

4. the end

[go back to home][home]

### HOW TO DUMP A MYSQL DATABASE

<details>
<summary>
View Content
</summary>

 the essential command is this

```sql
	mysqldump -u *username* -p --all-databases > /path/to/location.sql
```
Explanation: this will dump all the databases to a specified location


#### HOW TO DUMP A DATABASE AND GZIP IT

instead of putting into an sql, it will gzip it. I think that means
that will compress the file

```sql
	mysqldump -u *username* -p --all-databases | gzip > /path/to/location.sql.gz
```


#### HOW TO DUMP ONE DATABASE

this dumps one database to a path

```sql
mysqldump -u <username> -p databaseName > /path/to/location.sql
```


#### HOW TO DUMP MULTIPLE DATABASES

this dumps multiple databases to a path

```sql
mysqldump -u <username> -p  --databases *insert database name*...*insert other database names* /path/to/location.sql
```

</details>



[go back to :house:][home]

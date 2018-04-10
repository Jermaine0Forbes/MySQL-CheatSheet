
# MYSQL HOW TO

## Database
- [how to change the database engine][engine]

## Errors

## Foreign Key

- [how to create a foreign key][foreign-key]

## Privileges
- [how to show all the privileges of a user][privilege-user]


## Settings
- [how to determine if timezone data is loaded into your mysql][timezone-check]
- [how to change the timezone in mysql ][change-timezone]
- [how to restart mysql][restart-mysql]

## Tables

## Triggers
- [how to change data before inserting][change-data]
- [how to create a trigger][trigger]

## Importing/Dumping
- [how to import a database ][import]
- [how to dump a mysql database][dump]

## Users

- [how to create a user and grant privileges][create-user]
- [how to change permissions and privileges for a user][permission]

## Stuff I need to do eventually

- how to set a variable 
- how to do an after trigger
- how to install timezones into sql
- is sharding possible in mysql?
- when to use unique keys
-  how to do normalization properly
- how to use mysql workbench 


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

delimeter $
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

#### BEFORE INSERT
```sql

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
	mysqldump -u *username* -p --alldatabase | gzip > /path/to/location.sql.gz
```


#### HOW TO DUMP ONE DATABSE

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

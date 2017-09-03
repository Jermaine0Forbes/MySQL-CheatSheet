
# MYSQL HOW TO

- [how to change data before inserting][change-data]
- [how to create a user and grant privileges][create-user]
- [how to dump a mysql database][dump]
- [how to change permissions and privileges for a user][permission]
- [how to create a trigger][trigger]
- [how to change the database engine][engine]

[change-data]:#how-to-change-data-before-inserting
[engine]:#how-to-change-the-database-engine
[create-user]:#how-to-create-a-user-and-grant-privileges
[trigger]:#how-to-create-a-trigger
[home]:#mysql-how-to
[dump]:#how-to-dump-a-mysql-database
[user]:#how-to-create-a-user
[permission]:#how-to-change-permissions-and-privileges-for-a-user

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
**reference**
- [How to Create a New User](https://www.digitalocean.com/community/tutorials/how-to-create-a-new-user-and-grant-permissions-in-mysql)

#### TYPES OF PERMISSIONS 

- **all privleges**: as we saw previously, this would allow a MySQL user all access to a designated database (or if no database is selected, across the system)
- **create**: allows them to create new tables or databases
- **delete**: allows them to delete rows from tables 
- **update**: allow them to update table rows
- **insert**: allows them to insert rows into tables
- **drop**: allows them to them to delete tables or databases
- **select**: allows them to use the Select command to read through databases 
- **grant option**: allows them to grant or remove other users' privileges

```sql
// the formula to grant permissions

GRANT [type of permission] ON [database name].[table name] TO ‘[username]’@'localhost’;
```

```sql
// the formula to revoke permissions

REVOKE [type of permission] ON [database name].[table name] FROM ‘[username]’@‘localhost’;
```
[go back to home][home]


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
- the essential command is this
```
	mysqldump -u *username* -p --all-databases > *location*
```
Explanation: this will dump all the databases to a specified location

```
	mysqldump -u *username* -p --alldatabase | gzip > *location.sql.gz*
```
Explanation: instead of putting into an sql, it will gzip it. I think that means
that will compress the file

[go back to home][home]

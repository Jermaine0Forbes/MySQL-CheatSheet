# logs

## 8/20/17

### tasks
- I am going to try to create a delete trigger even though I don't feel like it

### how to delete a trigger

```mysql
	
	DROP TRIGGER IF EXISTS `delete_this_shit`;CREATE DEFINER=`jermaine`@`localhost` TRIGGER `delete_this_shit` AFTER DELETE ON `list` FOR EACH ROW BEGIN delete from regular where id = old.id OR name = old.name; END 
```

### something to note
- Apparently, you need to add a delimeter when you create  a trigger I have never been
able to do it successfully with triggers

### here is the update trigger I created, a yesterday
```
	delimeter $
	create trigger trigger_exchange
		after insert on orders
		 for each row
		 	begin
		 		update customers 
				set account = account - new.amount 
				where cust_id = new.cust_id;
			end $



```
## 8/19/17

### tasks
- I am going to try to create a trigger inserts data into a table and deletes
the data when the other data is deleted
- I am going to try to create an update trigger

## 8/13/17

### tasks
- trying to create a trigger, wish me luck

#### 1st trigger
- okay, I created my first trigger and it didn't take me long to figure out 
that the delimiter keyword is bullshit and it does not matter. All of the info
that allowed me to understand trigger was [this](http://www.mysqltutorial.org/create-the-first-trigger-in-mysql.aspx) link. In any case let me write down
what I did so that my future self will see it.
```sql
	
	create table employee(
		id serial,
		first_name varchar(45),
		last_name varchar(45)
	);

	create table employee_list(
		id serial,
		name varchar(90),
		status varchar(7),
		registered datetime default current_timestamp
	);


	create trigger test_trigger
	after insert on employee
		for each row
			begin
				insert into employee_list 
				(name, status, registered) values
				(concat(new.first_name," ", new.last_name), rand(), now());

			end

```
- yep, I think that is all I did to create a trigger. So essentially, when I insert new 
row into **employee** it will also insert information into the table **employee_list**.
These values will grab first_name and last_name from employee and concat them into name,
it will generate a random number, and give the current time.

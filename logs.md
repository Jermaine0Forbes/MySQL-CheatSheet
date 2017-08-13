# logs


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
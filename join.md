# MYSQL JOINS   

## What do you need to know before doing a MySQL JOIN
[what is a foreign key][foreign]
[what is a foreign key constraint][constraint]
[the on keyword][on]
[the using keyword][using]


## Types of JOINS
[inner join][inner]
[left join][left]
[right join][right]
[natural join][natural]
[cross join][cross]


[home]:#mysql-joins
[foreign]:#what-is-a-foreign-key
[constraint]:#what-is-a-foreign-key-constraint
[on]:#the-on-keyword
[using]:#the-using-keyword
[inner]:#inner-join
[left]:#left-join
[right]:#right-join
[natural]:#natural-join
[cross]:#cross-join


## What is a JOIN
**reference**
- [w3resource](https://www.w3resource.com/mysql/advance-query-in-mysql/mysql-joins.php)
- [mysql](https://dev.mysql.com/doc/refman/5.7/en/join.html)
- [w3schools](https://www.w3schools.com/sql/sql_join.asp)

 A join is a command where you can combine two or more tables that will create a
 new table based on the specified columns that you are querying.

### What is a foreign key?

**reference**
- [MySQL Foreign Key](http://www.mysqltutorial.org/mysql-foreign-key/)

**MySQLTUTORIAL:** A foreign key is a field in a table that matches another field of another table.
A foreign key places constraints on data in the related tables

**My Definition:**  The foreign key links the primary key column from the root table to
the column of the  dependent table. You usually make these connections with an ID of a table

#### Example 1

```sql
// the root table

create table trainer (
    id serial,
    name varchar(100)
);

// the dependent table
create table pokemon(
    id serial,
    name varchar(50),
    trainer_id int  unsigned not null,
    foreign key  (trainer_id)
    references trainer(id)
    on delete cascade
    on update cascade
);
```

[go back home][home]

### What is a foreign key constraint

**reference**

```sql

```

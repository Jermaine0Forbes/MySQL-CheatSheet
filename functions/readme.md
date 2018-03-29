# MySQL Functions

## String 
- [concat()][concat]
- [concat_ws()][concat-ws]
- [substr][substr]
- [length][length]
- [format][format]



## Date 

- [date()][date]
- [current_timestamp][current-timestamp]
- [time()][time]

[format]:#format
[length]:#length
[substr]:#substr
[concat-ws]:#concat_ws
[concat]:#concat
[time]:#time
[date]:#date
[current-timestamp]:#current_timestamp
[home]:#mysql-functions





### format

<details>
<summary>
View Content
</summary>

Formats the number with commas, decimals and **rounds the decimals up**

`FORMAT(number, decimal_places)`


```sql

select format(12356.236,2);

+---------------------+
| format(12356.236,2) |
+---------------------+
| 12,356.24           |
+---------------------+

```

</details>

[go back :house:][home]



### length

<details>
<summary>
View Content
</summary>

Return the string length of the given value

`LENGTH(string)`



```sql

 select length("jermaine forbes");



+---------------------------+
| length("jermaine forbes") |
+---------------------------+
|                        15 |
+---------------------------+


```

</details>

[go back :house:][home]


### substr

<details>
<summary>
View Content
</summary>

`SUBSTR(string, start, length)`



```sql

 select substr("jermaine forbes", 1,7)


+--------------------------------+
| substr("jermaine forbes", 1,7) |
+--------------------------------+
| jermain                        |
+--------------------------------+

```

</details>

[go back :house:][home]

### concat_ws 

<details>
<summary>
View Content
</summary>
The first parameter is the string that you are going to use to seperate
the column values from each other. In this example, I just used "--"

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

</details>

[go back :house:][home]

### concat 

<details>
<summary>
View Content
</summary>

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
</details>

[go back :house:][home]

### time

<details>
<summary>
View Content
</summary>

gets the time from datetime or timestamp expressions

```sql
select id, first_name, time(trainer_registered) from trainers;

+----+------------+--------------------------+
| id | first_name | time(trainer_registered) |
+----+------------+--------------------------+
|  1 | Ash        | 22:07:46                 |
|  2 | Gary       | 22:08:43                 |
|  3 | Misty      | 22:10:15                 |
|  4 | Jessie     | 22:10:15                 |
|  5 | Brock      | 15:14:39                 |
+----+------------+--------------------------+
```

</details>



[go back :house:][home]

### date

<details>
<summary>
View Content
</summary>
extracts the date from the datetime expression

**reference**
:link: [w3schools](https://www.w3schools.com/sql/sql_ref_mysql.asp)

```sql
select id, first_name, date(trainer_registered) from trainers ;


+----+------------+--------------------------+
| id | first_name | date(trainer_registered) |
+----+------------+--------------------------+
|  1 | Ash        | 2017-07-02               |
|  2 | Gary       | 2017-07-02               |
|  3 | Misty      | 2017-07-02               |
|  4 | Jessie     | 2017-07-02               |
|  5 | Brock      | 2017-07-04               |
+----+------------+--------------------------+

```

</details> 



[go back :house:][home]

### current_timestamp

<details>
<summary>
View Content
</summary>
gives the default value the current timestamp

**reference**
- [Automatic Initialization and Updating for TIMESTAMP and DATETIME](https://dev.mysql.com/doc/refman/5.7/en/timestamp-initialization.html)

```sql
CREATE TABLE t1 (
  ts TIMESTAMP DEFAULT CURRENT_TIMESTAMP ON UPDATE CURRENT_TIMESTAMP,
  dt DATETIME DEFAULT CURRENT_TIMESTAMP ON UPDATE CURRENT_TIMESTAMP
);
```

</details>



[go back :house:][home]

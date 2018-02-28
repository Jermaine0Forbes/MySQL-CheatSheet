# MySQL Functions


## Date 

- [date][date]
- [current_timestamp][current-timestamp]
- [time][time]

[time]:#time
[date]:#date
[current-timestamp]:#current_timestamp
[home]:#mysql-functions


### time

gets the time from datetime or timestamp expressions

```
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

[go back :house:][home]

### date 

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

[go back :house:][home]

### current_timestamp

gives the default value the current timestamp

**reference**
- [Automatic Initialization and Updating for TIMESTAMP and DATETIME](https://dev.mysql.com/doc/refman/5.7/en/timestamp-initialization.html)

```sql
CREATE TABLE t1 (
  ts TIMESTAMP DEFAULT CURRENT_TIMESTAMP ON UPDATE CURRENT_TIMESTAMP,
  dt DATETIME DEFAULT CURRENT_TIMESTAMP ON UPDATE CURRENT_TIMESTAMP
);
```

[go back :house][home]

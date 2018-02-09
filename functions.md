# MySQL Functions

- [CURRENT_TIMESTAMP][current-timestamp]

[current-timestamp]:#current_timestamp
[home]:#mysql-functions

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

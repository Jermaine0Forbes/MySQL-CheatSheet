
# MYSQL HOW TO

- [how to dump a mysql database][dump]

[home]:#mysql-how-to
[dump]:#how-to-dump-a-mysql-database

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
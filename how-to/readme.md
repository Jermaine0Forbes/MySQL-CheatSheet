
# MYSQL HOW TO

- [how to dump a mysql database][dump]
- [how to create a user][user]
- [how to change permissions and privileges for a user][permission]
- [how to create a trigger][trigger]

[trigger]:#how-to-create-a-trigger
[home]:#mysql-how-to
[dump]:#how-to-dump-a-mysql-database
[user]:#how-to-create-a-user
[permission]:#how-to-change-permissions-and-privileges-for-a-user

### HOW TO CREATE A TRIGGER



### HOW TO CHANGE PERMISSIONS AND PRIVILEGES FOR A USER

```

```
[go back to home][home]

### HOW TO CREATE A USER
-
```

```
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
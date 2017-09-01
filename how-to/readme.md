
# MYSQL HOW TO

- [how to create a user and grant privileges][create-user]
- [how to dump a mysql database][dump]
- [how to change permissions and privileges for a user][permission]
- [how to create a trigger][trigger]

[create-user]:#how-to-create-a-user-and-grant-privileges
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

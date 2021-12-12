# 📝 MySQL connection error and Solution

- MySQL connection error and Solution

<br>

## 📌 Cannot access to mysql database
Error message
```
mysql connection error : Error: ER_DBACCESS_DENIED_ERROR: Access denied for user 'root'@'127.0.0.1' to database 'dog'
```

<br>

## ⛏️ Solution
1. Connect to mysql server
```
$ sudo mysql
```

2. 
```
CREATE USER 'root(yourUserName)'@'127.0.01(yourhost#)' IDENTIFIED WITH mysql_native_password BY 'enterYourPasswordHere';

or

ALTER USER 'root'@'127.0.01' IDENTIFIED WITH mysql_native_password BY 'enterYourPasswordHere';
```


3. 
```
grant all privileges on *.* to 'root'@'127.0.0.1';
```

4. 
```
FLUSH PRIVILEGES;
```

5. Check if the user is created
```
SELECT User, Host, authentication_string FROM mysql.user;
```

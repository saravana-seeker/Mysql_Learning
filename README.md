# Mysql_Learning
Mysql cheat sheet and some useful technique 

# Mysql With Nodejs 
## Connection

## Create a Database

## Create a table

## Insert a value

## Simple signup and signIn page 


## User Login
```
mysql -u root -p 
```
## Show users
```
SELECT User, Host FROM mysql.user;
```

## Create User
```
CREATE USER 'saravana'@'localhost' IDENTIFIED BY 'password';
```

## Delete User
```
DROP USER 'saravana'@'localhost'
```

## Show database;
```
SHOW DATABASES;
```

## Create Database
```
CREATE DATABASE saravana;
```
## Use Database;
```
USE  saravana;
```
## Delete database
```
DROP DATABASE saravana;
```
# Table

## Create a table
```
CREATE TABLE users( id INT auto_increment,firstname varchar(100),lastname varchar(100),email varchar(100), register_date DATETIME,primary key(id));
```

## Update a value / record with table
```
INSERT INTO users (firstname,lastname,email,register_date) values ("saravana","kumar","saravana@gmail.com",now());
```
## Getting all value
```
SELECT * FROM users;
```
## Specific set of value only 
```
SELECT firstname , lastname from users;
```
## Using id to get
```
SELECT firstname  from users where id = 2;
```
## Delete a Row  or user 
```
DELETE FROM users WHERE id=1;
```
## Update a Row or user
```
UPDATE users SET email="saravana@gmail.com" where id=2;
```

# Column
## Insert a columns to a table
```
ALTER TABLE users ADD age varchar(20);
```
## Modify the columns
```
ALTER TABLE users MODIFY age int;
```

## Limit  Key word

## Cheat Sheet
https://gist.github.com/bradtraversy/c831baaad44343cc945e76c2e30927b3




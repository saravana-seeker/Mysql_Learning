# Mysql_Learning
Mysql cheat sheet and some useful technique 

# Mysql With Nodejs 
## Connection
```
const mysql = require("mysql");
const con = mysql.createConnection({
  host: "localhost",
  user: "saravana",
  password: "password",
});
con.connect((err) => {
  if (err) throw err;
  console.log("Connected successfully");
});

```
## Create a Database
```
const mysql = require("mysql");
const con = mysql.createConnection({
  host: "localhost",
  user: "saravana",
  password: "password",
});
con.connect((err) => {
  if (err) throw err;
  console.log("Connected successfully");
  const sql = "CREATE DATABASE mydb";
  con.query(sql, (err, result) => {
    if (err) throw err;
    console.log(result);
  });
});

```

## Create a table User
```
const mysql = require("mysql");
const con = mysql.createConnection({
  host: "localhost",
  user: "saravana",
  password: "password",
  database: "mydb",
});
con.connect((err) => {
  if (err) throw err;
  console.log("Connected successfully");
  const sql = `CREATE TABLE user(id INT auto_increment ,first_name varchar(100),last_name varchar(100),email varchar(100) ,register_date DATETIME , primary key(id))`;
  con.query(sql, (err, result) => {
    if (err) throw err;
    console.log(result);
  });
});

```

## Insert a value into a user table
```
const mysql = require("mysql");
const con = mysql.createConnection({
  host: "localhost",
  user: "saravana",
  password: "password",
  database: "mydb",
});
con.connect((err) => {
  if (err) throw err;
  console.log("Connected successfully");
  const sql = `INSERT INTO  user(first_name,last_name,email,register_date) values("saravana","k","saravana@gmail.com",now())`;
  con.query(sql, (err, result) => {
    if (err) throw err;
    console.log(result);
  });
});

```

## Simple Signup and SignIn API 
[Login & SignUp](https://github.com/saravana-seeker/Mysql_Learning/blob/main/MySql_Nodejs_API.md)

## MYSQL User Login
```
mysql -u root -p 
```
## Mysql Grant All Permission
```
ALTER USER 'santhosh'@'localhost' IDENTIFIED WITH mysql_native_password BY 'password';
GRANT ALL PRIVILEGES ON * . * TO 'santhosh'@'localhost';
flush privileges;
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




## Intro 
1. Very beginner friendly approach for understand the login and signup concept using mysql nodejs connection.

## Install Modules

## Create Database
```jsx
const mysql = require("mysql");
const express = require("express");
const app = express();
const bcrypt = require("bcryptjs");
// mysql connection
const con = mysql.createConnection({
  host:"localhost",
  user: "saravana",
  password: "password"
});
//Create a database 
con.connect((err) => {
    if(err) throw err;
    console.log("Connected successfully ");
    con.query("CREATE DATABASE mydb",(error,result)=>{
        if(error) throw error;
        console.log(result)
    })
});
```

## Create a User tabel with NOT NULL Values
```js
con.connect((err) => {
  if (err) throw err;
  console.log("Connected successfully ");
  con.query(
    "CREATE TABLE users (id INT auto_increment NOT NULL,name varchar(100) NOT NULL,email varchar(100) NOT NULL , password varchar(250) NOT NULL,register_date DATETIME , primary key(id) )",
    (error, result) => {
      if (error) throw error;
      console.log(result);
    }
  );
});
```
## Insert Into user table
```js
con.connect((err) => {
  if (err) throw err;
  console.log("Connected successfully ");
  const sql = `INSERT INTO  users(name,email,password,register_date) values("saravana","saravana@gmail.com","password",now())`;
  con.query(sql, (error, result) => {
    if (error) throw error;
    console.log(result);
  });
});

```
## Register User 
```js
// Register --> name ,email ,and password
app.post("/register", async (req, res) => {
  const { name, email, password } = req.body;
  const hashPassword = await bcrypt.hash(password, 5);
  //check if the user exist in our database
  con.query("SELECT * FROM users WHERE email=?", [email], (err, result) => {
    if (err) throw err;
    if (result.length === 0) {
      con.query(
        "INSERT INTO users(name,email,password,register_date) values(?,?,?,now())",
        [name, email, hashPassword],
        (err, result) => {
          if (err) throw err;
          console.log("user create successfully ");
          res.send("user created successfully ");
        }
      );
    } else {
      res.send("User exist..!");
    }
  });
});

```
## Login Using bcryptjs
```js

app.post("/login", async (req, res) => {
  const { email, password } = req.body;
  con.query(
    "SELECT password from users where email = ?",
    [email],
    (err, result) => {
        if(err) throw err;
        const DbPass = result[0].password;
        const DeHash =  bcrypt.compare(password,DbPass,(err,result)=>{
            try{
                if(!result){
                    res.send("Invalid username and password")
                }
                else{
                    res.send("Login successfully ..!")
                }
            }
            catch(err){
                console.log(err)
            }
        })
      
    }
  );
});
```
## Final Login and Signup 
```jsx
const mysql = require("mysql");
const express = require("express");
const app = express();
const bcrypt = require("bcryptjs");

// mysql connection
const con = mysql.createConnection({
  host: "localhost",
  user: "saravana",
  password: "password",
  database: "mydb",
});

//
con.connect((err) => {
  if (err) throw err;
  console.log("database connected ");
});

app.use(express.json());

// Register --> name ,email ,and password
app.post("/register", async (req, res) => {
  const { name, email, password } = req.body;
  const hashPassword = await bcrypt.hash(password, 5);
  //check if the user exist in our database
  con.query("SELECT * FROM users WHERE email=?", [email], (err, result) => {
    if (err) throw err;
    if (result.length === 0) {
      con.query(
        "INSERT INTO users(name,email,password,register_date) values(?,?,?,now())",
        [name, email, hashPassword],
        (err, result) => {
          if (err) throw err;
          console.log("user create successfully ");
          res.send("user created successfully ");
        }
      );
    } else {
      res.send("User exist..!");
    }
  });
});

app.post("/login", async (req, res) => {
  const { email, password } = req.body;
  con.query(
    "SELECT password from users where email = ?",
    [email],
    (err, result) => {
        if(err) throw err;
        const DbPass = result[0].password;
        const DeHash =  bcrypt.compare(password,DbPass,(err,result)=>{
            try{
                if(!result){
                    res.send("Invalid username and password")
                }
                else{
                    res.send("Login successfully ..!")
                }
            }
            catch(err){
                console.log(err)
            }
        })
      
    }
  );
});



app.listen(3001, (err) => {
  if (err) throw err;
  console.log("server is running on port 3001");
});

```



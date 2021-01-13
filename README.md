# Code-Bits
As I continue to learn, here are the pieces of code that will help me learn. 


## Server Starter Code
```
const express = require("express");
const bodyParser = require("body-parser");
const ejs = require("ejs");
const mongoose = require('mongoose');

const app = express();

app.set('view engine', 'ejs');

app.use(bodyParser.urlencoded({
  extended: true
}));
app.use(express.static("public"));

//TODO

app.listen(3000, function() {
  console.log("Server started on port 3000");
});
```

## To Get MongoDB up and running
`mongod --dbpath /usr/local/var/mongodb --logpath /usr/local/var/log/mongodb/mongo.log --fork`

`mongod --config /usr/local/etc/mongod.conf`

`ps aux | grep -v grep | grep mongod`

`mongo`

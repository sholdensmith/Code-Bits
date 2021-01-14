# Code-Bits
As I continue to learn, here are the pieces of code that will help me learn. 


## Server Starter Code With Database
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

// SET UP DB
mongoose.connect("mongodb://localhost:27017/wikiDB", {useNewUrlParser: true, useUnifiedTopology: true});

// MONGO SCHEMA
const articleSchema = {
  title: String,
  content: String
};

const Article = mongoose.model("Article", articleSchema);

// GET AND SEND ALL ARTICLES
app.get("/articles", function(req, res) {
  Article.find(function(err, foundArticles){
    res.send(foundArticles);
  });
});

app.listen(3000, function() {
  console.log("Server started on port 3000");
});

```

## To Get MongoDB up and running
`mongod --dbpath /usr/local/var/mongodb --logpath /usr/local/var/log/mongodb/mongo.log --fork`

`mongod --config /usr/local/etc/mongod.conf`

`ps aux | grep -v grep | grep mongod`

`mongo`

## Deploying to Heroku
To get an app into git and deploy to heroku:
`git init`

`git add .`

`git commit -m “Initial commit”`

`heroku login`

`heroku create`

`touch Procfile`

`open Procfile` (and include the text `web: node app.js`

```
let port = process.env.PORT;
if (port == null || port == "") {
  port = 3000;
}

app.listen(port, function() {
  console.log("Server has started successfully.");
});
```

Put  in this with current version of node
```“engines”: {
    “node”: “10.x”
  },
```

Create a .gitignore file with 
```
/node_modules
npm-debug.log
.DS_Store
/*.env
```

again, do 
`git add .` and `git commit -m "Add gitignore, procfile, and updated ports, etc."`

then finally,
`git push heroku main`

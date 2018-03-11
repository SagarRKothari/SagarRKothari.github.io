---
layout: post
title:  "NodeJS - Connecting To MongoDB"
date:   2018-03-10 10:00:00
categories: nodejs
tags: nodejs js javascript MongoDB database connection
comments: true
logo: beer
---

Install dependencies.

```
npm init
npm install mongodb@2.2.5 --save
```

Download & Run [MongoDB](https://www.mongodb.com/download-center#community)

```
sh ~/mongo/bin/mongod --dbpath ~/mongo-data
```


```javascript
// 1. Load MongoDB library
// Get Mongo Client
const MongoClient = require('mongodb').MongoClient;

// 2. Connect to Database with MongoDB Client
MongoClient.connect('mongodb://localhost:27017/TodoApp', (error, db) => {
    // 3. If received an error, log error & return
    if (error) {
        return console.log('Unable to connect to MongoDB Server');
    }
    // 4. Log success message of MongoDB connected.
    console.log('Connected to MongoDB server');
    // 5. Insert a record to A collection named `ToDos`
    // 6. Pass a javascript object. In this case, object has text & completed.
    db.collection('Todos').insertOne({
        text: 'Something to do',
        completed: false
    // 7. Handle insertion response.
    }, (error, result) => {
        // 8. If error received do something.
        if (error) {
            return console.log('Unable to insert todo', error);
        }
        // 9. If record inserted successfully, do somehthing
        console.log(JSON.stringify(result.ops, undefined, 2));
    });
    // 10. Close the connection now
    db.close();
});
```


Download & launch [`Robo 3T`](https://robomongo.org/download)
You should see output as follows.

![Robo3TImage]({{ "/assets/2018-03-10/Robo3T.png" | absolute_url }})

I agree, screenshot above & code given above are not matching.
There you go.

```javascript
    db.collection('Users').insertOne({
        name: 'Sagar R. Kothari',
        age: 30,
        location: 'Hyderabad, Telangana, India'
    }), (error, result) => {
        if (error) {
            return console.log('Unable to insert User', error);
        }
        console.log(JSON.stringify(result.ops, undefined, 2));
    }
```
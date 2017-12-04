---
layout: post
title:  "NodeJS - First express application with nodejs"
date:   2017-12-01 10:00:00
categories: nodejs
tags: nodejs js express javascript
comments: true
logo: flask
---

I started learning `node.js`. `Express` is one of the most popular package.
I created my first `express` server & `hello world` of express is as follows.

```javascript
// Load Express module
const express = require('express');

// Create server - variable app is server instance.
var app = express();

// Tell sever to use public folder to load static htmls
app.use(express.static(__dirname + '/public'));


// tell server to manage this get request with given response
app.get('/', (request, response) => {
    // response.send('<h1>Hello Express!</h1>');
    response.send({
        name: 'Sagar',
        likes: [
            'Programming',
            'Reading',
            'Blogging'
        ]
    })
});

// tell server to manage `/about` get request to manage with following response
app.get('/about', (req, res) => {
    res.send('About Sagar Page.');
});

// tell server to manage `/bad` get request with following request
app.get('/bad', (req, res) => {
    res.send({
        errorMessage: 'Something went wrong.'
    });
});

// tell server to start with port 3000 & log a message when started
app.listen(3000, () => {
    console.log('Server is up on port 3000');
});
```
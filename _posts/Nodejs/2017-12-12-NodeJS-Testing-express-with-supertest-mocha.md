---
layout: post
title:  "NodeJS - Testing express application with supertest and mocha"
date:   2017-12-12 10:00:00
categories: nodejs
tags: nodejs js javascript testing test expect supertest mocha 
comments: true
logo: beer
---

Install dependencies.

```
npm init
npm install express --save
npm install mocha --save-dev # this will install mocha as developer dependencies.
npm install supertest --save-dev # this will supertest mocha as developer dependencies.
```

Here is the sample file to be tested.

```javascript
// server.js
const express = require('express');
var app = express();

app.get('/', (req, res) => {
    res.send('Hello World!');
});

app.listen(3000);

module.exports.app = app; // exporting app so that it can be easily accessible from test classes.
```

Here is the file for sample code having test case.

```javascript
// server.test.js
const request = require('supertest');

var app = require('./server').app;

it('should return hello world response', (done) => {
    request(app)
        .get('/')
        .expect(200)
        .expect('Hello World!')
        .end(done);
});
```

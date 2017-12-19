---
layout: post
title:  "NodeJS - Setting and starting maintenance mode"
date:   2017-12-06 10:00:00
categories: nodejs
tags: nodejs js express javascript maintenance
comments: true
logo: bookmark-o
---

Following illustrates how to create start maintainance mode for nodejs express applications.

Run following command to setup & install above specified modules.

```
npm init
npm install express --save
npm install hbs --save
```

Following is the code for `server.js` file. Please find inline comments to understand code.

```javascript
// load fs module
const fs = require('fs');

// load handlebars module
const hbs = require('hbs');

// load express module
const express = require('express');

// create an instance of express and variable name is `app`
var app = express();

// setting the view engine. 
// Telling express app that for view engine we will be using handlebars
app.set('view engine', 'hbs');

// following method will be invoked before any request hit.
// here, we're injecting custom code which will be executed before each request execution.
// it is known as `MIDDLEWARE`
app.use((request, response, next) => {
    // convert current time stamp to readable string
    var now = new Date().toString();
    var logMessage = `${now}: ${request.method} ${request.url}`;
    // log request-method and request-url with time-stamp
    console.log(logMessage);
    // log it to file
    fs.appendFile('server.log', logMessage + '\n', (error) => {
        if (error) {
            console.log('Got some error while logging into file. Error: ' + error.message);
        }
    });
    // application continues only if you run next function.
    // please make sure you run next function or-else every request will fail.
    next();
});

// following method will be invoked after above fuction for any request hit.
// here, we're injecting custom code which will be executed after above function & before each request execution.
// as we are not going to run NEXT function, it will stop all requests.
app.use((request, response, next) => {
    // render from `maintenance.hbs` file.
    response.render('maintenance.hbs');
});

// telling express app to listen requests on port 3000
// and logging custom message once started.
app.listen(3000, () => {
    console.log('Server started on port 3000');
});
```

Contents of `maintenance.hbs` file.

```html
<!DOCTYPE html>
<html>
    <head>
        <title>Some Website</title>
    </head>
    <body>
        <h1>We'll be right back.</h1>
        <p> This site is under update process. </p>
    </body>
</html>
```

Here is the sample output.

![Demo]({{"/assets/2017-12-06/demo.png" | absolute_url}})

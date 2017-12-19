---
layout: post
title:  "NodeJS - Server.log - Creating logger"
date:   2017-12-05 10:00:00
categories: nodejs
tags: nodejs js express javascript logger
comments: true
logo: bookmark-o
---

Following illustrates how to create a logger for `nodejs` express application.

Run following command to setup & install above specified modules.

```
npm init
npm install express --save
```

Following is the code for `server.js` file. Please find inline comments to understand code.

```javascript
// load fs module
const fs = require('fs');

// load express module
const express = require('express');

// create an instance of express and variable name is `app`
var app = express();

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

// telling express app to listen requests on port 3000
// and logging custom message once started.
app.listen(3000, () => {
    console.log('Server started on port 3000');
});
```

Once server is started, upon each request, you'll see a log in console.
Here is the sample output.

```
Server started on port 3000
Tue Dec 19 2017 20:16:48 GMT+0530 (IST): GET /
Tue Dec 19 2017 20:17:00 GMT+0530 (IST): GET /about
Tue Dec 19 2017 20:17:10 GMT+0530 (IST): GET /
```

Here is the sample output for `server.log` file.

![Server.log]({{"/assets/2017-12-05/Server-log.png"}})
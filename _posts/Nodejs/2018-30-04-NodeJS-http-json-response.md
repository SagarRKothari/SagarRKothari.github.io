---
layout: post
title:  "NodeJS - Sending JSON Response with http"
date:   2018-04-30 10:00:00
categories: nodejs
tags: nodejs js javascript JSON http
comments: true
logo: beer
---

Install dependencies.

```
npm init
npm install http --save
```

```javascript
const http = require('http');

const hostname = 'localhost';
const port = 3000;

const server = http.createServer((req, res) => {
    const { url } = req;
    console.log(url);
    if (url === '/translation') {
        const translation = {
            1: "One",
            2: "Two",
            3: "Three"
        };
        res.setHeader('Content-Type', 'application/json');
        res.write(JSON.stringify(translation));
        res.end();
    }
    res.end('Welcome to Node.');
});

server.listen(port, hostname, () => {
    console.log(`Server Started at ${hostname}:${port}`);
});
```
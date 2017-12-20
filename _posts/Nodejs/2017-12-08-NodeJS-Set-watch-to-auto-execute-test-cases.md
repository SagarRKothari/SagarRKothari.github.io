---
layout: post
title:  "NodeJS - Setting up watch to auto execute test cases"
date:   2017-12-08 10:00:00
categories: nodejs
tags: nodejs js javascript mocha scripts
comments: true
logo: coffee
---

In this article, I'm going to illustrate how to auto-execute test cases with scripts of `package.json`

Please [view part-1 of setting up mocha for testing]({{ site.baseurl }}{% post_url Nodejs/2017-12-07-NodeJS-Testing-with-mocha %})

```json
{
  "name": "node-web-server",
  "version": "1.0.0",
  "description": "",
  "main": "index.js",
  "scripts": {
    "test": "mocha **/*.test.js",
    "test-watch": "nodemon --exec 'npm test'" // this will run `npm test` as soon as code is changed
  },
  "author": "",
  "license": "ISC",
  "dependencies": {
    "express": "^4.16.2",
    "hbs": "^4.0.1"
  },
  "devDependencies": {
    "mocha": "^4.0.1"
  }
}

```

Now go back to terminal & run following command to start auto-execution of test cases.

```
npm run test-watch
```

Above should give you the output as follows.


```sh
node-web-server$ npm run test-watch

> node-web-server@1.0.0 test-watch /Users/sagar/LearnNodeJS/node-web-server
> nodemon --exec 'npm test'

[nodemon] 1.12.1
[nodemon] to restart at any time, enter `rs`
[nodemon] watching: *.*
[nodemon] starting `npm test`

> node-web-server@1.0.0 test /Users/sagar/LearnNodeJS/node-web-server
> mocha **/*.test.js



  ✓ should add two numbers
  ✓ should square a number

  2 passing (6ms)

[nodemon] clean exit - waiting for changes before restart
^C
node-web-server$
```
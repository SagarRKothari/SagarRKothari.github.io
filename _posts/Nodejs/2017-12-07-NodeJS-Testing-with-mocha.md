---
layout: post
title:  "NodeJS - Testing your Nodejs application with Mocha"
date:   2017-12-07 10:00:00
categories: nodejs
tags: nodejs js javascript mocha
comments: true
logo: coffee
---

[Mocha](http://mochajs.org/) is a simple, flexible, fun JavaScript test framework for node.js and the browser.

```
npm init
npm install mocha --save-dev # this will install mocha as developer dependencies.
```

Here is the file which we'll be testing.


```javascript
// utils.js
module.exports.add = (a, b) => a + b;
module.exports.square = (a) => a * a;
```

Here is the file which covers code for testing.

```javascript
// utils.test.js
const utils = require('./utils');

it('should add two numbers', () => {
    var result = utils.add(10, 20);
    if (result !== 30) {
        throw new Error(`Expected 30, got ${result}`);
    }
});

it('should square a number', () => {
    var result = utils.square(10);
    if (result !== 100) {
        throw new Error(`Expected 100, got ${result}`);
    }
});
```

Here is the partial code of `package.json` file.

```json
{
  "name": "node-web-server",
  "version": "1.0.0",
  "description": "",
  "main": "index.js",
  "scripts": {
    "test": "mocha **/*.test.js" // this command will run mocha to test our test cases
  },
  "author": "",
  "license": "ISC",
  "dependencies": {
    "express": "^4.16.2",
    "hbs": "^4.0.1"
  },
  "devDependencies": { // dev-specific dependencies
    "mocha": "^4.0.1"
  }
}
```

To start executing test cases, run following command from `terminal`.

```
npm test # which will run "mocha **/*.test.js" command
```

Here is the example output of above command.

```sh
node-web-server$ npm test

> node-web-server@1.0.0 test /Users/sagar/LearnNodeJS/node-web-server
> mocha **/*.test.js



  ✓ should add two numbers
  ✓ should square a number

  2 passing (8ms)

node-web-server$
```
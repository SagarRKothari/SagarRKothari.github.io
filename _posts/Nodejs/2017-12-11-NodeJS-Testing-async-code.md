---
layout: post
title:  "NodeJS - Testing Async Code"
date:   2017-12-11 10:00:00
categories: nodejs
tags: nodejs js javascript testing test expect jest 
comments: true
logo: coffee
---

In this article, I've added the a sample code for testing async code.

```javascript
// utils.js file
module.exports.add = (a, b) => a + b;
module.exports.square = (a) => a * a;

// a method for which test case has been added
module.exports.asyncAdd = (a, b, callback) => {
    setTimeout(() => {
        callback(a + b);
    }, 1000);
};
```

Test-case for above function.

```javascript
// utils.test.js
it('should async add two numbers', (done) => {
    utils.asyncAdd(10, 20, (result) => {
        expect(result).toBe(30);
        expect(result).toBeA('number');
        done();
    });
});
```
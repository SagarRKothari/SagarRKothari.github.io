---
layout: post
title:  "NodeJS - Testing with expect and/or jest"
date:   2017-12-09 10:00:00
categories: nodejs
tags: nodejs js javascript mocha jest expect
comments: true
logo: coffee
---

In this article, I'm going to illustrate how to use `expect` to write test cases.

Please [view part-1 of setting up mocha for testing]({{ site.baseurl }}{% post_url Nodejs/2017-12-07-NodeJS-Testing-with-mocha %})

```
npm init
npm install mocha --save-dev # this will install mocha as developer dependencies.
npm install expect@1.20.2 --save-dev
npm i jest --save-dev
```

Here is the sample file to be tested.

```javascript
// utils.js
module.exports.add = (a, b) => a + b;
module.exports.square = (a) => a * a;
```

Here is the file for sample code having test cases.

```javascript
const expect = require('expect');
const utils = require('./utils');

it('should add two numbers', () => {
    var result = utils.add(10, 20);
    expect(result).toBe(30).toBeA('number');
});

it('should square a number', () => {
    var result = utils.square(10);
    expect(result).toBe(100).toBeA('number');
});

// Extra test function demonstrating different functions of expect library.

it('should expect some values', () => {
    // if both the objects are same
    expect({name: 'Sagar'}).toEqual({name: 'Sagar'});

    // if both the objects are not same
    expect({name: 'Sagar'}).toNotEqual({name: 'Amit'});

    // if it has
    expect([2,3,4]).toInclude(4);

    // if it doesn't have
    expect([2,3,4]).toExclude(5);

    // if object has a specific property
    expect({
        name: 'Sagar',
        age: 29,
        location: 'Hyderabad'
    }).toInclude({
        name: 'Sagar'
    });

    // if object does NOT have a specific property
    expect({
        name: 'Sagar',
        age: 29,
        location: 'Hyderabad'
    }).toExclude({
        name: 'Amit'
    });
});

```
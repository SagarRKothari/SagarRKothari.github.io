---
layout: post
title:  "NodeJS - JSON Conversion"
date:   2017-11-24 10:00:00
categories: nodejs
tags: nodejs js javascripting javascript
comments: true
logo: coffee
---

In this post, I'll explain about converting `JSON` to `String` and from `String` to `JSON`.

##### Convert from `JSON` to `String`

```javascript
// Get your object
var obj = {
    name: 'Sagar'
};
// convert it to string
var stringObj = JSON.stringify(obj);
console.log(typeof stringObj);
console.log(stringObj);
```

##### Convert from `String` to `JSON`

```javascript
// Get your string
var personString = '{ \
    "name": "Sagar", \
    "age": 29 \
}';
// convert it to JSON
var person = JSON.parse(personString);
console.log(typeof person);
console.log(person)
```
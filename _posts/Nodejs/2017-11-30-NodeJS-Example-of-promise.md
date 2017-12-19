---
layout: post
title:  "NodeJS - Example of Promises in ES6"
date:   2017-11-30 10:00:00
categories: nodejs
tags: nodejs js ES6 javascript promise promiese
comments: true
logo: flask
---

Here, I've added a simple example of usage of Promise in javascript for Node.js.

```javascript
var asyncAdd = (a, b) => {
    return new Promise((resolve, reject) => {
        setTimeout(() => {
            if (typeof a === 'number' && typeof b === 'number') {
                resolve(a + b);
            } else {
                reject('Arguments must be numbers');
            }
        }, 1500);
    });
}

asyncAdd(10, 15).then((result) => {
    console.log('Result: ', result);
}, (error) => {
    console.log(error);
});
```

Above function can be chained with multiple calls. Here is an example.

```javascript
asyncAdd(10, 15).then((result) => {
    console.log('Result: ', result);
    return asyncAdd(result, 33); 
}, (error) => {
    console.log(error);
}).then((result) => {
    console.log('Result: ', result);
}, (error) => {
    console.log(error);
});
```

But such chainings are not recommended. For better usage, use catch block in Promise.

```javascript
asyncAdd(10, '15').then((result) => {
    console.log('Result: ', result);
    return asyncAdd(result, 33); 
}).then((result) => {
    console.log('Result: ', result);
}).catch((error) => {
    console.log(error)
});
```
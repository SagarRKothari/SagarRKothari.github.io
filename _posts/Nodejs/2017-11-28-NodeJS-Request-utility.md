---
layout: post
title:  "NodeJS - Using Request package for sending requests"
date:   2017-11-28 10:00:00
categories: nodejs
tags: nodejs js request http call service server
comments: true
logo: send
---

##### About

[request](https://www.npmjs.com/package/request) is designed to be the simplest way possible to make http calls. It supports HTTPS and follows redirects by default.

##### Installation

```sh
npm install request
```

##### Usage

```javascript
var request = require('request');
request('http://www.google.com', function (error, response, body) {
  console.log('error:', error); // Print the error if one occurred
  console.log('statusCode:', response && response.statusCode); // Print the response status code if a response was received
  console.log('body:', body); // Print the HTML for the Google homepage.
});
```

Another Example.

```javascript
let requestedAddress = argv.address;
let encodedAddress = encodeURIComponent(requestedAddress);
let urlToRequest = 'https://maps.googleapis.com/maps/api/geocode/json?key=YOUR_GOOGLE_MAP_API_KEY&address=' + encodedAddress;

request({
    url: urlToRequest,
    json: true
}, (error, response, body) => {
    if (error) {
        console.log('Something went wrong');
    } else if (body.status === 'OK') {
        var result = body.results[0];
        console.log(`Address: ${result.formatted_address}`);
        console.log(`Address: ${result.geometry.location.lat}`);
        console.log(`Address: ${result.geometry.location.lng}`);
    } else if (body.status === 'ZERO_RESULTS') {
        console.log('Unable to find that address.');
    } else {
        console.log('No Results found.');
    }
});
```
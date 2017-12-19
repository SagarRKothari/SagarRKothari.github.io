---
layout: post
title:  "NodeJS - Get weather details from given address"
date:   2017-11-29 10:00:00
categories: nodejs
tags: nodejs js request http call service server
comments: true
logo: send
---

Problem Statement: Get weather of given address from command line.

In this post, I've used 3 `js` files.

* `App.js` will take care of arguments from command line.
* `geocode.js` will take care of converting address to lat-lng using google api.
* `weather.js` will take care of provide weather from given lat-lng details.

External dependencies

* maps.googleapis.com
* api.darksky.net

#### `App.js`

```javascript
const yargs = require('yargs');

const geocode = require('./geocode/geocode.js');
const weather = require('./weather/weather.js');

const argv = yargs
    .options({
        a: {
            demand: true,
            alias: 'address',
            describe: 'Address to fetch weather for',
            string: true
        }
    })
    .help()
    .alias('help', 'h')
    .argv;

geocode.geocodeAddress(argv.address, (error, results) => {
    if (error) {
        console.log(error);
    } else {
        // console.log(JSON.stringify(results, undefined, 2));
        weather.getWeather(results.latitude, results.longitude, (error, result) => {
            if (error) {
                console.log(error);
            } else {
                console.log(`Current temperature is ${result.temperature}`);
            }
        });
    }
});
```

#### `geocode.js`

```javascript
const request = require('request');

var geocodeAddress = (address, callback) => {
    var encodedAddress = encodeURIComponent(address);
    var urlToUse = `https://maps.googleapis.com/maps/api/geocode/json?address=${encodedAddress}&key=YOUR_API_KEY`;
    request({
        url: urlToUse,
        json: true
    }, (error, response, body) => {
        if (error) {
            callback('Unable to connect to Google Servers.');
        } else if (body.status === 'ZERO_RESULTS') {
            callback('Unable to find that address');
        } else if (body.status === 'OK') {
            callback(undefined, {
                address: body.results[0].formatted_address,
                latitude: body.results[0].geometry.location.lat,
                longitude: body.results[0].geometry.location.lng
            });
        }
    });
};

module.exports.geocodeAddress = geocodeAddress;
```

#### `weather.js`

```javascript
const request = require('request');

var getWeather = (latitude, longitude, callback) => {
    var urlToUse = `https://api.darksky.net/forecast/YOUR_API_KEY/${latitude},${longitude}`;
    request({
        url: urlToUse,
        json: true
    }, (error, response, body) => {
        if (error) {
            callback('Unable to connect to Forecast Servers.');
        } else if (response.statusCode === 400) {
            callback('Unable to fetch weather');
        } else if (response.statusCode === 200) {
            callback(undefined, {
                temperature: body.currently.temperature
            });
        }
    });
};

module.exports.getWeather = getWeather;
```
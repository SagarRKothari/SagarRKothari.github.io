---
layout: post
title:  "NodeJS - Example of weather fetch with axios"
date:   2017-12-01 10:00:00
categories: nodejs
tags: nodejs js axios promise
comments: true
logo: flask
---

Here, I've added a simple example of usage of Promise in javascript for Node.js.
Following example also illustrates usage of promise chaining.

```javascript
const yargs = require('yargs');
const axios = require('axios');

const argv = yargs
    .options({
        a: {
            demand: true,
            alias: 'address',
            string: true,
            describe: 'Address to fetch weather for'
        }
    })
    .help()
    .alias('help', 'h')
    .argv;

var encodedAddress = encodeURIComponent(argv.address);
var geocodeURL = `https://maps.googleapis.com/maps/api/geocode/json?address=${encodedAddress}&key=YOUR_SERVER_KEY`

axios.get(geocodeURL).then((response) => {
    if (response.data.status === 'ZERO_RESULTS') {
        throw new Error('Unable to find that address');
    }
    var lat = response.data.results[0].geometry.location.lat;
    var lng = response.data.results[0].geometry.location.lng;
    var darkskyURL = `https://api.darksky.net/forecast/YOUR_KEY/${lat},${lng}`;
    console.log(response.data.results[0].formatted_address);
    return axios.get(darkskyURL);
}).then((response) => {
    var temperature = response.data.currently.temperature;
    var apparant = response.data.currently.apparentTemperature;
    console.log(`It seems like ${temperature}. It feels like ${apparant}`);
}).catch((error) => {
    if (error.code === 'ENOTFOUND') {
        console.log('Unable to connect to servers');
    } else {
        console.log(error.message);
    }
});
```
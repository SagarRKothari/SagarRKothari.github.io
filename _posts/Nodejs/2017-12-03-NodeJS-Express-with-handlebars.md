---
layout: post
title:  "NodeJS - Express application with handlebars"
date:   2017-12-03 10:00:00
categories: nodejs
tags: nodejs js express javascript handlebars
comments: true
logo: bookmark-o
---

I started learning `node.js`. `Express` is one of the most popular package.
With the help of [`handlebarsjs`](http://handlebarsjs.com/), we can achieve templating.

Run following command to setup & install above specified modules.

```
npm init
npm install express --save
npm install hbs --save
```

Following is the code for `server.js` file. Please find inline comments to understand code.

```javascript
// load express module
const express = require('express');

// load handlebars module
const hbs = require('hbs');

// create an instance of express and variable name is `app`
var app = express();

// loading static contents from `public` directory. 
// for example, if I have `help.html` file under public folder, 
// any one can access it by, http://localhost:3000/help.html
app.use(express.static(__dirname + '/public'))

// setting the view engine. 
// Telling express app that for view engine we will be using handlebars
app.set('view engine', 'hbs');

// telling handlebars that we've kept our partial files here.
// partial files contains common html contents like common headers, footers 
hbs.registerPartials(__dirname + '/views/partials')

// telling handlerbars to use this helper function inside handlebar files.
// if I use {{getCurrentYear}} inside html.hbs file, it will display current year
hbs.registerHelper('getCurrentYear', () => {
    return new Date().getFullYear();
});

// telling handlebars to use this helper function inside handlebar files.
// if I use { { screamIt welcomeMessage } } = WELCOME TO MY WEBSITE. YAY
hbs.registerHelper('screamIt', (message) => {
    return message.toUpperCase();
});

// telling express application to use `home.hbs` 
// for rendering & using passed parameters
app.get('/', (request, response) => {
    // response.send('Hello Express!');
    response.render('home.hbs', {
        pageTitle: 'Home page',
        welcomeMessage: 'Welcome to my website. Yay.'
    });
});

// telling express application to use `about.hbs` for `/about` request
// for rendering & using passed parameters
app.get('/about', (request, response) => {
    response.render('about.hbs', {
       pageTitle: 'About Page'
    });
});

// telling express app to listen requests on port 3000
// and logging custom message once started.
app.listen(3000, () => {
    console.log('Server started on port 3000');
});
```

Followings are contents for different files.

![Folder Contents]({{'/assets/2017-12-03/folder-structure.png' | absolute_url}})

> `footer.hbs` (Partial file)

```hbs
<footer>Created By: Sagar R Kothari. Copyright {{getCurrentYear}}</footer>
```

> `header.hbs` (Partial file)

```hbs
<h1>{{pageTitle}}</h1>
<p><a href="/">Home</a></p>
<p><a href="/about">About</a></p>
```

> `about.hbs`

```hbs
<html>
    <head>
        <title> { { pageTitle } } </title>
    </head>
    <body>
        { { > header } }
        <p>Help Page content goes here.</p>
       { { > footer } }
    </body>
</html>
```

> `home.hbs`

```hbs
<!DOCTYPE html>
<html>
    <head>
        <title> { { pageTitle } } </title>
    </head>
    <body>
        { { > header } }
        <p> { { screamIt welcomeMessage } } </p>
        { { > footer } }
    </body>
</html>
```

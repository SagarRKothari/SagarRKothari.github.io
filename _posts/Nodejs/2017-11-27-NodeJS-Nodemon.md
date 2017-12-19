---
layout: post
title:  "NodeJS - Nodemon for server or error monitoring"
date:   2017-11-27 10:00:00
categories: nodejs
tags: nodejs js nodemon server error monitoring
comments: true
logo: refresh
---

##### About

[nodemon](https://www.npmjs.com/package/nodemon) will watch the files in the directory in which nodemon was started, and if any files change, nodemon will automatically restart your node application.

nodemon does not require any changes to your code or method of development. nodemon simply wraps your node application and keeps an eye on any files that have changed. Remember that nodemon is a replacement wrapper for node, think of it as replacing the word "node" on the command line when you run your script.

##### Installation

```sh
npm install -g nodemon
```

##### Usage

```sh
nodemon app.js
```

##### Example output

```sh
$ nodemon app.js 
[nodemon] 1.12.1
[nodemon] to restart at any time, enter `rs`
[nodemon] watching: *.*
[nodemon] starting `node app.js`
Command not recognized
[nodemon] clean exit - waiting for changes before restart
```

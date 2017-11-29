---
layout: post
title:  "NodeJS - Using fs module to read write to files"
date:   2017-11-26 10:00:00
categories: nodejs
tags: nodejs js fs file read write
comments: true
logo: file-o
---

##### About

[fs](https://nodejs.org/api/fs.html) is provided by simple wrappers around standard POSIX functions. To use this module do require('fs'). All the methods have asynchronous and synchronous forms.


#### Deleting file

ASync Version

```javascript
const fs = require('fs');

fs.unlink('/tmp/hello', (err) => {
  if (err) throw err;
  console.log('successfully deleted /tmp/hello');
});
```

Sync Version

```javascript
const fs = require('fs');

fs.unlinkSync('/tmp/hello');
console.log('successfully deleted /tmp/hello');
```

#### Reading file

Sync Version

```javascript
var notesString = fs.readFileSync('notes-data.json');
var notesFromFile = JSON.parse(notesString);
```

##### Writing to file

Sync Version

```javascript
// notes loaded from memory
var myNotesInMemory = JSON.parse(fs.readFileSync('notes-data.json')); 
// notes being written to file
fs.writeFileSync('notes-data.json', JSON.stringify(notes));
```
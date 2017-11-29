---
layout: post
title:  "NodeJS - yargs utility for command line help"
date:   2017-11-25 10:00:00
categories: nodejs
tags: nodejs js yargs commandline arguments
comments: true
logo: terminal
---

##### About

[Yargs](https://www.npmjs.com/package/yargs) helps you build interactive command line tools, by parsing arguments and generating an elegant user interface.

It gives you:

* commands and (grouped) options (my-program.js serve --port=5000).
* a dynamically generated help menu based on your arguments.

Example:

![ScreenShot](https://raw.githubusercontent.com/yargs/yargs/HEAD/screen.png)

##### Installation

```sh
npm install yargs --save
```

---

##### Usage

---

###### Importing `yargs`
```javascript
const yargs = require('yargs');
```

Example terminal commands, to accept, are as follows, for a terminal-based-notes application.

```sh
$node app.js list # which will list all the notes
$node app.js read --title='My Secret Note'
$node app.js add -t="Note Title" -b="Note body section"
$node app.js add --title="My Personal Note title" --body="Custom note body"
```

###### Setting up `yargs`
```javascript
const titleOptions = {
  describe: 'Title of note',
  demand: true,
  alias: 't'
};
const bodyOptions = {
  describe: 'Body of note',
  demand: true,
  alias: 'b'
};
const argv = yargs
  .command('add', 'Add a new note', {
    title: titleOptions,
    body: bodyOptions
  })
  .command('list', 'List all notes')
  .command('read', 'Read a note', {
    title: titleOptions,
  })
  .command('remove', 'Remove a note', {
    title: titleOptions
  })
  .help()
  .argv;
var command = argv._[0];
```

###### Using `yargs` variable

```
if (command === 'add') {
  // do something to add a note
  // argv.title 
  // argv.body
} else if (command === 'list') {
  // do something to list all notes
} else if (command === 'read') {
  // do something to read a specific note
  // argv.title = requested note title
} else if (command === 'remove') {
  // do something to remove a specific note
  // argv.title = requested note title
}
```

###### Another Example.

If you want user to provide address, you can configure `yargs` as follows.

```javascript
const argv = yargs
    .options({
        a: { // name of parameter
            demand: true, // requires true
            alias: 'address', // alias - another name
            describe: 'Address to fetch weather for', // description of command. It will be displayed in help
            string: true // is it string? 
        }
    })
    .help() // generates help
    .alias('help', 'h') // alias of help command
    .argv; // argument values
```

Need more examples? [Click here.](https://github.com/yargs/yargs/blob/HEAD/docs/examples.md)
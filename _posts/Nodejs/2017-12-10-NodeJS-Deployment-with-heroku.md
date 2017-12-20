---
layout: post
title:  "NodeJS - Deployment with heroku"
date:   2017-12-10 10:00:00
categories: nodejs
tags: nodejs js javascript heroku deployment 
comments: true
logo: coffee
---

In this article, I've added the steps which I've followed for deployment to `heroku`.

***Step 1.*** Update your code as indicated below. Please insert code which takes port number dynamically from process.

```javascript
const express = require('express');

const portFromProcess = process.env.PORT || 3000;

var app = express();

app.listen(portFromProcess, () => {
    console.log(`Server started on ${portFromProcess} port`);
});
```

***Step 2.*** Make sure you have `git` as version control system & all your changes are commited & pushed to origin.

***Step 3.*** Run `heroku login` command to login to your heroku account. I assume you've heroku account.

```
sagar (master) node-web-server $ heroku login
```

***Step 4.*** Run `heroku keys:add` command to add key. In my case, I selected `id_rsa.pub`

```
sagar (master) node-web-server $ heroku keys:add
? Which SSH key would you like to upload? (Use arrow keys)
❯ /Users/sagar/.ssh/id_rsa.pub 
  /Users/sagar/.ssh/id_rsa_assembla.pub 
  /Users/sagar/.ssh/id_rsa_github_sag333ar.pub 
  /Users/sagar/.ssh/id_rsa_github_sagardevices.pub 
```

***Step 5.*** To ensure, keys are added run following command

```
sagar (master) node-web-server $ heroku keys
heroku keys:remo=== sag333ar@gmail.com keys
ssh-rsa AAAAB3NzaC...qOWnTlAw== sag333ar@gmail.com
```

***Step 6.*** Now run following command to set-up & authenticate with heroku.

```
sagar (master) node-web-server $ ssh -v git@heroku.com
```

You should see output as follows. I've added last few lines of output here.

```
debug1: Server accepts key: pkalg ssh-rsa blen 279
debug1: Authentication succeeded (publickey).
Authenticated to heroku.com ([50.19.85.154]:22).
debug1: channel 0: new [client-session]
debug1: Entering interactive session.
debug1: pledge: network
debug1: Sending environment.
debug1: Sending env LC_CTYPE = UTF-8
PTY allocation request failed on channel 0
shell request failed on channel 0
```

***Step 7.*** Create `heroku` app.

```
heroku create
```

After executing above command, I got following output.

```
sagar (master) node-web-server $ heroku create
Creating app... done, ⬢ agile-retreat-76589
https://agile-retreat-76589.herokuapp.com/ | https://git.heroku.com/agile-retreat-76589.git
```

***Step 8.*** Push/deploy your app to heroku.

```
git push heroku master
```

After executing above command, I got following output.

```
remote: -----> Compressing...
remote:        Done: 18.7M
remote: -----> Launching...
remote:        Released v3
remote:        https://agile-retreat-76589.herokuapp.com/ deployed to Heroku
remote: 
remote: Verifying deploy... done.
To https://git.heroku.com/agile-retreat-76589.git
```

Here is the output from heroku-admin-panel & website.

![Heroku-admin-panel]({{"/assets/2017-12-10/heroku.png" | absolute_url}})

---

![website]({{"/assets/2017-12-10/webapp.png" | absolute_url}})
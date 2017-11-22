---
layout: post
title:  "npm install throws error - UNABLE TO GET ISSUER CERT LOCALLY"
date:   2017-11-22 02:00:00
categories: Tools
tags: tools ReactNative npm install error Nodejs 
comments: true
logo: hand-o-up
---

While installing npm modules, I was getting following error.
Please find the solution which I've used below error message.

```
npm ERR! fetch failed https://github.com/expo/node-websql/archive/18.0.0.tar.gz
npm WARN retry will retry, error on last attempt: Error: unable to get local issuer certificate
npm ERR! fetch failed https://github.com/expo/node-websql/archive/18.0.0.tar.gz
npm WARN retry will retry, error on last attempt: Error: unable to get local issuer certificate
npm ERR! fetch failed https://github.com/expo/node-websql/archive/18.0.0.tar.gz
npm ERR! Darwin 16.7.0
npm ERR! argv "/usr/local/bin/node" "/usr/local/bin/npm" "install" "--save"
npm ERR! node v6.10.0
npm ERR! npm  v3.10.10
npm ERR! code UNABLE_TO_GET_ISSUER_CERT_LOCALLY

npm ERR! unable to get local issuer certificate
npm ERR! 
npm ERR! If you need help, you may report this error at:
npm ERR!     <https://github.com/npm/npm/issues>
```

After receiving such errors & tried to find out the root cause. 
I came to know that due to strict SSL downloads, npm downloads were failing.
Firewalls were causing issues & downloads from npm were being rejected.

I executed following command to disable strict SSL checks. 

```
npm config set strict-ssl false
```

After this, I was able to download npm commands correctly.

Here are the set of commands which I was trying to execute.

```
$ npm install -g create-react-native-app
$ create-react-native-app my-app
$ cd my-app/
$ npm start
```
---
layout: post
title:  "Generating Archive - list of Articles"
date:   2017-10-28 10:00:00
categories: Scripts
tags: Jekyll Customization Github Pages
---

### Step 1.

Create `Archive.html` under root folder of your web-site.

----

### Step 2.

Copy And Paste following Code into `html` file which you just created.

```
---
layout: default
title: Archive
---

<div id="home">
  <h1>Archive ( { { site.posts | size } } posts)</h1>
  <ul class="posts">
    { % for post in site.posts % }
      <li><span> { { post.date | date_to_string } } </span> &raquo; <a href=" { { post.url } }"> { { post.title } } </a></li>
    { % endfor % }
  </ul>
</div>
```

### Step 3.

Run following command to start server.

```
bundle exec jekyll serve
```

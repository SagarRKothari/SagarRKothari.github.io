---
layout: post
title:  "Generating Category wise article list"
date:   2017-10-30 10:00:00
categories: Scripts
tags: Jekyll Customization Github Pages
---

### Step 1.

Create `Categories.html` under root folder of your web-site.

----

### Step 2.

Copy And Paste following Code into `html` file which you just created.

```
---
layout: default
title: Categories
---

<h1>Category wise articles</h1>

<ul>
{ % assign tags list = site.categories  % }  
   { %  if tags list.first[0] != null  % } 
     { %  for tag in tags list  % }  
      <li>
         { { tag[0] } } 
        <ul>
           { %  assign pages list = tag[1]  % }   
           { %  for post in pages list  % } 
             { %  if post.title != null  % } 
               { %  if group == null or group == post.group  % } 
                <li><a href=" { { site.url } }  { { post.url } } "> { { post.title } } 
                  (<span class="entry-date"><time datetime=" { { post.date | date to xmlschema } } " itemprop="datePublished"> { { post.date | date: " % B  % d,  % Y" } } )</time>
                </span></a></li>
               { %  endif  % } 
             { %  endif  % } 
           { %  endfor  % } 
           { %  assign pages list = nil  % } 
        </ul>
      </li>
     { %  endfor  % } 
   { %  endif  % } 
 { %  assign tags list = nil  % } 
</ul>
```

### Step 3.

Run following command to start server.

```
bundle exec jekyll serve
```

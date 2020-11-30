---
title: Template engine NodeJS
date: "2017-08-19"
template: "post"
draft: false
slug: "templating-node-js"
category: "Programming"
tags:
  - "Nodejs"
  - "Programming"
description: "template engine for your nodejs application"
socialImage: "/media/42-line-bible.jpg"
---
### Template engine for ExpressJS

How to do templating using `ejs` in node js.

Install ejs

```bash
npm install ejs --save 
```

Make sure you create a `views` folder at the root level, where all your HTML(.ejs) files will go



In the `server.js` where your express js is mentioned add the following line

```jsx
app.set('view engine', 'ejs');
```

In the routes return the HTML files as follows

```jsx
res.render('index'); // index should be present inside the views folder
```

How to have common files, like headers, footer, import common layouts to the pages

```java
<%-  include('header'); %> // make sure there is a file header.ejs in the same folder level
```
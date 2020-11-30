---
title: Middleware NodeJS
date: "2017-08-19"
template: "post"
draft: false
slug: "nodejs-middleware"
category: "Programming"
tags:
  - "NodeJS"
  - "Programming"
description: "Add Middleware to your code"
socialImage: "/media/42-line-bible.jpg"
---

### Intercept all the HTTP request

How to log all the HTTP request in node js?

It is not a great idea to write print statements in all the requests, in node js middlewares come in handy to solve this problem.

How to implement, create a file `middelware.js`

```jsx
/**
 * middle ware for intercepting all the request
 * @param {*} req 
 * @param {*} res 
 * @param {*} next 
 */
let restGateway = (req, res, next) => {
		console.log("URL => "+ req.url);
    next(); // next will be a callback sent back to the original request
}
module.exports = {
    restGateway: restGateway
  }
```

In routes, file implement something like this

```jsx
router.get('/index', **middleware.restGateway**, (req, res) => {
    res.render('pages/index');

});
```
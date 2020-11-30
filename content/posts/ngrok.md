---
title: Make your application access from anywhere
date: "2020-09-22"
template: "post"
draft: false
slug: "ngrork"
category: "Programming"
tags:
  - "Programming"
  - "Infra"
description: "NGROK - Public URL for testing your chatbot"
socialImage: "/media/42-line-bible.jpg"
---

Definitely, you might have come across the scenario of I have the local application running, how to check the webhooks from a 3rd party application?

Here is the easy solution - Download `ngrok` https://ngrok.com/ for your OS after installation

 If your application runs on 8000 execute the following command, make sure your ngrok executable is present in the folder.
```
./ngrok http 8000 // port number
```
You can see the following screen in your bash

![/media/ngrork.jpeg](/media/ngrork.png)

Now you can see an `http` and `https`, make sure you have allowed all hosts in your server application

```
app.run(host='0.0.0.0') // for flask apps
ALLOWED_HOSTS = ['*'] // in your sertings file change to this, for django
```

To debug the requests you can go to `localhost:4040`

![/media/debug_ngrork.png](/media/debug_ngrork.png)

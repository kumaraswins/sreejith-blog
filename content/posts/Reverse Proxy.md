---
title: Reverse Proxy
date: "2019-08-19"
template: "post"
draft: false
slug: "reverse-proxy"
category: "Server"
tags:
  - "Python"
  - Django
  - "Programming"
description: "Serialize your json using django rest framework"
socialImage: "/media/42-line-bible.jpg"
---

The reverse proxy is proxy servers that will fetch content(HTML, CSS, API calls) on behalf of the client.

The client will be the end-user computer, mobile phones, etc, the server will be hosted on the cloud platform like AWS/Google/Azure. It will hide the existence of the real server and serves as a proxy to the real REST call.

How does it work?


Here we can take the example of Nginx, and see how it does reverse proxy, it acts as a web server on the above diagram.

While developing in the local machine the application runs on a certain port, 8000 or 3000. While you deploy the same in the cloud we need to bind the port 80 and the port number where our application runs(express or flask servers). 

Port 80 is dedicated to receiving the incoming request and route the request to the configured port.

```bash
server {
       listen 80;
                      location /static/ {
              root  {{ your_path }}; # serve your static file
       }
```

Doing the reverse proxy like the following

```bash
location / {
               proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
               proxy_redirect off;
               include proxy_params;
               proxy_pass http://127.0.0.1:8888;
       }
```

Full configurations look like this

```bash
server {
       listen 80;
       server_name {{ server_name }};
       location = /favicon.ico { access_log off; log_not_found off; }
       location /static/ {
              root  {{ your_path }};
       }
       location / {
               proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
               proxy_redirect off;
               include proxy_params;
               proxy_pass http://127.0.0.1:8888;
       }
}
```
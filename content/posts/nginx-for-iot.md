---
title: NGINX for IOT devices
date: "2020-09-21"
template: "post"
draft: false
slug: "config-nginx-iot"
category: "Programming"
tags:
  - "Programming"
  - "IOT"
  - "Home Automation"
description: "How to configure NGINX for IOT devices."
socialImage: "/media/42-line-bible.jpg"
---


Most of the IoT devices will not be compatible with modern web servers. To make IoT enable devices we need to make sure the webserver communication is sorted.

I have used NodeMCU ESP8266 for making my home a smart home, but when I deployed to a remote server the communication was not happening. By default, NGINX is HTTP compliant we need to configure it for HTTP 1.0


```
server {
       listen 80;
       server_name {{ server_name }};

       location = /favicon.ico { access_log off; log_not_found off; }

       location /static/ {
              root  /home/ubuntu/home;
       }


       location / {
          proxy_http_version 1.0;
          proxy_set_header Upgrade $http_upgrade;
          proxy_set_header Connection "Upgrade";
          proxy_set_header        X-Forwarded-For   $remote_addr;
          proxy_set_header        X-Real-IP         $remote_addr;
          proxy_set_header        Host              $host;
          proxy_set_header Access-Control-Allow-Origin *;
          proxy_read_timeout 900;
          proxy_pass http://127.0.0.1:3000;
       }
}
```
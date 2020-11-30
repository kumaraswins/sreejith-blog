---
title: IOT Device Sockets
date: "2020-09-21"
template: "post"
draft: false
slug: "iot-sockets"
category: "Programming"
tags:
  - "Programming"
  - "IOT"
  - "Home Automation"
description: "Connect your controller to the cloud machine"
socialImage: "/media/42-line-bible.jpg"
---

The biggest challenge for any controller is the communication to the cloud machine. 

We can see how NodeMCU ESP8266 is connected to the cloud machine

Server-side NodeJS, socket io for bi-directional communication on-demand without Bluetooth module.

Client/Controller will be C++ 

Use normal socket io connection on the server-side.

Initial declaration

```
#include <ESP8266WiFi.h>
#include "ArduinoJson.h"
#include "SocketIOClient.h"
#include "PZEM004Tv30.h"
PZEM004Tv30 pzem(&Serial);

StaticJsonBuffer<200> jsonBuffer;

SocketIOClient client;
const char* ssid     = "**** Your SSID ****";
const char* password = "****Password****";

char host[] = "*****IP address*****";
int port = ***PORT***;
```

Make sure it tries to connect until it connects to the internet

```
void client_connect() {

  while (!client.connect(host, port)) {
    Serial.println("connection failed");
    delay(1000);
  }
if (client.connected())
  {
    client.send("connection", "message", "Connected !!!!");
  }

  if (client.monitor()) {
    Serial.println(RID);
    Serial.println(Rname);
    Serial.println(Rcontent);
    root["complete"] = "init";
    root.printTo(JSON);
    client.sendJSON("JSON", JSON);
  }
}
```
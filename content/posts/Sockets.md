---
title: Sockets
date: "2017-08-19"
template: "post"
draft: false
slug: "sockets-io"
category: "Programming"
tags:
  - "NodeJS"
  - "Programming"
description: "Sockets IO, async request response"
socialImage: "/media/42-line-bible.jpg"
---[Socket.io](http://socket.io) is the easiest way to establish sockets communication between a client and a server.

### Why sockets?

Conventionally, the client can communicate with the server through REST or SOAP APIs. What if a server wanted to push some information to the client. It can do bidirectional communication easily.

### How it works?

Initially, the server and the client will do a handshake with HTTP and the client gets 100 as the status code(protocol changes). From now it will be a web sockets call(HTTP to WS).

After the connections are established then it will get constant acknowledgment from the client and the server.

```jsx
- `ping`. Fired when a ping packet is written out to the server.
- `pong`. Fired when a pong is received from the server.
```

![Sockets%20f35c637c45224bbfa33fe70fca4968ed/sock.png](/media//sock.png)

Sockets Arch

### Node JS Implementation - Server side

Go to [https://socket.io/](https://socket.io/)

```jsx
var io = require('socket.io')(http);
var getSocketId =  function(socketMessage, basket){
        var oJson = {};
        var message = socketMessage.split("|");
        var uuid = message[0];
        oJson["socketId"] = basket[uuid];
        oJson["message"] = message[1];
        return oJson;
    }
var rooms = {}
io.on('connection', function(socket) {
   // this will prevent broadcasting to particular client 
    socket.on('message', function(msg) {
        var socket_ = getSocketId(msg,rooms);
        io.to(socket_["socketId"]).emit('message', socket_['message']);
    });
// resgister with unique id and socket id
    socket.on('init', function(msg) {
        rooms[message] = socket.id;
    }
}
```

### Client Side implementation

```html
<script src="/socket.io/socket.io.js"></script>
<script>
  const socket = io('http://localhost');

socket.on('message', (msg) => {
  console.log(msg)
});
</script>
```
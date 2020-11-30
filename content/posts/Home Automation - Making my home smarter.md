---
title: Home Automation - Making My Home Smarter
date: "2020-10-20"
template: "post"
draft: false
slug: "home"
category: "Programming"
tags:
  - "Programming"
  - "IOT"
  - "Home Automation"
description: "How I made my home as a smart home"
socialImage: "/media/42-line-bible.jpg"
---



When the pandemic broke, people started to feel bored and was clueless what to,  I was not an exception though.  I and my school mates were having a video chat and suddenly a friend of mine told me why can’t we make our home smart home. Like a stereotype, everyone was saying it would take a lot of money, and more importantly, our houses were 20 years old as well as the switchboards. Finally, we decided to install a new set of a box that will be placed above your conventional switchboards without changing anything. 

What are the skill sets required to do this?

1. Electronics knowledge with hands-on experience, like doing soldering, designing the circuit.
2. Electrical understanding of your house, AC / DC  differentiation.
3. Microcontrollers and programming them.
4. Web app development to make it configurable.

## Hardware Components are materials required 
> PCB (printed circuit board). Where all your components stay and have your connections intact.  
> Relay Control - electro-mechanical switch , which turns on and off your circuit on demand.  
> AC -DC converter. All your components are DC powered, but it will be connected to the AC supply of your house to power your circuit.
> Micro-controller - node MCU, why we chose this because it can be connected to your WiFi, for communication. 
> Power measurements module.

- - - -
Components before connections. 
![](/media/base.jpg)

We have used 4 `Relay Boards` . Each relay can connect 2 switches, in my house we have chosen 8 switches to control through our application. 


After all the circuit connections it looks like this

![](/media/cir.png)

- - - -

### Installation on the real switch-board

It is always harder to make it real and make it work beyond a  project.

We have to open our switchboards to connect with our circuits.

![](/media/wiring.jpeg)

After all the connections the whole switchboard looks like this
![](/media/switch.jpg)

## Application Details

Tech Stack

1. Node JS, application wrapper with express JS and MySQL for DB
2. Socket IO for communication with the IoT devices.
3. Arduino Editor for programming Node MCU.

![](/media/block.jpg)


The features are as follows. 

1. Device management - Manage and register your home devices with a proper authentication process.
2. Device Connectivity -  Seamless connectivity and configurable.
3. Data Analytics -  Shows how much power is consumed live.
4. Dashboard App - Responsive dashboard and works on all platforms.



<figure class="video_container">
  <video controls="true" allowfullscreen="true" poster="/media/dash_banner.png">
    <source src="/media/DashOut.mp4" type="video/mp4">
  </video>
</figure>

 - - - -

 Final Working 

 <figure class="video_container">
  <video controls="true" allowfullscreen="true" poster="/media/out_banner.png">
    <source src="/media/ou.mp4" type="video/mp4">
    
  </video>
</figure>

Major Contributors - 

1. [Murali Krishnan](  https://www.linkedin.com/in/muralikrih/). Responsible for the design and development of hardware and circuit connections.
2. [Prasanna Rajagopal]( https://www.linkedin.com/in/sprajagopal/). Microcontroller programming and configurations
3. Myself - Building dashboard and integrations and dedicated my house for testing  :P



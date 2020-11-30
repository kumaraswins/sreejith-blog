---
title: Mitra Robot
date: "2020-09-20"
template: "post"
draft: false
slug: "mitra"
category: "Robotics"
tags:
  - "Robotics"

description: "Mitra robot built in India, I was part of core founding team"
socialImage: "/media/42-line-bible.jpg"
---

Evolution is not only pertained to humans it is also applicable for Robots. It can be compared to a child’s growth from nappies to becoming an adult.

Invento robotics company founded by 2016 October, the company was formed on the intention to produce consumer robots. Initially, we didn't have much of a clue for choosing the materials, we have to do a lot of background research to decide on the robot structure how it should look. It was 5 people to start with.

> **We came across some fascinating data through some of the research papers**

1. Robots built in the past was not taller than humans, since humans were intimidated if they see robots taller than him.
2. All the robotic voice like google home, Alexa all have a female voice, psychology report says that male voice feels more dominating compared to female voice.
3. When you say people expect robots to be like in sci-fi movies, it was very hard to convince the customers or people to understand reality.

With all these inputs we are good to start with the prototype. Now we chose a material that was easy to bend and cut, so we chose PVC foam. **Initial prototype took 3 months to have a structure and make the robot move.**

### **Challenges we faced in this version was.**

1. Maintaining the center of gravity
2. Controlling the robot with a remote
3. Making the robot to move straight.
4. Choosing the right batteries and motors.

![/media/Screenshot_2020-01-20_at_4.44.42_PM.png](/media/Screenshot_2020-01-20_at_4.44.42_PM.png)

Initial days of working

![/media/Screenshot_2020-01-20_at_4.45.08_PM.png](/media/Screenshot_2020-01-20_at_4.45.08_PM.png)

Mitra - made of PVC foam

5. Attaining 3 degrees of freedom

6. Giving express to the eyes.

**Limitations was**

1. It couldn't do the 360-degree movement
2. Noisy movements.

> Second prototype was mostly to add more software & 360-degree movement.

In this, we had multiple software stacks.

1. ATMEL chips for controlling the motors
2. Raspberry PIs for processing
    1. Face detection using OPEN-CV using an external camera.
    2. Speech recognition using CMU sphinx using an external mic.
    3. Bluetooth communication from the processor to the controller.
    4. Basic NLP transforming text to logical commands. 
    5. Used python and C++.

  3. Battery powered and backup was up to 2 hours.

![/media/36540952551_a2f83d0cd8_w.jpg](/media/36540952551_a2f83d0cd8_w.jpg)

With different heights

The most highlighted point of this version was controlling the movements through the voice .

We were part of the global entrepreneur summit in November 2017

It was our prestigious moment were got the opportunity to  meet our prime minister and Ivanka Trump and the robot was launched by the dignitaries

> Now the robots can move autonomously in this version

 We can’t call it has a full-functioned robot until it is moved autonomously. This was the most challenging task for us, we took the textbook solution of doing a triangulation and move the robot autonomously. But it was never simple like this, we used ultrasonics beacons for triangulation and compass for the direction. The compass was giving lots of issues in the real world due to magnetic interference, we did magnetic shielding to overcome this issue.

![/media/1511885542-6185.jpg](/media/1511885542-6185.jpg)

[At GES 2017](https://www.youtube.com/watch?v=ufPJNI58HSQ)

> Now its time to make the robot more intelligent and aware.

By the Start of 2018, we moved away from the prototyping stage and started to standardized our product as follows

1. Improve the speech and the NLP along with multiple language support.
2. Improve computer vision
3. Doing machine learning in the cloud
4. Control the robot from the cloud
5. Using SLAM along with ROS combined with help of LIDAR by replacing the beacon-based navigation.

By mid of 2018, we were able to sell the robots to the customer and started to become a profitable company with 25 employees.

### Creating a mold for Mitra

To create the mold we had to some crazy pieces of stuff, we have to study how the car companies do their mold. We found out that clay modeling was used to make the mold. Then we have to design the structure of the robot in the clay and the take the mold out of this and make it production-ready and scale the production process

![/media/25739480877_02f70c12ac_c.jpg](/media/25739480877_02f70c12ac_c.jpg)

Clay modeling to make the mold

![/media/38800275660_a26675d3c9_c.jpg](/media/38800275660_a26675d3c9_c.jpg)

Structure out of the mold
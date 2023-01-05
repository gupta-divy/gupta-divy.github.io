---
title:  "Chitrak-Quadruped Robot"
layout: post
---

Quadrupeds, in general legged robots are superior to wheeled robots in terms of traverisng complex terrains with potential applications in space Exploration, caves / mine inspection, construction sites, etc. However, compared to wheeled robots they are much less efficient with same form-factor. 

## How we approached this problem?
Imagine yourself standing for 1hr, your legs will start hurting gradually. Though theoretically you are not moving but to maintain your stance your muscles are actively working. Similar thing happens with legged robots; to keep their stance joint motor needs to apply continuous torque (thus continuous current consumption). One simple solution for this could be - designing a controller that employs static equillibrium when not moving. However, with sensor noise, design constraints and external disturbances achieving this could be a little challenging.

In this project, we used self-locking actuators at each joint (2 dof for each leg) that ensures static state at all angles.

## Individual Contribution:
<img align="left" width="200" height="100" src="/assets/Chitrak_Iteration_1.png" style="padding-right: 15px;">

<img align="right" width="200" height="100" src="/assets/Chitrak_Iteration_2.png" style="padding-right: 15px;">

We worked on this project during my pre-final year at IIT Roorkee as part of [Models and Robotics Section, IIT-R](https://mars.iitr.ac.in/), which is a student led robotics group. I worked on the design and kinematic simulation of first two iterations of the robot. This project was selected for Engineers Conclave (Student led undergraduate projects) to represent college in InterIIT-Tech Meet 2019. 

{% include embed.html url="https://youtu.be/embed/_hBBhkbbs5qY" %}

{% include embed.html url="https://youtu.be/embed/_Yxk5NU94QKA" %}
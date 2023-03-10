---
title:  "Chitrak-Quadruped Robot"
layout: post
---

Quadrupeds, in general legged robots are superior to wheeled robots in terms of traverisng complex terrains with potential applications in space Exploration, caves / mine inspection, construction sites, etc. However, compared to wheeled robots they are much less efficient with same form-factor. 



## How we approached this problem?
Imagine yourself standing for 1hr, your legs will start hurting gradually. Though theoretically you are not moving but to maintain your stance your muscles are actively working. Similar thing happens with legged robots; to keep their stance joint motor needs to apply continuous torque (thus continuous current consumption). One simple solution for this could be - designing a controller that employs static equillibrium when not moving. However, with sensor noise, design constraints and external disturbances achieving this could be a little challenging.

In this project, we used self-locking actuators at each joint (2 dof for each leg) that ensures static state at all angles.

## Individual Contribution:
<img align="left" width="320px" height="100px" src="/assets/Chitrak_Iteration_1.png" style="padding-right: 15px;">

<img width="320px" height="100px" src="/assets/Chitrak_Iteration_2.png" style="padding-left: 15px;">

I worked on this project during my pre-final year at IIT Roorkee as part of [Models and Robotics Section, IIT-R](https://mars.iitr.ac.in/), which is a student led robotics group. In this project, I worked on the design and kinematic simulation of first two iterations of the robot. This project was selected for Engineers Conclave (among Student-led projects category) to represent college in InterIIT-Tech Meet 2019.

## Check out our project videos:

{% include embed.html url="https://www.youtube.com/embed/hBBhkbbs5qY" %}

{% include embed.html url="https://www.youtube.com/embed/Yxk5NU94QKA" %}


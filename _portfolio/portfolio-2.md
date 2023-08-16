---
title: "Chitrak-Quadruped"
excerpt: "To improve efficiency of a legged robot, in particular quadruped we ideated with using self-locking actuators for each joint to achieve static stability.<br/><img src='/images/Chitrak_Iteration_1.png' width="240" height="100">"
collection: portfolio
---
Quadrupeds and legged robots have gained significant attention in the field of robotics due to their ability to traverse complex terrains. This characteristic makes them particularly advantageous for various applications, including space exploration, caves/mine inspection, and construction sites. Although legged robots offer superior maneuverability over wheeled robots in these challenging environments, they typically exhibit lower efficiency when considering the same form factor. 


## Defining the Problem
Imagine yourself standing for 1hr, your legs will start hurting gradually. Though theoretically you are not moving but to maintain your stance your muscles are actively working. Similar thing happens with legged robots; to keep their stance joint motor needs to apply continuous torque (thus continuous current consumption). One simple solution for this could be - designing a controller that employs static equillibrium when not moving. However, with sensor noise, design constraints and external disturbances achieving this could be challenging.

In this project, we used self-locking actuators at each joint (2 dof for each leg) that ensures static balance when stationary. Though using self-locking actuators enabled us to achieve static balance, these actuators lacks the bandwidth to support dynamic response required for walking with legged system.

## Design and Prototype:
<img align="left" width="320px" height="100px" src="/images/Chitrak_Iteration_1.png" style="padding-right: 15px;">

<img width="320px" height="100px" src="/images/Chitrak_Iteration_2.png" style="padding-left: 15px;">

I worked on this project during my pre-final year at IIT Roorkee as part of [Models and Robotics Section, IIT-R](https://mars.iitr.ac.in/), which is a student led robotics group. In this project, I contributed for the design and prototype of first two iterations of the robot. In addition to the mechanical design, I designed and simulated Bezier curve based foot trajectory along with implementation of position controller to track foot trajectory. This project was selected for Engineers Conclave (among Student-led projects category) to represent college in InterIIT-Tech Meet 2019.

## Check out our project videos:

{% include embed.html url="https://www.youtube.com/embed/hBBhkbbs5qY" %}

{% include embed.html url="https://www.youtube.com/embed/Yxk5NU94QKA" %}
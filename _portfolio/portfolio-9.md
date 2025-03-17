---
title: "PredicKOA - Low-cost inertial motion capture system"
excerpt: "Built a device / methodology to predict the onset and track the progress of Knee Osteoarthritis in elderly using wireless low-cost inertial sensors. Skills: C, Sensor System IMUs, Microcontroller programming, Circuit Design, Signal Processing, Machine Learning (SVM), Motion Capture" 
collection: portfolio
---
PredicKOA or Predicting Knee Osteoarthritis was my undergraduate thesis project at IIT Roorkee. The goal of the project was to build a device / methodology to predict the onset and track the progress of Knee Osteoarthritis in elderly using wireless low-cost inertial sensors. This project was inspired by lack of Motion capture technology and the skillset required to operate them in budget contrained settings with poor healthcare infrastructure- rural areas, developing countries, etc. Additionally, it can help in better identifying new bio-markers for diseases affecting the muskuloskeletal system with motion data from users in their natural work / home setting. Furthermore, application of this could be extended to track progress of other physio / neurological diseases affecting mobility especially in elderly.



## So, how it works?
![PredicKOA working](/images/p9_predicKOA_process.jpg)

### Prototype
Hardware setup included 7-modules for data-collection placed on lower-body(Lower-back, Thigh, Shank and Ankle) and each module used a NodeMCU(ESP8266), low-cost Wi-Fi enabled microcontroller and a MPU9250, 9DoF inertial sensors. UI interface developed using MATLAB was used to send triggers over Wi-Fi for data-collection and system was hardcoded to trigger with different delays to enable approximate synchronization of data from each module. The raw inertial data (Gyroscope, accelerometer and magnetometer) collected by these modules is transferred to the system over Wi-Fi which is pre-processed using Kalman Filter to generate and store orientation data for each IMU sensor or attached body part.

### Estimating Gait features and Joint Kinematics:
Gait features includes walking speed, stride time, and others like initial and final foot contact. These features are usually affected by neuro-muskuloskeletal diseases; Eg. Imagine yourself walking when you are mentally exhausted vs when you are energized, this is the effect of neurological factors on your gait pattern. There are multiple ways to estimate these parameters and for this project I used vertical acceleration data from IMU placed at lower-back with [GaitPy algorithm](https://pypi.org/project/gaitpy/) by Matthew Czech to extract these features. Further, joint angles were calculated using [OpenSense (OpenSim)](https://simtk.org/projects/opensense) which takes in orientation data of IMUs and estimate joint kinematics.

### Predicting Knee Osteoarthritis (KOA)
Estimated gait features and joint angles (kinematics) acts as bio-markers as they changes with progressing knee osteoarthritis. Some of these bio-markers includes decrease in range of motion for Knee Flexion and Hip Flexion, decrease in Peak Flexion angle at Heel Strike and Midswing, increased double support time, etc.  Support Vector Machine or other Neural-net classification models could be trained to predict KOA progress with accuracy.
![Gait features affected by KOA](/images/p9_predicKOA_features.png)


## Conclusion
Project was not concluded and was hindered by COVID-19 (2020, received A+ for progress). However, this project gave me a deeper understanding on science of bipedal walking and other biomechanical concepts.
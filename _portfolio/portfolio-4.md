---
title: "Robot Sensing and Navigation"
excerpt: "We have examined the sensors and mathematical techniques for robotic sensing and navigation with a focus on sensors such as cameras, GPS, IMUs, and laser scanners.<br/><img src='/images/RSN_DataCollection.png'>"
collection: portfolio
---
This work is part of EECE5554 course at Northeastern University. In this course, we examined the actual sensors and mathematical techniques for robotic sensing and navigation with a focus on sensors such as cameras, sonars, and laser scanners. These are used in association with techniques and algorithms for dead reckoning and visual inertial odometry in conjunction with GPS and inertial measurement units. A large component of the class involved programming in both the ROS and MATLAB environments with real field robotics sensor data sets. Individual sub-projects includes writing drivers for different sensors and analysis scripts for the collected data. 



## Project Descriptions [(Github)](https://github.com/gupta-divy/Robot-Sensing-and-Navigation)

### GPS [(Details)](https://github.com/gupta-divy/Robot-Sensing-and-Navigation/blob/main/GPS/src/report.pdf)
In this lab we worked with USB-based GPS module (BU-353S4), where we collected and analyzed data in stationary and moving conditions to understand the working principle of GPS and factors affecting accuracy of the module. Key insight: GPS module works better in moving condition compared to stationary.


### RTK-GPS [(Details)](https://github.com/gupta-divy/Robot-Sensing-and-Navigation/blob/main/RTK-GPS/src/report.pdf)
In this lab we worked with RTK_GPS setup using ArduSimple RTK2B-F9P kit, where we setup our own base-station and RF based communication with the GPS module. We collected and analyzed data from different environments (Occluded and Open-field) and conditions (Moving and stationary) to understand the advantages of RTK based setup on the accuracy and precision of GPS. To collect the data, our driver is similar to driver from GPS module, with few additional field published on /gps topic: Fix_quality. Key insight: RTK_setup significantly improved precision from 1.25m GPS to 0.5m RTK_GPS in case of moving condition.

### IMU-Noise Analysis [(Details)](https://github.com/gupta-divy/Robot-Sensing-and-Navigation/blob/main/IMU-Noise%20Analysis/src/report.pdf)
In this lab we collected and analyzed IMU-sensor (VectorNAV-100) data to understand the different noise characteristics present in Gyroscope and Accelerometer data using [Allan Variance analysis](https://www.mathworks.com/help/nav/ug/inertial-sensor-noise-analysis-using-allan-variance.html) on a 5hr stationary dataset collected in the basement of a parking lot. Further, we modeled an IMU with these noise characteristics in MATLAB to understand its implications in the sensor selection process for different applications. Also, we analyzed the performance of a stationary inertial sensor using different statistical tools to visualize the error distribution of Gyroscope, Accelerometer and Magnetometer. 

### Dead-Reckoning [(Details)](https://github.com/gupta-divy/Robot-Sensing-and-Navigation/blob/main/Dead-Reckoning/src/report.pdf)
In this lab, we collected inertial and gps data using [NUance car](https://fieldroboticslab.ece.northeastern.edu/autonomous-car/), Northeastern's autonomous car. Collected data includes two datasets - Magnetometer_calb (To remove soft-and-hard iron-bias from Mag data) and moving_data. To collect data, we are using the driver files from GPS and IMU module. For analysis, we performed dead-reckoning using a complementary filter with Gyroscope and Magenetometer and compared it with GPS trajectory. Key Insight: Small drfit-bias in Gyro significantly impacts the estimated trajectory, when we trust measurements of Gyroscope more than Magnetometer in complementary filter. 

### Image-Stitching [(Details)](https://github.com/gupta-divy/Robot-Sensing-and-Navigation/blob/main/Image-Stitching/report.pdf)
In this lab, we used CALTECH camera toolbox to calibrate the phone camera, and generated panaroma of these calibrated images from different scenes and overlapping. We worked with harris-corner detector and and iterated with different parameters to generate the panaroma for a set of images. MATLAB script is based on [MATLAB Photomosaicing](https://www.mathworks.com/help/vision/ug/feature-based-panoramic-image-stitching.html?searchHighlight=panorama&s_tid=doc_srchtitle).

### SLAM-VSLAM [(Details)](https://github.com/gupta-divy/Robot-Sensing-and-Navigation/blob/main/SLAM-VSLAM/src/analysis/report_TBD.pdf)
This was a group project (3-weeks), where we implemented different SLAM (HDL-GraphSLAM and LEGO-LOAM) and VSLAM (RTABMAP and ORB SLAM3) algorithms on KITTI-dataset and further used YOLO to detect traffic-signs and map them on the 2D trajectory. Real-world constraints in terms of cost, accuracy, computation, power and ease of integration limits the use of sensors and algorithm configuration, so as part of this project we tried to understand the implementation challenges of each algorithms along with their benefits. Further, we tried to address the issue of road-safety for autonomous vehicles which can leverage on the semantic information like traffic signs (speed limit, school signs, etc.) to improve on safety of passengers and pedestrians. 
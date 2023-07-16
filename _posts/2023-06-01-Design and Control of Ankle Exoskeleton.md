---
title:  "Design and ML-based Control of Ankle Exoskeleton"
layout: post
---
<img align="left" width="200" height="250" src="/assets/AnkleExo_CAD.png" style="padding-right: 15px; padding-bottom: 15px;">
Deteriorating muscles among elderly leads to reduced mobility and independance. And with ankle joint muscle group contributing to ~42% of positive work during walking, ankle exoskeletons have the potential to significantly improve the restricted mobility among elderly. In recent times, there has been increased push in this field of exoskeletons, however there is ample room for improvementin terms of both Design and Control. 

In this project, I am working on making the ankle exoskeleton lighter and compliant to augment natural joint movement instead of restricting it. Along with improved design, I am working incorporating data-driven methods to provide assistance in natural ambulating environments which continuously varies and requires walking with different speeds, climbing steps, taking-turns, etc.



## Design and Prototype
Design of the ankle-exoskeleton incorporates several key-features aimed at providing optimal assistance and adaptability to different users. One key aspect is its unidirectional series elastic actuation system, capable of delivering an assistive platarflexion torque of upto 60Nm (~40% of ankle joint torque among healthy adults). In addition to this, this device uniquely leverages material compliancy to allow inversion-eversion of foot, which is absent in most available ankle-exoskeletons. 

Additionally, another important design constraint for the ankle exoskeleton is to reduce distal mass which tends to reduce augmentation factor of the exoskeleton. ([Augmentation Factor](https://jneuroengrehab.biomedcentral.com/articles/10.1186/1743-0003-11-80) – It is a mathematical model developed to predict the metabolic impact of untested exoskeletons at moderate walking speeds. Positive AF suggests metabolic improvement and vice versa). The model was optimized to minimize weight (~1050gm/leg including electronics) while maintaining the required structural integrity. 

Overall, the ankle exoskeleton's design incorporates the design constraints based on previous research in the field, while adding new novelties - Compliancy and Series elastic-actuation.

![Ankle Exoskeleton Designs](/assets/AnkleExo_Designs.png)


## Controller Design
Current lower-limb wearable devices like exoskeletons and prosthetics are limited to lab-settings because of their inability to work in natural environments. To enable their use among healthy populations, it becomes necessary to have a control policy that supports multimodal ambulation (e.g., different walking speeds, running, inclined walks, jumping, etc.). 

In most available wearable devices, a three-level control system is often employed, consisting of high-level, mid-level, and low-level controllers. The high-level controller functions as a classifier to determine the ambulation mode. Subsequently, the mid-level controller generates a reference assistance trajectory for the classified mode, and the low-level controller is responsible for tracking this trajectory. This control system hierarchy enables efficient and accurate control of wearable devices in continuous ambulation mode with finite switching modes. However, this high-level control policy may not be suitable in natural settings where ambulation modes are not steady-state modes and cannot be discretized. 

To overcome this limitation, I am developing a subject and task-agnostic controller that uses deep-learning model on wearable sensor data to predict biological torque which can be directly mapped to assistive torque. IMU, goniometer, and pressure insole data (19 features) from 3 subjects across five different tasks are used to train traditional deep-learning  models, including fully-connected neural networks (FCNN), long short-term memory (LSTM) networks, and temporal convolution neural (TCN) networks. The trained model in then evaluated on an unseen subject in training across 22 hold-out tasks (untrained tasks). This approach resulted in an average RMSE of 0.056 Nm/Kg in predicting biological torque for walking at average speed (~3-4% of peak torque value). 

![RMSE across different tasks](/assets/AnkleExo_taskRMSE.png)
<center>RMSE on 22 hold-out tasks for FCNN, LSTM and TCN Model</center>

![Torque prediction for normal-walking](/assets/AnkleExo_walkRMSE.png)
<center>Biological torque profile for normal walking at average walking speed</center>

To learn more on ML-Controller - [Read here](https://github.com/gupta-divy/Exo-controller-ML/blob/main/Project_report.pdf)

## Ongoing work
Currently working on improving the design and integrating the controller. Also, on controller side, I am working on hyperparameter tuning of the NN using Bayesian Optimization.
---
title: "Design and Control of Ankle Exoskeleton"
excerpt: "Built an Ankle Exoskeleton which is lighter, have passive compliance to allow natural joint movement and features novel actuator for near zero-impedance for backdrivability"
collection: portfolio
---
<img align="left" width="200" height="250" src="/images/Intro_Exo.jpg" style="padding-right: 15px; padding-bottom: 15px;">
Deteriorating muscles among elderly leads to reduced mobility and independance. And with ankle joint muscle group contributing to ~42% of positive work during walking, ankle exoskeletons have the potential to significantly improve the restricted mobility among elderly. In recent times, there has been increased push in this field of exoskeletons, however there is ample room for improvement in terms of both Design and Control. 

In this project, I worked on making the ankle exoskeleton lighter and add passive compliance to allow natural joint movement instead of restricting it. Further, novel [actuator mechanism](https://gupta-divy.github.io/portfolio/portfolio-1/) is used to achieve smooth transition across different gait phases - swing and stance. Along with improved design, I tested conventional heirarichal state-machine control design and also, data-driven approach to provide assistance outside lab settings irrespective of task performed.

## Design and Prototype
<img align="left" width="200" height="250" src="/images/p2_ankleExo_forces.jpg" style="padding-right: 15px; padding-bottom: 15px;">
Design of the ankle-exoskeleton incorporates several key-features aimed at providing optimal assistance and adaptability to different users. 
- Unidirectional series elastic actuation system, capable of delivering an assistive platarflexion torque of upto 50Nm (~40% of ankle joint torque among healthy adults) allowing for unimpeded backdrivability
- Passive material compliancy to allow inversion-eversion and rotation of foot about ankle joint, which is absent in most available ankle-exoskeletons 

Additionally, another design constraint considered around the design was to reduce distal mass which tends to reduce augmentation factor of the exoskeleton. ([Augmentation Factor](https://jneuroengrehab.biomedcentral.com/articles/10.1186/1743-0003-11-80) – It is a mathematical model developed to predict the metabolic impact of untested exoskeletons at moderate walking speeds. Positive AF suggests metabolic improvement and vice versa). The model was optimized to minimize weight (~1050gm/leg including electronics) while maintaining the required structural integrity. 

<img src="/images/p2_AnkleExo_Designs.png" alt="Design Iteration 1" style="display: block; margin: 15px auto; width: 80%; height: auto;">
<center>Design Iteration 1 with Geometric series elastic spring</center>

<img src="/images/p2_AnkleExo_Designs2.jpg" alt="Design Iteration 2" style="display: block; margin: 15px auto; width: 80%; height: auto;">
<center>Design Iteration 2 with Novel spring mechanism for series elasticity</center>

## Controller Design 
Traditionally, control architecture in exoskeletons follow a heirarichal state machine architecture. Top-level controller is a state machine that employs different mid-level controller based on tasks / activities (running walking, jumping, etc.) and time into that activity (for walking, gait phase). Mid-level controller applies different control strategy for each state-machine combination suggested by top-level controller. And finally low-level controller often employed by the motor controller itself - tracks the desired control command by mid-level controller (torque, position command). However, in a natural setting, having a heirarichal state machine architecture doesn't work as there are infinite state combinations - depedent on walking speed, ground incline, user-action, etc. Data-driven methods merge the top-level and mid-level controller, where direct torque value is commanded based on time history of sensor values.

In the following section, traditional control method is discussed focused only on walking and the data-driven approach is discussed in another article, [here](/_portfolio/portfolio-3.md). 

### High-Level Controller: Time based-gait phase estimator 
<img align="left" width="100" height="150" src="/images/p1_torque_conversion.png" style="padding-right: 15px; padding-bottom: 15px;">
The system employs an Inertial Measurement Unit (IMU) to identify heel strikes during walking, detected as peaks in the gyroscope signal corresponding to rapid changes in angular velocity. Following the detection of each heel strike, a time-based estimator calculates the stride duration by measuring the time interval between two consecutive heel strikes. The average of the stride durations over the last three steps is then used to predict the timing of the upcoming gait phases.

\[
GaitPhase(\%) = \frac{t-t_{LastHeelStrike}}{T}
\]
here, $T$ is average time period of last three strides

### Mid-Level Controllers:
<img src="/images/p2_fourPointSpline.jpg" alt="Four Point Spline" style="display: block; margin: 15px auto; width: 60%; height: auto;">
<center>Stance Controller: Four Point Spline [ref](https://www.science.org/doi/10.1126/science.aal5054) </center> 

**Stance Controller (Open-Loop Torque Control)**
During the stance phase, which spans 0–62\% of the gait cycle, the controller operates in an open-loop torque control mode using predefined torque spline curves that mimic the biological torque profile of the ankle joint. The torque curve is defined by a 4-point spline that governs four key parameters of the torque profile: rise time, peak time, peak assistive torque, and fall time. Based on insights from the literature, these parameters are tuned and optimized to maximize reductions in metabolic cost.

**Swing Controller (Track CAM Angle)**
The swing phase, covering 62–100\% of the gait cycle, focuses on maintaining a low tension in the cable to minimize interaction with the user. Studies suggest that disengaging the user from the actuator dynamics during this phase enhances natural foot motion and user comfort. The CAM-based spring design in the system achieves this by tracking a pre-set CAM angle, thus achieving desired low-tension in cable —sufficient to prevent slack without introducing resistance. This ensures the actuator remains transparent during the swing phase, facilitating unimpeded user motion.

**Swing-to-Stance Transition (Reel-In Controller)**
During the transition from swing to stance, the controller utilizes a reel-in strategy to adjust cable tension smoothly via velocity control. This process begins at t-heel strike - 0.2 seconds (heel strike minus 0.2 seconds) and commands a constant reel-in velocity until a predefined torque threshold is reached. This ensures a smooth engagement of the actuator without sudden jerks, allowing the torque profile to seamlessly take over as the stance phase begins.

**Stance-to-Swing Transition (Reel-Out Controller)**
The transition from stance to swing employs a reel-out strategy designed to gradually reduce cable tension. This is achieved using a reel-out velocity until the actuator is in low-force regime and then switches to CAM angle tracking, effectively achieving low tension in the cable as the system disengages. By ensuring a smooth reduction in tension, the reel-out strategy prevents any unwanted torque application during the swing phase, maintaining transparency and enhancing user comfort.

---
Traditional controller strategy works well on level-ground walking in a range of speeds however, it fails as we starts deviating from the same - either incline (gait phase detection fails, heel strike time affected due to incline) or running (gait phase for gait cycle changes) or some other non-cyclic tasks. 
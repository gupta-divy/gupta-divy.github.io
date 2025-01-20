---
title: "Design and Control of Non-Linear Series Elastic Actuator (SEA) - Cable Drive"
excerpt: "A novel series elastic actuator design with a cable-driven system that achieves precise force control over a wide range [1–200N] through a mechanically programmable stiffness using CAM"
collection: portfolio
---

<img align="left" width="200" height="250" src="/images/p1_actuator_schematic.png" style="padding-right: 15px; padding-bottom: 5px;">

Unidirectional cable-drive actuators are excellent for applications requiring high force with minimal resistance to back-driving. However, they face challenges when it comes to precise force control, especially in low-force regions.

This happens because high-torque motors struggle with rotor inertia, which reduces their sensitivity to small force changes. For wearable robotics, there’s also an added issue: sudden jerks when transitioning between Slack and Taut cable states. \
\



## A Promising Solution: Series Elastic Actuator (SEA)

One promising solution is a **Series Elastic Actuator (SEA)**. By adding a spring element in series with the transmission, we can dampen the jerks and simplify low-force tracking by converting it into a position control problem. 

However, traditional SEAs often fall short due to the reliance on linear springs, which create a trade-off:
- A soft spring is good for low forces but limits the actuator’s overall force capacity.
- A stiff spring allows high-force applications but sacrifices low-force sensitivity.

<div style="display: flex; justify-content: space-around; align-items: center; margin: 15px 0;">
    <img src="/images/p1_springStiffness.png" alt="Spring Stiffness" style="width: 45%; height: auto;">
    <img src="/images/p1_actuator_design.png" alt="Actuator Design" style="width: 45%; height: auto;">
</div>

This project solves these issues with a **non-linear SEA** using a **CAM-based spring mechanism**. The non-linear spring allows mechanical programming of the stiffness, making it adaptable for different needs. 

At low forces, the actuator acts like a soft spring, maintaining tension to avoid slack. As forces increase, the stiffness gradually ramps up, eventually disengaging the spring to behave like a traditional cable-driven system. 

### Key Benefits:
- Achieves both high-force capability and excellent low-force sensitivity.
- The CAM-based mechanism is tunable for diverse applications, such as delicate handling (e.g., picking a strawberry) and lifting heavy objects.


## Design and Prototype

<img align="left" width="150" height="200" src="/images/p1_torque_conversion.png" style="padding-right: 15px; padding-bottom: 15px;">

The actuator combines a **CAM-based spring mechanism** with a kinematic pulley arrangement to achieve a tailored stiffness profile. The reasoning for pulley configuration is based off the need to have very-low stiffness requiring large deflections. Further, adjustments to the CAM shape and pulley configuration enable customization for specific applications. Thus, allowing user to mechanically program the non-linear stiffness curve for various applications. This current design was optimized for use with an ankle exoskeleton, where a near zero stiffness is desired during swing phase of walking and high stiffness during stance phase, with a smooth transition in between.


### Key Features:

1. **Two Force Modes**:
    - **Low-force mode**: The spring is engaged, providing very low stiffness to maintain tension even with large deflections.
    - **High-force mode**: The spring disengages, and the actuator functions as a traditional cable-driven system.

2. **Customizable Force-Displacement Curve**:
    - The force-displacement relationship can be fine-tuned for specific tasks, balancing low-force control and applying high-force values.


## Hardware Used

<img src="/images/p1_hardwareUsed.jpg" alt="Hardware Used" style="display: block; margin: 15px auto; width: 60%; height: auto;">

**Motor**: CubeMars AKE60-8
**Motor Controller**: Odrive Pro, Transitioning to Moteus for its open-source firmware
**Compute**: Jetson Nano Orin, supporting ML-based controllers for exoskeleton application
**Sensors**: Two Encoders, MA600,  one for the CAM Angle and another for the motor shaft and an IMU BNO085 for application with exoskeleton (Currently adding IMU support to Moteus firmware).


## Controller Design
<img src="/images/p1_control_system.png" alt="Control System" style="display: block; margin: 15px auto; width: 90%; height: auto;">
The actuator features broadly 2 control behavior - low-force and high-force modes, which are controlled by finite state-machine architecture, with different control strategies for each:

**Low-Force Mode**: Cascaded **PD controller** with gains fine-tuned for fast response and disturbance rejection. The loop is closed around cam angle error for which PD controller outputs the velocity command which is tracked by low-level controller within motor-controller.

**High-Force Mode**: In high-force region, the current feedback in motor is sufficient to accurately track the cable force values / motor torque. Thus, internal low-level controller works well for stability in high-force mode.

**Transition**: For transition between the two regions low-level velocity controller is used with ramped velocity trajectory to avoid abrupt changes.

This hybrid strategy ensures precise force tracking across the actuator's entire operating range 1-200N.

<div style="display: flex; justify-content: space-around; align-items: center; margin: 15px 0;">
    <img src="/images/p1_actuator_setup.png" alt="Actuator Setup" style="width: 45%; height: auto;">
    <img src="/images/p1_step_response.png" alt="Step Response" style="width: 45%; height: auto;">
</div>

---

This innovative SEA design bridges the gap between low-force sensitivity and high-force capability, making it a versatile solution for applications ranging from wearable robotics to industrial grippers. 

[Published MS Thesis](https://www.proquest.com/docview/3147874129) Non-linear series elastic cable drive actuator - Design and Controls (Patent Pending: US Patent 18/911616)

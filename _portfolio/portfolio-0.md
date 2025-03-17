---
title: "Manipulator Control - Task and Motion Planning Algorithm"
excerpt: "Self-learning project in which I'm building the task and motion planning (TAMP) pipeline for pick n place task in cluttered environments. Skills: C++, MuJoCo, Motion Planning, Behavior Trees, Manipulator Kinematics, Optimization, Reinforcement Learning, URDF Files"
collection: portfolio
---
External Links: [Code-GitHub](https://github.com/gupta-divy/SelfLearning/tree/main/manipulator_controls), [Reinforcement Learning project Report](https://github.com/gupta-divy/SelfLearning/blob/main/CS5180_RL_Final_Project-1.pdf)
In this project, I'm developing a **Task and Motion Planning (TAMP) pipeline** for a **UR5 robot** to perform pick-and-place tasks in cluttered environments. The goal is to create a modular, code pipeline 
that integrates **task execution, motion planning, and inverse kinematics**, all within the **MuJoCo** simulation framework.

Since it's a self-learning project, the code is very modular to test and switch different algorithms for different parts of the pipeline with ease.

<div style="display: flex; justify-content: space-around; align-items: center; margin: 15px 0;">
    <img src="/images/p0_ur5_setup.jpg" alt="UR5 Setup - MuJoCo" style="width: 45%; height: auto;">
    <img src="/images/p0_pusher_setup.jpg" alt="Pusher-v2 Gym Environment" style="width: 45%; height: auto;">
</div>

## Task Execution with Behavior Trees

To break down high-level tasks efficiently, I'm implementing a **Behavior Tree (BT)** framework. This modular approach helps the robot:
- Decompose complex tasks into smaller, reusable sub-tasks.
- Seamlessly integrate perception, planning, and control.

## Motion Planning: RRT and Custom Algorithms
For motion planning, I've implemented **Rapidly-exploring Random Trees (RRT)** from scratch while exploring alternative approaches. My key focus areas include:
- Code Modularity for path planning in both C-space and Task space
- Experimenting with **RRT***, **PRM** and other sampling based approaches to improve path quality and estimation time
- Experimenting different sampling strategies for improving prediction time - goal bias, ellipsoid region, etc.

Additionally, I've added **spline based trajectory generation methods** to smoothen out the generated path

## Inverse Kinematics: Testing Different Approaches
For application with pick n place, and other tasks, I'm exploring various **Inverse Kinematics (IK)** methods for converting between task-space and C-space, including:
- Jacobian-based methods including Pseudo Inverse (numerical approach for iterative solutions)
- Analytical solutions using Pinnochio library (for simpler kinematic configurations)
- Optimization-based solvers - utilizing Scipy library

The simulation setup consists of:
- A **UR5 robot model** with realistic kinematics and dynamics
- **Obstacle-rich environments** for motion planning robustness testing
- **Sensor integration** with noise to mimic challenges with real hardware

## Related Project: Reinforcement Learning for Dynamic Obstacle Avoidance
In a separate project, I explored **Reinforcement Learning (RL) algorithms** for dynamic obstacle avoidance in a **push-and-place task**. This involved modifying the **Pusher-v2 environment** to introduce dynamic obstacles representing human interactions.

### Enhancements to the Environment
- **Modified Pusher-v4 Model**: A two-link manipulator with 7 DoF, adjusted joint limits, and refined contact dynamics
- **Obstacle Representation**: Spherical objects mimicking human arms, capable of moving along X, Y, and Z axes with added damping
- **Expanded State Space**: Included obstacle positions, safety margins, and contact information to improve obstacle awareness
- **Updated Reward Function**: Introduced penalties for safety margin breaches and impacts, enforcing safe interactions with obstacles

### RL Algorithms Tested
- **Proximal Policy Optimization (PPO)**: Tuned clip range and incorporated State Dependent Exploration (SDE) for improved stability
- **Deep Deterministic Policy Gradient (DDPG)**: Adjusted action noise parameters and integrated SDE-based exploration
- **Soft Actor-Critic (SAC)**: Optimized entropy coefficients and action noise distributions for robust exploration

### Key Results
- Enhanced real-time obstacle avoidance
- Improved adaptability to changes in object and goal positions
- Found **SAC** to be the most robust among the tested algorithms
 
This project highlights the integration of **safety constraints, RL-based learning, and task adaptability**, contributing to real-world human-safe robotic applications.



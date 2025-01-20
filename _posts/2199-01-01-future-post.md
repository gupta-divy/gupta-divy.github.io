---
title: 'Reinforcement Learning: Finite Markov Decision Process (MDP)'
date: 2199-01-01
permalink: /posts/blog-post-2/
tags:
  - cool posts
  - category1
  - category2
---

## Introduction



## Examples, Tasks that fit into MDP Framework
- Legged robot: Consider applying a RL to control the motion of a biped robot. In this case, actions can be current input at each actuator on the biped and the states can be joint angles and velocities. The goal of our control policy is to make sure the robot doesn't fall and move forward. So the reward, can be position of COM of the robot.
- Plastic decomposing chemical composition: Applying RL-policy to generate chemical composition that can break the hydrocarbon chain in plastics. Actions can be attaching an element to a base molecule, and the states can be toxicity, stability and reactivity with plastic. The goal of this is to decompose plastic into non-polluting compounds, so reward can be positive values for non-polluting compounds and vice-versa.
- Controlling rocket to avoid space-debris: The goal is to cross a space debris while taking minimum damage. In this case, actions can be thrusters angle and force, and states can be rocket health, fuel levels, velocity and accelerations. The reward can be positive for ditance traversed and negative rewards for each hit.

Though, MDP framework is flexible enough to accomodate all goal-directed learning tasks, but I believe it can't be used to create artforms like painting and music. Since art is subjective, it is impossible to estimate or assign a reward for any iteration, without feedback from a human.

## Equations that explains the Dynamics of MDP

Probability of being in state St = s' and have reward Rt = r, given previous state St-1 and action taken in that state At-1 = a is defined by function p and is fundamental dynamics of the MDP that completely characterize the environment's dynamics. Note - Probability value of for St and Rt depends only on the immediately preceding state and actions. This can be thought as restriction on the state not on the decision making process. State must follow *Markov Property*, which is defined as the state must include information about all aspects of the past agent-environment interaction that make a difference for the future. 



### 3. **Twist**


### 4. **Wrench**
- Analogous to a twist, but describes forces and torques acting on a rigid body.
- Combines torque $$\tau$$ and force $$f$$:
  $$
  W = \begin{bmatrix}
  \tau \\
  f
  \end{bmatrix}
  $$

---

## Representations

### 1. **Matrix Form of a Twist**
Twists can be expressed as 4x4 matrices:
$$
\hat{\xi} = \begin{bmatrix}
  [\omega] & v \\
  0 & 0
\end{bmatrix}
$$
- $$[\omega]$$: Skew-symmetric matrix of $$\omega$$.

### 2. **Screw Parameters**
- **Axis**: Direction and position of the screw axis.
- **Pitch**: The ratio of translation to rotation (e.g., $$h = \frac{d}{\theta}$$).

---

## Operations

### 1. **Screw Composition**
- You can combine twists or wrenches using linear algebra (e.g., matrix addition, cross products).
- Useful for solving robotic kinematics problems where multiple motions are superimposed.

### 2. **Exponential Map**
- Used to calculate rigid body transformations from a twist.
- Formula: $$T = e^{\hat{\xi} \theta}$$
- Intuition: This maps a twist over a distance (or angle of rotation) $$\theta$$.

### 3. **Reciprocity**
- A twist $$\xi$$ and a wrench $$W$$ are reciprocal if:
  $$
  \xi^T W = 0
  $$
- This property is crucial in force/velocity analysis of mechanisms.

---

## Applications

### 1. **Robot Kinematics**
- **Forward Kinematics**: Use twists to describe joint motions and compute the end-effector pose.
- **Inverse Kinematics**: Solve for joint parameters given a desired end-effector pose.

### 2. **Mechanics**
- Use wrenches to describe forces and torques acting on a rigid body.
- Analyze equilibrium conditions or dynamics of complex systems.

### 3. **Motion Analysis**
- Study the combined translation and rotation of rigid bodies in mechanical or robotic systems.

---

## Notes
- **Visualization**: Think of a corkscrew motion. It’s not just about the shape, but the motion along and around the axis.
- **Matrix Computation**: Efficient software libraries like NumPy or MATLAB simplify the heavy lifting.
- **Connections**: Screw theory is deeply connected to Lie groups and Lie algebras, especially in SE(3) (special Euclidean group).

---

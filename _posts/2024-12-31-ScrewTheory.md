---
title: 'Screw Theory: Modeling Manipulator'
date: 2024-12-31
permalink: /posts/blog-post-2/
tags:
  - Controls, Modeling, Robot
---
Screw theory is a mathematical framework to analyze and describe rigid body motion in 3D space. It elegantly connects the combined linear and rotational motion about same axis observed in a physical screw to rigid body motion. In addition, it gives better physical understanding of singularities compared to DH parametrization where the maths do not perfectly translate to geometric interpretation. In Screw theory, in case of singularities Screw Axis aligns or coincides with each other thus loosing a DOF. 

## Key Concepts 
(In Progress, not compplete)
### 1. **Spatial Velocity or Twist**
A rigid body with Twist $\mathcal{V}_r$ can be thought of as translating at v_r while rotating with angular velocity $\omega_b$ about an axis passing through r.
  $$
  \mathcal{V}_r = \begin{bmatrix} \omega_r \\ v_r \end{bmatrix} \in \mathbb{R}^6
  $$

Changing the reference frame for Twist, can be achieved by using an $[Ad_T]$

Twists can be expressed as 4x4 matrices:
$$
\hat{\mathcal{V}} = \begin{bmatrix}
  [\omega] & v \\
  0 & 0
\end{bmatrix}
$$
here, $[\omega]$: Skew-symmetric  matrix of $$\omega$$

### 2. **Screw Axis (Plücker Line)**
Every rigid body can be realized by a screw motion

## Resources
- Youtube: [Advanced Robotics Control](https://youtu.be/-4pH6BZZKcQ?si=xAhERAdXGIvjHLOL)
- "Modern Robotics" by Lynch and Park (highly recommended for detailed screw theory coverage).

---

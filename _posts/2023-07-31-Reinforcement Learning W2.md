---
title:  "Reinforcement Learning: Finite Markov Decision Process (MDP)"
layout: post
categories: blog
---
## Introduction


## Examples, Tasks that fit into MDP Framework
- Legged robot: Consider applying a RL to control the motion of a biped robot. In this case, actions can be current input at each actuator on the biped and the states can be joint angles and velocities. The goal of our control policy is to make sure the robot doesn't fall and move forward. So the reward, can be position of COM of the robot.
- Plastic decomposing chemical composition: Applying RL-policy to generate chemical composition that can break the hydrocarbon chain in plastics. Actions can be attaching an element to a base molecule, and the states can be toxicity, stability and reactivity with plastic. The goal of this is to decompose plastic into non-polluting compounds, so reward can be positive values for non-polluting compounds and vice-versa.
- Controlling rocket to avoid space-debris: The goal is to cross a space debris while taking minimum damage. In this case, actions can be thrusters angle and force, and states can be rocket health, fuel levels, velocity and accelerations. The reward can be positive for ditance traversed and negative rewards for each hit.

Though, MDP framework is flexible enough to accomodate all goal-directed learning tasks, but I believe it can't be used to create artforms like painting and music. Since art is subjective, it is impossible to estimate or assign a reward for any iteration, without feedback from a human.
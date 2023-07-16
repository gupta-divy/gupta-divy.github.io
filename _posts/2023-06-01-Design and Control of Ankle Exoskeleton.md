---
title:  "Design and ML-based Control of Ankle Exoskeleton"
layout: post
---
<img align="left" width="170" height="220" src="/assets/AnkleExo_CAD.png" style="padding-right: 15px; padding-bottom: 15px;">
Deteriorating muscles among elderly leads to reduced mobility and independance. And with ankle joint muscle group contributing to ~42% of positive work during walking, ankle exoskeletons have the potential to significantly improve the restricted mobility among elderly. In recent times, there has been increased push in this field of exoskeletons, however there is ample room for improvementin terms of both Design and Control. 

In this project, I am working on making the ankle exoskeleton lighter and compliant to augment natural joint movement instead of restricting it. Along with improved design, I am working incorporating data-driven methods to provide assistance in natural ambulating environments which continuously varies and requires walking with different speeds, climbing steps, taking-turns, etc.



## Design and Prototype
In the crutch walking gait cycle, crutch stance phase follows the dynamics of a double inverted pendulum in which crutch acts as Link1 and our body acts as Link2. Leveraging this dynamics and providing a rigid support to the body at pelvis for swinging at the end of link2, enabled load transfer.

![Crutch walking cycle](/assets/Crutch_cycle.png)
![Crutch working](/assets/Crutch_working.png)

## Outcome
We iterated with different configurations of crutches; 
1. **Iteration 1:** In this configuration, I used a flexible link to transfer load to thighs and used spring for additional shock absorption on the crutches. It didn't worked well in terms of load transfer and additionally slipped on thighs. 
2. **Iteration 2:** In this configuration, I achieved the desired functionality by using rigid links and providing a seated structure to support pelvis, thus transferring load during leg swing phase. 
3. **Iteration 3:** Improving on Iteration 2, I added constrained lateral movement to ease with crutch swing, designed physical stops based on simulation data to ensure stability, and further used telescopic locking seat to improve on the mobility of this crutch configuration.

This design was awarded second prize in Inter-IIT Tech Meet for the problem statement by [Biomedical Innovation Centre(BETIC)](https://www.betic.org/), IIT Bombay, India.

![Crutch iterations](/assets/Crutch_prototypes.png)
Left: Iteration1, Middle: Iteration2, Right: Iteration3

{% include embed.html url="https://www.youtube.com/embed/isyfPDoThuw" %}
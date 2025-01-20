---
title: "Redesigned Crutches"
excerpt: "To minimize the risk of crutch palsy and similar diseases, I redesigned crutches to offload the upperbody and transfer 60% of loading forces to pelvis region, thus reducing the intense pressure at one location."
collection: portfolio
---
<img align="left" width="140" height="220" src="/images/p8_Crutch_Itr3.png" style="padding-right: 15px; padding-bottom: 15px;">
Currently available crutches do not have the provision for weight distribution due to which long term use leads to intense pressure at one location depending on the type of crutch– Wrist, Elbow, or Underarms. This long-term intense pressure (from forces ~120% body weight) commonly leads to following medical conditions – Crutch Palsy, Wrist Injury, Artery Damage, etc. Lack of training among crutch users further increases the risk due to improper posture while walking with crutch. In India, approximately 13.5 million people are more prone to risk these conditions due to improper crutch handling. 

To minimize the risk of crutch palsy and similar diseases, I redesigned crutches to offload the upperbody and transfer 60% of loading forces to pelvis region, thus reducing the intense pressure at one location.

## How it works?
In the crutch walking gait cycle, crutch stance phase follows the dynamics of a double inverted pendulum in which crutch acts as Link1 and our body acts as Link2. Leveraging this dynamics and providing a rigid support to the body at pelvis for swinging at the end of link2, enabled load transfer.

![Crutch walking cycle](/images/p8_Crutch_cycle.png)
![Crutch working](/images/p8_Crutch_working.png)

## Outcome
We iterated with different configurations of crutches; 
1. **Iteration 1:** In this configuration, I used a flexible link to transfer load to thighs and used spring for additional shock absorption on the crutches. It didn't worked well in terms of load transfer and additionally slipped on thighs. 
2. **Iteration 2:** In this configuration, I achieved the desired functionality by using rigid links and providing a seated structure to support pelvis, thus transferring load during leg swing phase. 
3. **Iteration 3:** Improving on Iteration 2, I added constrained lateral movement to ease with crutch swing, designed physical stops based on simulation data to ensure stability, and further used telescopic locking seat to improve on the mobility of this crutch configuration.

This design was awarded second prize in Inter-IIT Tech Meet for the problem statement by [Biomedical Innovation Centre(BETIC)](https://www.betic.org/), IIT Bombay, India.

![Crutch iterations](/images/p8_Crutch_prototypes.png)
Left: Iteration1, Middle: Iteration2, Right: Iteration3

{% include embed.html url="https://www.youtube.com/embed/isyfPDoThuw" %}
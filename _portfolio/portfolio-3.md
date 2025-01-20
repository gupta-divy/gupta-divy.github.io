---
title: "Data Driven Control Design- Deep Learning based Task-Agnostic Controller"
excerpt: "Developed a subject and task-agnostic controller using deep learning model utilizing wearable sensor data, enabling use of exoskeletons outside lab settings"
collection: portfolio
---
<img align="left" width="200" height="250" src="/images/Intro_Exo.jpg" style="padding-right: 15px; padding-bottom: 15px;">
Current lower-limb wearable devices, like exoskeletons and prosthetics, are often restricted to lab settings due to their inability to perform effectively in natural environments. To enable their use in real-world scenarios, a control policy is needed that can handle multimodal ambulation, such as varying walking speeds, running, inclined walks, jumping, and sit-to-stand movements.

As described in the [Ankle Exo Project](https://gupta-divy.github.io/portfolio/portfolio-2/), most wearable devices use a three-level control system: a high-level controller that classifies ambulation modes, a mid-level controller that generates a reference trajectory for the classified mode, and a low-level controller that tracks this trajectory. While this approach works well for continuous, steady-state ambulation modes, it struggles when the ambulation modes in real-world settings are dynamic and cannot be easily discretized.

To overcome this limitation, I developed a subject- and task-agnostic controller using a deep learning model that predicts biological torque from time-history wearable sensor data, which is directly mapped to assistive torque.

<img src="/images/p3_sensorConfig.jpg" alt="Sensor Config" style="display: block; margin: 15px auto; width: 75%; height: auto;">
<center>Sensor Configuration</center>


## Dataset
The study used a diverse dataset consisting of wearable sensor data from five participants, covering 27 different ambulation tasks and variations of certain modes. Each task included a minimum of 4,000 time steps, representing an average of 20 seconds of data, with 80 features per sample from sensors like IMUs, goniometers, EMG sensors, and pressure insoles. This comprehensive dataset allowed for a thorough evaluation of data-driven techniques for estimating torque in ankle exoskeletons.

### Training Dataset
The objective was to create a generalized training model capable of working across different ankle exoskeleton devices and sensor configurations. To ensure repeatability, I selected tasks that could be consistently performed. I used a forward selection technique with an FCNN model and refined the selection based on biomechanical understanding and the repeatability of tasks within the experimental setup.

<img src="/images/p3_taskSelection.jpg" alt="Task Selection" style="display: block; margin: 15px auto; width: 80%; height: auto;">
<center>Task Selection</center>


### Training Features
I tested different feature subsets, ranging from all 80 sensors to a limited set (2 IMUs, 2 goniometers, 14 features). My hypothesis was that only a few key features, such as pressure insoles data, ankle angle, shank accelerometer data, and EMG signals from soleus and gastrocnemius muscles, would contribute directly to torque estimation. To validate this, I trained a regression model, analyzed feature f-values, and iteratively added and removed features to assess the FCNN model’s performance.

While EMG sensors showed high relevance, they were prone to noise due to sweat, hair, and skin adhesion, making them less suitable for natural settings. This emphasized the importance of thoughtful feature selection and integrating domain knowledge to develop more effective machine learning models.

## Training
Three distinct machine learning models were used to estimate ankle joint torque, each implemented with the deep learning framework TensorFlow:
- **FCNN:** Fully Connected Neural Network
- **LSTM:** Long Short-Term Memory
- **TCN:** Temporal Convolutional Network

The hyperparameters and overall architecture for each model were chosen through experimentation. Each model was compiled with the Adam optimizer and the MSE loss function. A callback function was added during training to save the best-performing model based on the validation dataset. More details about the models can be found in this [report](https://github.com/gupta-divy/Exo-controller-ML/blob/main/Project_report.pdf).

## Results
The TCN model performed the best, achieving the lowest error with an average RMSE of 0.093 N.m/Kg. The LSTM model had a slightly higher RMSE at 0.097, while the FCNN model had the highest at 0.098. On average, we achieved an RMSE of around 8% across all tasks. However, for tasks more relevant to ankle exoskeletons, the RMSE improved to around 5%.

In terms of computational efficiency, the TCN model was the fastest, with an average prediction time of 6µs. The FCNN model took about 60µs, and the LSTM model required 300µs due to the need for sequential data processing.

![RMSE across different tasks](/images/p3_AnkleExo_taskRMSE.png)
<center>RMSE on 22 hold-out tasks for FCNN, LSTM, and TCN Models</center>

![Torque prediction for normal-walking](/images/p3_AnkleExo_walkRMSE.png)
<center>Biological torque profile for normal walking at average walking speed</center>

## Other work:
I fine-tuned the model hyperparameters using Bayesian Optimization from the HyperOpt Library, achieving a 25% reduction in RMSE. Additionally, I removed the pressure insoles data from the feature set to make the model more generalized as the pressure insoles sensors were found to be prone to noise and permanent deformation over time. This reduction with number of features, resuled in an increased RMSE of around 10% but maintained the generalizability which is the key for its application.

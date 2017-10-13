
# CarND-Controls-MPC
## Tao YANG 
Oct. 13, 2017
---


## Overview

In this project, I implemented the MPC for the car driving around the lake with the help of ipopt and cppad. The cost function is a combination of cross track error, orientation error, actuation error and change of actuation error.

## Rubric points

1. **The Model:** Student describes their model in detail. This includes the state, actuators and update equations.
 * In this project, we apply the kinematic model as shown in the class with six states: vehicle's x and y coordinates, orientation ($\psi$), velocity, cross track error and psi error ($epsi$). The actuators are the steering angle $\delta_t$ and the throttle value $a_t$. The state update equation is as follows: 
![alt text](fig1.png "Logo Title Text 1")
 * A special handling is for $\psi$. Since the positive/negative definition is different between the model and the simulator, the sign before $\frac{v}{L_f}$ should be changed to negative from positive.
2. **Timestep Length and Elapsed Duration (N & dt):** Student discusses the reasoning behind the chosen N (timestep length) and dt (elapsed duration between timesteps) values. Additionally the student details the previous values tried.
 * The choice of $N=10$ and $t=0.1$ in the project is a consideration of tradeoff between computational cost and model accuracy. The higher $N$ is, the larger computational cost is, while the smaller $t$ is, the better kinematic model can approximate the true trajectory. The choice of $t=0.1$ only considers the latency is 100ms, which makes it easy to handle. Other choices such as $(N=25, t=0.05)$, $(N=5, t = 0.1)$ have also been explored.

3. **Polynomial Fitting and MPC Preprocessing:** A polynomial is fitted to waypoints. If the student preprocesses waypoints, the vehicle state, and/or actuators prior to the MPC procedure it is described.
 * In this project, the waypoints are preprocessed in such as way that the vehicle's x and y coordinate are zero, and initial orietation is 0. See code line 97-103 in the main.cpp.

4.  **Model Predictive Control with Latency:** The student implements Model Predictive Control that handles a 100 
millisecond latency. Student provides details on how they deal with latency.
 * The main observation for handling latency is that with a latency of 100ms, our current actuation will be applied in the next steps. With this, a simple change in the code line 119-122 in MPC.cpp will do the work.


```python

```

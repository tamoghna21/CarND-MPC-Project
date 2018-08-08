# CarND-Controls-PID
Self-Driving Car Engineer Nanodegree Program

[//]: # (Image References)

[video1]: ./video_output/MPC_control.mov "VideoMPC"
[image1]: ./equations/eq1.png "eq1"
[image2]: ./equations/eq2.png "eq2"
[image3]: ./equations/eq3.png "eq3"

---

## The Model

The kinematic model of the car considered in this project has six states [x,y,ψ,v,cte,eψ].
* x, y and ψ denote the position and orientation angle(in radian) of the car in 2D plane.
* v is the speed of the car in heading direction.
* cte is for cross track error, the deviation of the car's y coordiate from ref trajectory.
* eψ is the deviation of the car's orientation from the reference orientation.

Two cotrol inputs are considered in the model, steering input δ and throttle input a. Steering input has limit of [-25 deg, 25 deg]. Throttle input a is for both accelerator and the brake; positive for acceleration and negetive for braking. The limits on a is [-1, 1].

The state update equations for the model are:

![alt text][image1]


![alt text][image2]


![alt text][image3]



Here's he video for P implementation [link to my video result][video1]

## Timestep Length and Elapsed Duration (N & dt)

The value of the number of steps (N) is chosen as 10 and the time duration between actuations (dt) is chosen as 0.1 sec. So, total time horizon is 10 * 0.1 sec = 1 sec. At fast speed of the car, especially at turns, trying to predict the environment of the car at more than 1 sec in the future is not realistic. dt is chosen 0.1 sec, because from MPC perspective, dt should be as less as possible and we are assuming 100ms latency for actuation commands.
Other values tried for (N,dt) are (25,0.1), (25,0.05) , (20,0.1).

## Polynomial Fitting and MPC Preprocessing

The waypoints provided by the simulator is fitted to a third degree polynomial.

Before fitting the polynomial, the waypoints, which are in global coordinate system, are transformed into car's local coordinate system. Then cte and eψ is calculated.
To account for the latency of actuation commands, the six state values have been subjected to the state update equations described above for a duration of 100ms to calculate the delayed state values, which are fed into the MPC algorithm.


## Model Predictive Control with Latency

As described above, to deal with the latency of 100ms, the state update equations were applied on the current state values. That gives the state values delayed by 100ms. Then the MPC calculates the optimum steering command δ  and throttle input a.


Here's a video of the performance of MPC algorithm in the simulator [link to my video result][video1]

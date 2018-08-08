# CarND-Controls-PID
Self-Driving Car Engineer Nanodegree Program

[//]: # (Image References)

[video1]: ./video_output/driving_P_control.mov "VideoP"
[video2]: ./video_output/driving_PD_control.mov "VideoPD"
[video3]: ./video_output/driving_PID_full.mov "VideoPID"
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

* The D part of the controller compensates for the change in CTE in each step. That helps to damp down the oscillation of the car movement in the simulator.

Here's he video for PD implementation [link to my video result][video2]


* I part of the controller compensates for the steady state error due to any unknown disturbances in the car model etc. In this case, it can take care of steering drift, for example.

Here's he video for PID implementation [link to my video result][video3]

## How the final hyperparameters were chosen.

* I tuned the parameters manually. I first tuned the P parameter so that the car is at least compensating for the CTE. Then the car starts moving jittery way. Then I choose the D parameter to make sure the car moves straight at straight stretches of the road. Then I tuned the I parameter, so that the car is at the center of the lane, especially at the curves, because the car tends to out of the center of the lane due to unknown disturbaces in the car.


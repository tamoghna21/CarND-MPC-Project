# Model Predictive Control for Autonomous Driving

Model Predictive control transforms a tracking problem into a Optimal Control Problem. First we have a model of the system with the state vector and the control inputs. We define a cost function based on the current and future model predicted state vector. The optimal Control problem is to find the Control inputs such that the cost is minimized.

#### Note: This Project is part of the Udacity Self Driving Car nanodegree program.

[//]: # (Image References)

[video1]: ./video_output/MPC_control.mov "VideoMPC"
[image1]: ./mpc_ss1.png "mpc car1"
[image2]: ./mpc_ss2.png "mpc car2"
[image3]: ./mpc_ss3.png "mpc car3"

### Model Predictive Control
* Details about the control states and algorithm can be found [here](https://github.com/tamoghna21/CarND-MPC-Project/blob/master/writeup.md). The car drives itself across the entire circuit and always maintaining the required trajectory, on the drivable part of the road. :)

![alt text][image1]



![alt text][image2]



![alt text][image3]


Here's a video of the performance of MPC algorithm in the simulator [link to my video result][video1]





### For instructions related to environment setup and the simulator, please see [this one](https://github.com/tamoghna21/CarND-MPC-Project/blob/master/README_udacity.md).

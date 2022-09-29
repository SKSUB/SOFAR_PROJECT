# SOFAR_PROJECT
## MOBILE ROBOT NAVIGAITON USING ROS AND UNITY

## Aim of the project
Aim of this project is to move the husky robot to the given goal position while mapping it's environment.

## Development of the project
### UNITY END
The scene of the project is developed in UNITY (Unity is a cross-platform game engine developed by Unity Technologies, you can find the more information in this link https://unity.com/).

Husky robot (non holonomic Robot) is the differential drive robot used in the simulation is equipped with the LIDAR sensor to detect obstacles.  (More details on https://clearpathrobotics.com/husky-unmanned-ground-vehicle-robot/).

Unity will publish the Husky LIDAR sensor data to laser_scan and the position of the robot to the Odometry/frame. 

Visual of the unity scence,

![unitys](https://user-images.githubusercontent.com/82164428/193106029-ea498ad9-14b2-41e4-9bb9-2f1ea651040c.jpg)

### ROS END
The move_base is the naviagation package used to move the robot in the simulation, based on the fixed goal received by the move_base it guides the robot along the path with the planner by publishing the safe velocity commands (cmd_vel). The slam_gmapping provide the localization of the robot and map of the environment. 

![navigation stack](https://user-images.githubusercontent.com/82164428/193112234-e8c4a21e-8d34-41dc-9f70-be64eaec97d2.jpg)

(More info about ros navigaiton: https://wiki.ros.org/navigation?distro=noetic , move_base : https://wiki.ros.org/move_base?distro=noetic and gmapping: https://wiki.ros.org/gmapping) 

### UML COMPONENT DIAGRAM TO VISUALIZE THE PROJECT

![0 (2)](https://user-images.githubusercontent.com/82164428/193113410-b3d19493-98bd-448d-8abf-7505282ddacb.jpg)

### UML TEMPORAL DIAGRAM

![0](https://user-images.githubusercontent.com/82164428/193113534-39467d77-ed0d-4149-b23d-6a0fcadf020b.jpg)

## Building the project and setting it up
### UNITY END




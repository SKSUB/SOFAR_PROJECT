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
You can install the unity hub using this link https://unity3d.com/get-unity/download, and you need to have a Unity version 2020.2.2 to run this simulation, you can download from this archive https://unity3d.com/get-unity/download/archive.  

Download the Unity project folder from this link https://github.com/TheEngineRoom-UniGe/SofAR-Mobile-Robot-Navigation, extract it, then open Unity Hub and ADD the project to your projects list using the associated button. 

In the bar on top of the screen, open the 'Robotics/ROS settings' tab and replace the 'ROS IP Address' with the IP of the machine running ROS. 

### ROS END
The ros version used for this project is Noetic instlled on Ubuntu version 20.04.04 (More details to installing and setting up ros: https://wiki.ros.org/ROS/Tutorials/InstallingandConfiguringROSEnvironment).

Navigate to your catkin_workspace and into the src folder, inside the src folder give the following command to clone this repository into your src folder:

```
git clone https://github.com/SKSUB/SOFAR_PROJECT
```

Before compiling the pakage with catkin_make, make sure the following libraries are included. 

Navigate to your source folder and run:
```
git clone https://github.com/ros/common_msgs
```

```
sudo apt-get install ros-noetic-lms1xx
```

```
sudo apt-get install ros-noetic-navigation 
```
```
sudo apt-get install ros-noetic-openslam-gmapping
```

Final step before compiling is to open the 'mobile_robot_navigation_project' package, then navigate to config folder and open the params.yaml file. Under ROS_IP, insert the IP address of your machine.

Now run:

```
catkin_make
```

NOTE: The whole project was run on the single machine with the help of vmware player, but it can work with multiple machine as well with ros running on one machine and unity running on other machine if they are properly connected. 
      More details about the husky package can be referred in this link https://github.com/husky/husky, the husky package are developed based on this packages. 

## Starting the Simulation 

In order to launch the launch files, first navigate to catkin_ws and run the following command in three seperate terminal:
```
source devel/setup.bash
```

In the first Terminal,

To start both the gmapping and move_base node, run the following command to lauch the gmapping_demo launch file:
```
roslaunch husky_navigation gmapping_demo.launch
```

This launch file launch the move_base node and slam_gmapping package node. you can see the result in terminal.

In the second terminal,

To start the connection between ros and unity, launch the navigation.launch file:

```
roslaunch mobile_robot_navigation_project navigation.launch
```
After this on unity press play button to start the simulation.

You can see the handshake message in the unity terminal if everything is right. Connection between ros and unity is established. 

Note: The detail overview about establishing the connection between ros and unity can be followed with this link: https://github.com/TheEngineRoom-UniGe/SofAR-Mobile-Robot-Navigation

In the third terminal,

Now launch the Rviz launch to visuallize the husky with all the simulations:

```
roslaunch husky_viz view_model.launch
```
Note: if you get the xacro error, run the following command ''sudo apt-get install ros-noetic-husky-desktop''


This is the picture of rviz generated:

![rviz](https://user-images.githubusercontent.com/82164428/193136272-1da81fe8-542e-4783-8ae5-11b09de242d4.jpg)

And when you run the rqt_graph, 

![rqt_graph](https://user-images.githubusercontent.com/82164428/193136365-a4da8d14-4a7c-44c0-bf70-84efc58b4ee9.jpg)





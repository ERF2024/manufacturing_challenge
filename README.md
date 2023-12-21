# ERF Manufacturing Challenge simulation framework

- Version 1.0.0

---

<div style="display:flex;">
<div style="flex:50%; padding-right:10px; border-right: 1px solid #dcdde1">

**Package summary**

A repository for ERF Manufacturing Challenge. Used for build, test, and deployment for the challenge.

- Maintainer status: maintained
- Maintainers
  - Andrea Pupa
  - Niccolò Lucci


</div>
<div style="flex:40%; padding-left:10px;">

**Table of Contents**
- [Overview](#overview)
- [Installation Steps](#installation-steps)
- [Usage](#usage)
- [Important](#important)

</div>
</div>

---

## Overview

<img src="images/erf_logo.png" width="200"/>  <img src="https://www.ros.org/imgs/logo-white.png" width="200"/>

- This repository provides framework and the URDF for the challenge for simulation 
- You can find information about the challenge on the <a href="https://erf2024.eu/challenges/">rule page</a>
- The supported robot for this simulation is the Yumi Single Arm.

---

## Installation Steps

Clone the repository:
```
git clone -b apupa/devel git@github.com:MerlinLaboratory/abb_wrapper.git
```
and follow the steps to install it <a href="https://github.com/MerlinLaboratory/abb_wrapper">here</a>.

## Usage
You can run the demo using the launch file:

```
roslaunch gazebo_ros_abb_wrapper challenge_scene.launch
```
The system is already integrate with MoveIt for planning purpose. 

You can control the robot publishing the trajectory on the topic
```
rostopic pub /vel_arm_controller/command ...
```
To close the gripper you can call the services :
```
rosservice call /open_gripper std_msgs/Trigger "{}"
rosservice call /close_gripper std_msgs/Trigger "{}"
```

### Sensor topics:

Over the robot there is a depth camera that simulate a Realsense.
To see the data, check the topics

```
/camera...
```

## Important:

The real yumi used in the challenge will be velocity controlled, i.e. you should implement your controller that moves the robot along a desired trajectory.
Once you have developed it you should modify the controllers in the challenge_scene.launch:
```
<arg name="controllers" default="vel_group_arm_controller gripper_controller" doc="Controllers that are activated by default."/>
<arg name="stopped_controllers" default="vel_arm_controller" doc="Controllers that are initally loaded, but not started."/>  
```


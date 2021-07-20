# Kalman-Filter-in-ROS
Use robot_pose_ekf and odom_to_trajectory ROS pkg to localize turtlebot.


This tutorial closely follows Udacity's Robotics Engineer Nano Degree. So, many procedures will be in correspondense to this Nano Degree course.

---

## Requirements
 - Ubuntu 16.04 or 18.04 or 20.04 
 - Robot Operating System(ROS) Kinetic or Melodic or Neotic
 - Atleast 4GB RAM
 - Intel i3 & above
 - Nvidia or AMD GPU (optional, for better simulation performance)
 - Recommended, ROS Kinetic installed on Ubuntu 16.04
 </br>
Note: You can also use online ROS Stduio Platform, https://app.theconstructsim.com/ 

## Catkin Workspace Setup
Before you start downloading the different ROS packages, you need to create a catkin_ws to hold them in. If you already have a workspace in your /home/workspace directory, it is recommended that you keep a copy of it by renaming it to catkin_ws_saved. By doing so, you’ll avoid any possible conflict with pre-installed packages.

**Note: The name of your ROS distro is the version of installed ROS on your system,i.e.,kinetic or melodic or neotic. You may replace the distro name in the shell commands used in this READMe.md according to your ROS distro.**

```
$ mkdir -p /home/workspace/catkin_ws/src
$ cd /home/workspace/catkin_ws/src
$ catkin_init_workspace
$ cd ..
$ catkin_make
```
### System Update & Upgrade
```
$ sudo apt-get update
$ sudo apt-get upgrade -y
```

## Turtlebot Package
Access this [link](http://wiki.ros.org/turtlebot_gazebo) and go through the **turtlebot_gazebo** documentation.
### Install the package
```
$ sudo apt-get install ros-kinetic-turtlebot*
```

## Robot Pose Extended Kalman Filter(EKF) Package
Access this [link](http://wiki.ros.org/robot_pose_ekf) and go through the **robot_pose_ekf** documentation.

## TurtleBot Teleop Package
Access this [link](http://wiki.ros.org/turtlebot_teleop) and go through the **turtlebot_teleop** documentation.
### Clone the Package:
```
$ cd /home/workspace/catkin_ws/src
$ git clone https://github.com/turtlebot/turtlebot
```

## Install & Build Packages
### Clone the repo:
```
$ git clone https://github.com/YashKSahu/Kalman-Filter-in-ROS.git
$ cp -r /home/workspaceKalman-Filter-in-ROS /home/workspace/catkin_ws/src
```
### Install Dependencies:
```
$ cd /home/workspace/catkin_ws/src
$ rosdep install --from-paths src --ignore-src -r -y
```
### Build entire workspace:
```
$ cd /home/workspace/catkin_ws/
$ catkin_make
$ source devel/setup.bash
```

## Run & Visualize in Rviz:
```
$ cd /home/workspace/catkin_ws/
$ catkin_make
$ source devel/setup.bash
```
Launch the main file
```
$ roslaunch main main.launch 
```
The above command is equivalent to,(No need to run these commands) </br>
$ roslaunch turtlebot_gazebo turtlebot_world.launch </br>
$ roslaunch robot_pose_ekf robot_pose_ekf.launch </br>
$ roslaunch odom_to_trajectory create_trajectory.launch </br>
$ roslaunch turtlebot_teleop keyboard_teleop.launch </br>
$ rosrun rviz rviz </br>

### Teleoperate the turtlebot
Make sure you are inside the terminal where you launched your main.launch file.
**Follow the instuctions in the terminal(use given keys to teleoperate)**

While teleoperating you will see to paths red and green slightly overlapping in the rviz window. </br>
**Green - Filtered Trajectory** </br>
**Red   - Unfiltered Trajectory** </br>


https://user-images.githubusercontent.com/66440615/126311955-6f0094cc-cac5-4ee6-a573-5ab1b1ca5a4c.mp4


## View list of topics and nodes through rqt tools:
Now that you’ve launched the nodes, open a new terminal and run the **rqt graph**.
```
$ sudo apt-get install ros-kinetic-rqt*
$ rosrun rqt_graph rqt_graph
```

## rqt_multiplot:
Analyze and Plot the running process with rqt_multiplot.
Access this [link](https://github.com/ethz-asl/rqt_multiplot_plugin) and go through the **rqt_multiplot** ROS plugin documentation. </br>

### Open a new terminal and install the *rqt_multiplot*:
```
$ sudo apt-get install ros-kinetic-rqt -y
$ sudo apt-get install ros-kinetic-rqt-multiplot -y
$ sudo apt-get install libqwt-dev -y
$ sudo rm -rf ~/.config/ros.org/rqt_gui.ini
```
### Run the *rqt_plot* package node:
```
$ rosrun rqt_multiplot rqt_multiplot
```

## To Stop
To kill all running processes, hit **ctrl**+**c** in your keyboard while being inside of the main.launch terminal.

**Note:Issues regarding any errors or anything, just email me: kumarsahuyash007@gmail.com**

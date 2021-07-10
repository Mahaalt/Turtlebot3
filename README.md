# Using Turtlebot3 with SLAM approach

First, go to this link: https://emanual.robotis.com/docs/en/platform/turtlebot3/overview/, press at Quick Start Guide.

choose your ROS version, I chose the melodic version.

To install the dependent ROS packages, use this command:

`$ sudo apt-get install ros-melodic-joy ros-melodic-teleop-twist-joy \
  ros-melodic-teleop-twist-keyboard ros-melodic-laser-proc \
  ros-melodic-rgbd-launch ros-melodic-depthimage-to-laserscan \
  ros-melodic-rosserial-arduino ros-melodic-rosserial-python \
  ros-melodic-rosserial-server ros-melodic-rosserial-client \
  ros-melodic-rosserial-msgs ros-melodic-amcl ros-melodic-map-server \
  ros-melodic-move-base ros-melodic-urdf ros-melodic-xacro \
  ros-melodic-compressed-image-transport ros-melodic-rqt* \
  ros-melodic-gmapping ros-melodic-navigation ros-melodic-interactive-markers`
  
_______________________________________________________________
  
 Use these commands to install the TurtleBot3 packages:
  
`$ sudo apt-get install ros-melodic-dynamixel-sdk`

`$ sudo apt-get install ros-melodic-turtlebot3-msgs`

`$ sudo apt-get install ros-melodic-turtlebot3`

_______________________________________________________________

To set your TurtleBot3 model name, use this command, I chosed waffle_pi:

`$ echo "export TURTLEBOT3_MODEL=waffle_pi" >> ~/.bashrc`

_______________________________________________________________

After finishing installing all the packaging, go to Simulations choice and choose Gazebo Simulation to run the TurtleBot in Gazebo or choose SLAM to run it in it.

If you choose Gazebo Simulation use these commands to install simulation package:

`$ cd ~/catkin_ws/src/`

`$ git clone -b melodic-devel https://github.com/ROBOTIS-GIT/turtlebot3_simulations.git`

`$ cd ~/catkin_ws && catkin_make`

_______________________________________________________________

To launch simulation of the empty world:

`$ export TURTLEBOT3_MODEL=waffle_pi`

`$ roslaunch turtlebot3_gazebo turtlebot3_empty_world.launch`

![empty world](https://user-images.githubusercontent.com/71232960/125146377-2e82c780-e12e-11eb-9f9d-3a0104ec8b75.png)

_______________________________________________________________

To launch simulation of the TurtleBot3 world:

`$ roslaunch turtlebot3_gazebo turtlebot3_world.launch`

![turtlebot3 world](https://user-images.githubusercontent.com/71232960/125146454-8c171400-e12e-11eb-912b-527656dceff2.png)

_______________________________________________________________


To launch simulation of the TurtleBot3 house:

`roslaunch turtlebot3_gazebo turtlebot3_house.launch`

![Turtlebot house](https://user-images.githubusercontent.com/71232960/125146523-dd270800-e12e-11eb-8b6f-d9af5beba931.png)

_______________________________________________________________

To operate TurtleBot3, open a new Terminal window and use this command, make sure do not close any simulation window if you want to move the TurtleBot3:

`$ roslaunch turtlebot3_teleop turtlebot3_teleop_key.launch`

![00](https://user-images.githubusercontent.com/71232960/125148669-b4a60a80-e13c-11eb-92b0-47d9d2ddecbb.png)

_______________________________________________________________

if you want to run the TurtleBot3 in the SLAM simulation with a map, it is recommended to use either TurtleBot3 World or TurtleBot3 House.

use one of the following commands to load the Gazebo environment.

I used the TurtleBot3 world.
_______________________________________________________________

To lunch the simulation world:

`$ export TURTLEBOT3_MODEL=waffle_pi`

`$ roslaunch turtlebot3_gazebo turtlebot3_world.launch`

![turtlebot3 world](https://user-images.githubusercontent.com/71232960/125146962-63dce480-e131-11eb-93b9-a852d6525f62.png)

_______________________________________________________________

To run the SLAM node, open a new Terminal window and use thess commands:

`$ roslaunch turtlebot3_slam turtlebot3_slam.launch slam_methods:=gmapping`

_______________________________________________________________

To run teleoperation node, open new terminal window use this commands:

`$ roslaunch turtlebot3_teleop turtlebot3_teleop_key.launch`

![01](https://user-images.githubusercontent.com/71232960/125147185-6e4bae00-e132-11eb-9bf5-c64a5fca2c9b.png)

_______________________________________________________________

When the map is created successfully, open a new terminal window and use this command to save it:

`$ rosrun map_server map_saver -f ~/map`

![02](https://user-images.githubusercontent.com/71232960/125147433-ed8db180-e133-11eb-8c9f-67601b13c588.png)

_______________________________________________________________

This is the final result:

![map](https://user-images.githubusercontent.com/71232960/125147434-eebede80-e133-11eb-9b1d-7eee6740a81a.png)

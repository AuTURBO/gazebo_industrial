
# image shot
<img src="/picture/1.png" width="70%" height="70%">
<img src="/picture/2.png" width="70%" height="70%">

# Run
* First install TurtleBot3 package and openmanipulator
http://emanual.robotis.com/docs/en/platform/turtlebot3/pc_setup/#pc-setup
http://emanual.robotis.com/docs/en/platform/openmanipulator/

```bash
$ sudo apt-get install ros-kinetic-joy ros-kinetic-teleop-twist-joy ros-kinetic-teleop-twist-keyboard ros-kinetic-laser-proc ros-kinetic-rgbd-launch ros-kinetic-depthimage-to-laserscan ros-kinetic-rosserial-arduino ros-kinetic-rosserial-python ros-kinetic-rosserial-server ros-kinetic-rosserial-client ros-kinetic-rosserial-msgs ros-kinetic-amcl ros-kinetic-map-server ros-kinetic-move-base ros-kinetic-urdf ros-kinetic-xacro ros-kinetic-compressed-image-transport ros-kinetic-rqt-image-view ros-kinetic-gmapping ros-kinetic-navigation ros-kinetic-interactive-markers

$ cd ~/catkin_ws/src/
$ git clone https://github.com/ROBOTIS-GIT/turtlebot3_msgs.git
$ git clone https://github.com/ROBOTIS-GIT/turtlebot3.git
$ git clone https://github.com/ROBOTIS-GIT/open_manipulator.git
$ git clone https://github.com/ROBOTIS-GIT/open_manipulator_msgs.git
$ git clone https://github.com/ROBOTIS-GIT/open_manipulator_simulations.git
$ cd ~/catkin_ws && catkin_make
$ cd ~/catkin_ws/src
$ git clone https://github.com/ROBOTIS-GIT/open_manipulator_with_tb3.git
  -> need build, just use 'open_manipulator_with_tb3_waffle.urdf.xacro' file . 
```

* Second install gazebo_indus package
```bash
 $ cd ~/catkin_ws/src/
 $ git clone https://github.com/hyunoklee/gazebo_indus.git
 $ cd ~/catkin_ws && catkin_make
```
* Run Gazebo World
```bash 
 $ roslaunch gazebo_indus turtlebot3_industrial.launch
```
* Run control, you can contol turtlebot3 model at gazebo simulation world
```bash
 $ roslaunch turtlebot3_teleop turtlebot3_teleop_key.launch
 $ rostopic pub /open_manipulator/joint2_position/command std_msgs/Float64 "data: -1.0" --once
``
* openmanipulator control
```bash
 $ rostopic pub /open_manipulator/joint2_position/command std_msgs/Float64 "data: -1.0" --once
``
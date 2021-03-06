
# image shot
<img src="/picture/8.png" width="70%" height="70%">
<img src="/picture/1.png" width="70%" height="70%">
<img src="/picture/2.png" width="70%" height="70%">

# youtube video
Click image to link to YouTube video.  
[![Video Label](http://img.youtube.com/vi/0pigUC3L-VQ/0.jpg)](https://youtu.be/0pigUC3L-VQ?t=0s)   
[![Video Label](http://img.youtube.com/vi/wz9ZSK_a4nU/0.jpg)](https://youtu.be/wz9ZSK_a4nU?t=0s)   

# Run
* First install TurtleBot3 package and openmanipulator
http://emanual.robotis.com/docs/en/platform/turtlebot3/pc_setup/#pc-setup  
http://emanual.robotis.com/docs/en/platform/turtlebot3/slam/#slam  
http://emanual.robotis.com/docs/en/platform/turtlebot3/navigation/#navigation  
http://emanual.robotis.com/docs/en/platform/turtlebot3/simulation/#simulation  
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
```

* Second install gazebo_indus package
```bash
 $ cd ~/catkin_ws/src/
 $ git clone https://github.com/hyunoklee/gazebo_indus.git
 $ cd ~/catkin_ws && catkin_make
```
* setup model 
```bash
 $ eb
```
```bash 
 export ROS_MASTER_URI=http://127.0.0.1:11311
 export ROS_HOSTNAME=127.0.0.1
 #export TURTLEBOT3_MODEL=burger
 #export TURTLEBOT3_MODEL=waffle
 export TURTLEBOT3_MODEL=waffle_pi
```
```bash 
 $ sb
```
* Change move base parameter 
'''bash
 $ gedit ~/catkin_ws/src/turtlebot3/turtlebot3_navigation/param/dwa_local_planner_params_waffle_pi.yaml
'''
modify below parameter  
acc_lim_theta: 3.2 -> 6.5  
sim_time: 2.0 -> 1.0  

* Run
```bash
 $ cp ~/catkin_ws/src/gazebo_industrial/map/* ~/
 $ roslaunch gazebo_indus tb3_industrial.launch
 $ roslaunch turtlebot3_navigation turtlebot3_navigation.launch map_file:=$HOME/catkin_ws/src/gazebo_industrial/map/map.yaml
 $ roslaunch gazebo_indus tb3_move_region.launch
```
if you want to move turtlebot3 at Goal Region of room. ( there is Goal region GR0, GR1, GR2, GL0, GL1, GL2 ) 
```bash 
 $ rostopic pub /move_region/goal_region std_msgs/String "data: GL2" --once
```

* with open manipulator launch & run
```bash
 $ roslaunch gazebo_indus tb3_industrial_manip.launch
 $ roslaunch turtlebot3_teleop turtlebot3_teleop_key.launch
 $ rostopic pub /open_manipulator/joint2_position/command std_msgs/String "data: -1.0" --once

```

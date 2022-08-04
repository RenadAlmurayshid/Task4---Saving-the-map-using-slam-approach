# Task4---Saving-the-map-using-slam-approach
Task 4 :  Saving map using SLAM approach 
1)  Go to the turtlebot website to get the manual 
https://emanual.robotis.com/docs/en/platform/turtlebot3/overview/
2)  Select the PC set up and make sure to select the suitable type iam working on the melodic type 
-  Installing ROS remotely 
$ sudo apt update
$ sudo apt upgrade
$ wget https://raw.githubusercontent.com/ROBOTIS-GIT/robotis_tools/master/install_ros_melodic.sh
$ chmod 755 ./install_ros_melodic.sh 
$ bash ./install_ros_melodic.sh
-  Command for the dependency installation 
$ sudo apt-get install ros-melodic-joy ros-melodic-teleop-twist-joy \
  ros-melodic-teleop-twist-keyboard ros-melodic-laser-proc \
  ros-melodic-rgbd-launch ros-melodic-depthimage-to-laserscan \
  ros-melodic-rosserial-arduino ros-melodic-rosserial-python \
  ros-melodic-rosserial-server ros-melodic-rosserial-client \
  ros-melodic-rosserial-msgs ros-melodic-amcl ros-melodic-map-server \
  ros-melodic-move-base ros-melodic-urdf ros-melodic-xacro \
  ros-melodic-compressed-image-transport ros-melodic-rqt* \
  ros-melodic-gmapping ros-melodic-navigation ros-melodic-interactive-markers

-  Turtlebot3 packages installation 
$ sudo apt-get install ros-melodic-dynamixel-sdk
$ sudo apt-get install ros-melodic-turtlebot3-msgs
$ sudo apt-get install ros-melodic-turtlebot3

-  Selecting either burger or waffle name and setting it command
echo "export TURTLEBOT3_MODEL=burger" >> ~/.bashrc

-  connect PC to wifi and check the IP address
$ ifconfig


-  Update the ROS IP address ( I inserted the image and how it should look )
$ nano ~/.bashrc


-  Source the bash 
$ source ~/.bashrc

3)  Go to the gazebo simulation and choose the type ( mine is melodic ) 
-  Get the simulation package to be installed 
$ cd ~/catkin_ws/src/
 $ git clone -b melodic-devel https://github.com/ROBOTIS-GIT/turtlebot3_simulations.git
$ cd ~/catkin_ws && catkin_make

-  Launch the simulation world 
Since I have chosen burger these are my commands 


$ export TURTLEBOT3_MODEL=burger



$ roslaunch turtlebot3_gazebo turtlebot3_empty_world.launch

-  Start turtlebot3 up 


$ roslaunch turtlebot3_teleop turtlebot3_teleop_key.launch

4)  On the left side you will see SLAM operation go there 
-  Launch simulation world 
Choose the type you have (Mine is melodic)


$ export TURTLEBOT3_MODEL=burger


$ roslaunch turtlebot3_gazebo turtlebot3_world.launch

-  Go to SLAM node and start running it with these commands 


$ export TURTLEBOT3_MODEL=burger


$ roslaunch turtlebot3_slam turtlebot3_slam.launch slam_methods:=gmapping

-  Get the teleportation node running by using these commands 
$ export TURTLEBOT3_MODEL=burger
$ roslaunch turtlebot3_teleop turtlebot3_teleop_key.launch

 Control Your TurtleBot3!
 ---------------------------
 Moving around:
        w
   a    s    d
        x

 w/x : increase/decrease linear velocity
 a/d : increase/decrease angular velocity
 space key, s : force stop

 CTRL-C to quit

-  Start saving the map 
rosrun map_server map_saver -f ~/map

5)  Select the navigation node list 
-  Get navigation nodes running 
 $ roscore

-  Get the navigation launched by using these commands 
$ export TURTLEBOT3_MODEL=burger
$ roslaunch turtlebot3_navigation turtlebot3_navigation.launch map_file:=$HOME/map.yaml

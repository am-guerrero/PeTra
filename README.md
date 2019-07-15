##############################
## ROS KINECTIC INSTALATION ##
##############################

$ sudo sh -c 'echo "deb http://packages.ros.org/ros/ubuntu $(lsb_release -sc) main" > /etc/apt/sources.list.d/ros-latest.list'  
$ sudo apt-key adv --keyserver hkp://ha.pool.sks-keyservers.net:80 --recv-key 421C365BD9FF1F717815A3895523BAEEB01FA116  
$ sudo apt-get update  
$ sudo apt-get upgrade  
$ sudo apt-get install ros-kinetic-desktop-full  
$ sudo rosdep init  
$ rosdep update  
$ echo "source /opt/ros/kinetic/setup.bash" >> ~/.bashrc  
$ source ~/.bashrc  
$ sudo apt install python-rosinstall python-rosinstall-generator python-wstool build-essential  
$ mkdir -p catkin_ws/src  
$ cd catkin_ws/  
$ catkin_make  
$ source devel/setup.bash  
$ echo $ROS_PACKAGE_PATH  

############################
## TENSORFLOW INSTALATION ##
############################

Repos:  
- https://github.com/ethz-asl/tensorflow_catkin  
- https://github.com/catkin/catkin_simple  
- https://github.com/tradr-project/tensorflow_ros_cpp.git  

$ cd ~/catkin_ws/src/  
$ git clone https://github.com/ethz-asl/tensorflow_catkin.git  
$ git clone https://github.com/catkin/catkin_simple.git  

IF YOU WANT COMPILE THE PACKAGE WITH OPTIMIZATION FOR YOUR CPU:  
  - Open the CMakeLists.txt of the tensorflow_catkin package  
  - Find "-Dtensorflow_OPTIMIZE_FOR_NATIVE_ARCH=OFF" and change it to ON
  - Save and continue the steps

$ catkin_make  
$ git clone https://github.com/tradr-project/tensorflow_ros_cpp.git  
$ catkin_make  

####################################
## TO TEST TENSORFLOW INSTALATION ##
####################################

Repo:  
- https://github.com/tradr-project/tensorflow_ros_test.git   

$ cd ~/catkin_ws/src/  
$ git clone https://github.com/tradr-project/tensorflow_ros_test.git  
$ catkin_make  
$ roscore  
$ rosrun tensorflow_ros_test tensorflow_ros_test_node  

#######################
## PETRA INSTALATION ##
#######################
$ sudo apt-get install ros-kinetic-rviz-visual-tools
$ cd ~/catkin_ws/src/  
$ git clone git@cre.unileon.es:claudiaaa/petra.git  
$ cd ..  
$ catkin_make  

Is necesary chage scanTopic in petra/config/parameters.yaml  

TO RUN IT:  

With a rosbag: roslaunch petra petra_rosbag.launch rosbag_file:=absolute_path_to_bag_file  
With a realtime info: roslaunch petra petra.launch  

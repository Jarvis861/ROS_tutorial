<div align="center">

# ROS_tutorial
</div>

## Introduction
This repository includes some example codes for ROS beginners to understand how ROS works. 

| Type |           |         | Communication Pattern | Message Type | Typical Usage |
| ------ | --------- | --------- | -------- | -------- | --------------- |
| topic | Talker-Listener | publish-subscribe | asynchronous | message(*.msg) | sensor data, control command, ... |
| service | Client-Server | request-response | synchronous | service(*.srv) | specific actions, switch, photo, ... |

* `src`: roscpp
* `scripts`: rospy
* `msg`: gps.msg
* `srv`: Greeting.srv

## Run
**1.  Run examples**
Run the following commands in 3 terminals.
* topic (roscpp)
```
roscore
rosrun my_demo listener
rosrun my_demo talker
```
* service (roscpp)
```
roscore
rosrun my_demo server
rosrun my_demo client
```
* topic (rospy)
```
roscore
rosrun my_demo py_listener
rosrun my_demo py_talker
```
* service (rospy)
```
roscore
rosrun my_demo py_server
rosrun my_demo py_client
```

**2.  Build an example**

*1)* Create a package:
```
cd ~/catkin_ws/src
catkin_create_pkg ${PACKAGE_NAME} roscpp rospy std_msgs
```

*2)* Define a message (or service):
```
cd ${PACKAGE_NAME}
mkdir msg && cd msg
gedit ${MESSAGE_NAME}.msg
```

*3)* Initialize `.msg` or `.srv` :
```
cd ~/catkin_ws
catkin_make
```

For roscpp, you will find header files in `~/catkin_ws/devel/include/${PACKAGE_NAME}/${MESSAGE_NAME}.msg`.

For rospy, the path is `~/catkin_ws/devel/lib/python3/dist-packages/${PACKAGE_NAME}/msg/__init__.py`

*4)* Configure `CMakeLists.txt` and `Package.xml` for roscpp.


## Install and Configure ROS

*1)* Install ROS Noetic. You can refer to this [installation guide](https://zhuanlan.zhihu.com/p/515361781).

*2)* Create a workspace and initialize:
```
mkdir -p ~/Documents/catkin_ws/src
cd ~/Documents/catkin_ws/src
catkin_init_workspace

cd ~/Documents/catkin_ws
catkin_make
```

*3)* Configure ROS environment:

* Open your `.bashrc` file:
```
sudo gedit ~/.bashrc
```
and make sure the following in `.bashrc`. Here the ROS version is `melodic` and the workspace path is `~/Documents/catkin_ws`.
```
# Set ROS noetic
source /opt/ros/noetic/setup.bash
source ~/Documents/catkin_ws/devel/setup.bash
```

* Recommend to add shortcut keys in your `.bash_aliases` file:
```
sudo gedit ~/.bash_aliases
```
and copy the following to `.bash_aliases`:
```
######### ROS workspace #########
alias cw='cd ~/Documents/catkin_ws'
alias cs='cd ~/Documents/catkin_ws/src'
alias cm='cd ~/Documents/catkin_ws && catkin_make'
```

* Source `.bashrc` or restart your terminal so the path changes take effect:
```
source ~/.bashrc
```

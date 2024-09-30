---
tags:
  - bp
---
https://gazebosim.org/docs/latest/ros_installation/#installing-the-default-gazebo-ros-pairing
![[Pasted image 20240930102806.png]]
# Installing the Default Gazebo/ROS Pairing
```bash
sudo apt-get install ros-${ROS_DISTRO}-ros-gz
```

# Launch Gazebo from ROS 2
```bash
ros2 launch ros_gz_sim gz_sim.launch.py gz_args:=empty.sdf
```

huh?
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

> [!info] Let's install ROS2 Jammy, since that has the best support for GZ Harmonic

```bash
sudo apt update && sudo apt install curl -y
sudo curl -sSL https://raw.githubusercontent.com/ros/rosdistro/master/ros.key -o /usr/share/keyrings/ros-archive-keyring.gpg
```

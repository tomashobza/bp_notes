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

> [!info] Let's install ROS2 Jammy, since that has the best support for GZ Harmonic https://docs.ros.org/en/jazzy/Installation/Ubuntu-Install-Debs.html
>> ![[Pasted image 20240930113950.png]]
>> nevermind ...

---
Let's try setting it all up

# Install MAVROS for ROS 2
```bash
sudo apt install ros-humble-mavros ros-humble-mavros-extras
```

# Install Gazebo (Ignition) Fortress
```bash
sudo apt-get update
sudo apt-get install lsb-release gnupg

sudo curl https://packages.osrfoundation.org/gazebo.gpg --output /usr/share/keyrings/pkgs-osrf-archive-keyring.gpg
echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/pkgs-osrf-archive-keyring.gpg] http://packages.osrfoundation.org/gazebo/ubuntu-stable $(lsb_release -cs) main" | sudo tee /etc/apt/sources.list.d/gazebo-stable.list > /dev/null
sudo apt-get update
sudo apt-get install ignition-fortress
```

# Install `gz_ros2_control`
https://github.com/ros-controls/gz_ros2_control
```bash
sudo apt install ros-humble-ign-ros2-control
```

# Install `ardupilot_gazbeo` plugin
https://github.com/ArduPilot/ardupilot_gazebo
```bash

```
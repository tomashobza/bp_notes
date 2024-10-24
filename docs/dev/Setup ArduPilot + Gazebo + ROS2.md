---
tags:
  - bp
---


Let's go through the setup process to ensure you have all the necessary packages:
0. Create a ROS2 workspace:
```bash
source /opt/ros/humble/setup.bash
mkdir -p ~/ros2_ws/src
cd ~/ros2_ws/src
```
2. First, make sure you're in your ROS2 workspace:
```bash
cd ~/ros2_ws
```
2. Clone the required repositories:
```bash
cd src
git clone https://github.com/ArduPilot/ardupilot_gazebo.git
git clone https://github.com/ArduPilot/ardupilot_gz.git
cd ..
```
3. Install dependencies
```bash
sudo apt update
rosdep update
rosdep install --from-paths src --ignore-src -r -y
```
4. Build the workspace
```bash
colcon build --symlink-install
```
5. Source the workspace
```bash
source /opt/ros/humble/setup.bash
source ~/ros2_ws/install/setup.bash
export GZ_VERSION=harmonic  # or garden, depending on your Gazebo version
```
6. Run the launch file
```bash
ros2 launch ardupilot_gz_bringup iris_runway.launch.py
```
Run the Gazebo -> ROS2 bridge on the camera topic
```bash
source /opt/ros/humble/setup.bash
ros2 run ros_gz_bridge parameter_bridge /world/map/model/iris/model/gimbal/link/pitch_link/sensor/camera/image@sensor_msgs/msg/Image[ignition.msgs.Image
```
Check if the topic is present
```bash
ros2 topic list
```
> Should return `/world/map/model/iris/model/gimbal/link/pitch_link/sensor/camera/image` 

Run `rqt` and watch the drone camera feed.

> [!warning] Make sure all terminals are sourced with step no. 5

This should be the result:
![[Pasted image 20240930232756.png]]

---
# Pokus
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



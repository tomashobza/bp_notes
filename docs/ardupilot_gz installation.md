---
tags:
  - bp
---
https://github.com/ArduPilot/ardupilot_gz?tab=readme-ov-file
## Install

#### 1. Create a workspace folder
```shell
mkdir -p ~/ros2_ws/src
```
#### 2. Get the project source
```shell
cd ~/ros2_ws
vcs import --input https://raw.githubusercontent.com/ArduPilot/ardupilot_gz/main/ros2_gz.repos --recursive src
```
#### 3. Set the Gazebo version to Harmonic or Garden:

It is recommended to put this in your `~/.bashrc` or equivalent file.
```shell
export GZ_VERSION=harmonic
```
#### 4. Update ROS dependencies
```shell
cd ~/ros2_ws
source /opt/ros/humble/setup.bash
sudo apt update
rosdep update
rosdep install --from-paths src --ignore-src -y
```
#### 5. Build
```shell
cd ~/ros2_ws
colcon build
```
#### 6. Test
```shell
source ./install/setup.bash
colcon test --packages-select ardupilot_sitl ardupilot_dds_tests ardupilot_gazebo ardupilot_gz_applications ardupilot_gz_description ardupilot_gz_gazebo ardupilot_gz_bringup
colcon test-result --all --verbose
```
---
tags:
  - bp
---
https://ardupilot.org/dev/docs/ros2-gazebo.html
## Install ROS2 ArduPilot
1. Clone required repos
```bash
mkdir -p ~/ardu_ws/src
cd ~/ardu_ws
vcs import --recursive --input  https://raw.githubusercontent.com/ArduPilot/ardupilot/master/Tools/ros2/ros2.repos src
```
2. Update all dependencies
```bash
cd ~/ardu_ws
sudo apt update
rosdep update
source /opt/ros/humble/setup.bash
rosdep install --from-paths src --ignore-src
```

## Install ROS2 + ArduPilot + Gazebo

3. Clone the required repos
```bash
cd ~/ardu_ws
vcs import --input https://raw.githubusercontent.com/ArduPilot/ardupilot_gz/main/ros2_gz.repos --recursive src
```

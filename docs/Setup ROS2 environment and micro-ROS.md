---
tags:
  - bp
---
https://github.com/ArduPilot/ardupilot/tree/master/libraries/AP_DDS#installing-build-dependencies
https://ardupilot.org/dev/docs/ros2.html#installation-ubuntu
```bash
# Clone the repository
mkdir -p ~/ardu_ws/src
cd ~/ardu_ws
vcs import --recursive --input  https://raw.githubusercontent.com/ArduPilot/ardupilot/master/Tools/ros2/ros2.repos src

# Install the dependencies
cd ~/ardu_ws
sudo apt update
rosdep update
source /opt/ros/humble/setup.bash
rosdep install --from-paths src --ignore-src

# Installing the MicroXRCEDDSGen build dependency
sudo apt install default-jre
cd ~/ardu_ws
git clone --recurse-submodules https://github.com/ardupilot/Micro-XRCE-DDS-Gen.git
cd Micro-XRCE-DDS-Gen
./gradlew assemble
echo "export PATH=\$PATH:$PWD/scripts" >> ~/.bashrc

# Build the workspace
cd ~/ardu_ws
colcon build --packages-up-to ardupilot_dds_tests
```

## Setup DDS
```bash
# Dependencies for a virtual serial port
sudo apt-get update
sudo apt-get install socat

# Install geographic_msgs
sudo apt install ros-humble-geographic-msgs
```

[[Installing ROS 2 and the micro-ROS build system]]
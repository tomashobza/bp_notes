---
tags:
  - bp
---
https://micro.ros.org/docs/tutorials/core/first_application_linux/
- Do "Installing ROS 2 and the micro-ROS build system"
    - Skip the docker run command, build it locally instead
- Skip "Creating a new firmware workspace"
- Skip "Building the firmware"
- Do "Creating the micro-ROS agent"
- Source your ROS workspace
```bash
ROS_DISTRO=humble

# Source the ROS 2 installation
source /opt/ros/$ROS_DISTRO/setup.bash

# Create a workspace and download the micro-ROS tools
mkdir microros_ws
cd microros_ws
git clone -b $ROS_DISTRO https://github.com/micro-ROS/micro_ros_setup.git src/micro_ros_setup

# Update dependencies using rosdep
sudo apt update && rosdep update
rosdep install --from-paths src --ignore-src -y

# Install pip
sudo apt-get install python3-pip

# Build micro-ROS tools and source them
colcon build
source install/local_setup.bash
```
## Creating a new firmware workspace
```bash
ros2 run micro_ros_setup create_firmware_ws.sh host
```
## Build the firmware
```bash
ros2 run micro_ros_setup build_firmware.sh
source install/local_setup.bash
```
## Creating the micro-ROS agent
```bash
# Download micro-ROS-Agent packages
ros2 run micro_ros_setup create_agent_ws.sh
```

Now, let’s build the agent packages and, when this is done, source the installation:
```bash
# Build step
ros2 run micro_ros_setup build_agent.sh
source install/local_setup.bash
```
## Running the micro-ROS app
```bash
# Run a micro-ROS agent
ros2 run micro_ros_agent micro_ros_agent udp4 --port 8888
```
Run micro-ROS node:
```bash
source /opt/ros/$ROS_DISTRO/setup.bash
source install/local_setup.bash

# Use RMW Micro XRCE-DDS implementation
export RMW_IMPLEMENTATION=rmw_microxrcedds

# Run a micro-ROS node
ros2 run micro_ros_demos_rclc ping_pong
```

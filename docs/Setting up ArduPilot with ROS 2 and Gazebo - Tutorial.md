This tutorial guides you through setting up a development environment for ArduPilot with ROS 2 Humble and Gazebo Harmonic on Ubuntu 22.04.

## Prerequisites

```bash
# Install ROS 2 Humble (if not already installed)
sudo apt install ros-humble-desktop-full

# Install additional dependencies
sudo apt install python3-vcstool python3-pip python3-pygame python3-matplotlib python3-lxml python3-yaml python-is-python3 libpython3-dev libtool cmake default-jre
```

## Setting up the Workspace

1. Create a new workspace:
```bash
cd ~
rm -rf ardu_ws  # Remove if exists
mkdir -p ardu_ws/src
cd ardu_ws
```

2. Clone required repositories:
```bash
vcs import --input https://raw.githubusercontent.com/ArduPilot/ardupilot_gz/main/ros2_gz.repos --recursive src
```

3. Set up Gazebo environment:
```bash
# Add to ~/.bashrc
echo "export GZ_VERSION=harmonic" >> ~/.bashrc
source ~/.bashrc

# Install Gazebo Harmonic and dependencies
sudo apt update
sudo apt install gz-harmonic
sudo apt install libgz-transport13-dev libgz-math7-dev libgz-msgs9-dev python3-gz-math7
```

## Installing MicroXRCEDDSGen

This is a crucial step and must be done correctly:

```bash
cd ~/ardu_ws
rm -rf Micro-XRCE-DDS-Gen  # Remove if exists
git clone https://github.com/ardupilot/Micro-XRCE-DDS-Gen.git
cd Micro-XRCE-DDS-Gen
git submodule update --init --recursive
./gradlew assemble
echo "export PATH=\$PATH:$PWD/scripts" >> ~/.bashrc
source ~/.bashrc

# Verify installation
microxrceddsgen -version
```

## Building the Workspace

1. Install ROS dependencies:
```bash
cd ~/ardu_ws
source /opt/ros/humble/setup.bash
rosdep update
rosdep install --from-paths src --ignore-src -r -y
```

2. Build the workspace (this will take some time):
```bash
colcon build --packages-up-to ardupilot_gz_bringup --symlink-install --allow-overriding ardupilot_msgs ardupilot_sitl ros_gz_bridge ros_gz_interfaces ros_gz_sim sdformat_urdf --cmake-clean-cache
source install/setup.bash
```

## Testing the Setup

1. Launch the simulation:
```bash
cd ~/ardu_ws
source install/setup.bash
ros2 launch ardupilot_gz_bringup iris_runway.launch.py
```

This should open Gazebo with a simulated Iris drone on a runway.

2. In a new terminal, check available ROS topics:
```bash
source ~/ardu_ws/install/setup.bash
ros2 topic list
```

## Common Issues and Solutions

1. If you get build errors related to ardupilot_msgs or symbolic links:
```bash
cd ~/ardu_ws
rm -rf build/ install/ log/
```
Then try building again.

2. If microxrceddsgen version issues occur, ensure you're using the ArduPilot fork and have initialized submodules.

3. If Gazebo packages are not found, make sure GZ_VERSION is set correctly:
```bash
echo $GZ_VERSION  # Should output 'harmonic'
```

## Directory Structure
After setup, your workspace should look like this:
```
~/ardu_ws/
├── src/
│   ├── ardupilot/
│   ├── ardupilot_gazebo/
│   ├── ardupilot_gz/
│   ├── ardupilot_sitl_models/
│   ├── micro_ros_agent/
│   ├── ros_gz/
│   └── sdformat_urdf/
├── build/
├── install/
└── log/
```

## Next Steps

1. Create custom Gazebo worlds
2. Implement autonomous flight controllers
3. Add sensors and custom plugins
4. Integrate computer vision capabilities

## References

- [ArduPilot Documentation](https://ardupilot.org/dev/)
- [ROS 2 Documentation](https://docs.ros.org/en/humble/)
- [Gazebo Documentation](https://gazebosim.org/docs)
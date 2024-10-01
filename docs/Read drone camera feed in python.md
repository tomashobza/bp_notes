---
tags:
  - bp
---
```bash
pip install opencv-python
pip install numpy
pip install dronekit
pip install pymavlink
```

```bash
sudo apt-get update
sudo apt-get install libgstreamer1.0-0 gstreamer1.0-plugins-base gstreamer1.0-plugins-good gstreamer1.0-plugins-bad gstreamer1.0-plugins-ugly gstreamer1.0-libav gstreamer1.0-doc gstreamer1.0-tools gstreamer1.0-x gstreamer1.0-alsa gstreamer1.0-gl gstreamer1.0-gtk3 gstreamer1.0-qt5 gstreamer1.0-pulseaudio
```

> [!warning] It turns out that Gazebo uses some internal transport protocol (I believe similar to ROS), so conventional libraries to read the camera feed don't work. I decided to go via the path of least resistance and use ROS2 with Gazebo and Ardupilot.

# Setup process
[[Setup ArduPilot + Gazebo + ROS2]]

# Configuration Architecture
```puml
@startuml
!define RECTANGLE class

skinparam componentStyle uml2

rectangle "Computer" {
  package "Gazebo" {
    [Physics Simulation]
    [Drone Model]
    [Simulated Sensors]
    [ArduPilot Plugin]
    [Camera]
  }

  package "ArduPilot SITL" {
    [Autopilot Firmware]
  }

  package "ROS 2" {
    [ROS 2 Nodes]
    [ros_gz_bridge]
  }

  [MAVProxy]
  [rqt]
}

[Physics Simulation] --> [Drone Model] : updates
[Drone Model] --> [Simulated Sensors] : generates data
[Simulated Sensors] --> [ArduPilot Plugin] : sends sensor data
[ArduPilot Plugin] <--> [Autopilot Firmware] : MAVLink
[Autopilot Firmware] <--> [MAVProxy] : MAVLink
[ArduPilot Plugin] --> [Drone Model] : applies control outputs
[Camera] --> [ros_gz_bridge] : Gazebo topic
[ros_gz_bridge] --> [ROS 2 Nodes] : ROS 2 topic
[ROS 2 Nodes] --> [rqt] : ROS 2 topic

note right of [ArduPilot Plugin]
  Bridges between Gazebo
  and ArduPilot SITL
end note

note right of [ros_gz_bridge]
  Translates between Gazebo
  and ROS 2 topics
end note

note bottom of [MAVProxy]
  Sends commands to
  ArduPilot SITL
end note

note bottom of [rqt]
  Displays camera
  feed and other data
end note

@enduml
```

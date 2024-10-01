---
tags:
  - bp
---
![[Pasted image 20240922232414.png]] 
![[Pasted image 20240922232623.png]]
Now for landing on an aruco marker, a camera on the drone is obviously a need. Let's setup [ardupilot and gazebo with a camera](https://github.com/ArduPilot/ardupilot_gazebo?tab=readme-ov-file#3-streaming-camera-video)
![[Pasted image 20240923142244.png]]
And we have video! But let's point the gimbal down by default:
Change this line in the file `~/ardupilot_gazebo/models/iris_with_gimbal`:
```xml
<pose degrees="true">0 -0.01 -0.124923 90 -90 90</pose>
```
Or point the gimball camera down with:
```bash
rc 6 1500 # roll
rc 7 1300 # pitch
```
![[Pasted image 20240923150857.png]]
# Run commands

Run Gazebo
```shell
gz sim -v4 -r iris_runway.sdf
```

Run ArduPilot SITL with a specified parameter file
```bash
cd ardupilot

sim_vehicle.py -D -v ArduCopter -f JSON --add-param-file=$HOME/ardupilot_gazebo/config/gazebo-iris-gimbal.parm --console --map
```

## Start camera feed
The `gimbal.sdf` world includes a 3 degrees of freedom gimbal with a zoomable camera. To start streaming:
```shell
gz topic -t /world/gimbal/model/mount/model/gimbal/link/pitch_link/sensor/camera/image/enable_streaming -m gz.msgs.Boolean -p "data: 1"
```

Display the streamed video:
```shell
gst-launch-1.0 -v udpsrc port=5600 caps='application/x-rtp, media=(string)video, clock-rate=(int)90000, encoding-name=(string)H264' ! rtph264depay ! avdec_h264 ! videoconvert ! autovideosink sync=false
```
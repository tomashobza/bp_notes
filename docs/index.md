---
tags:
  - bp
---
# Roadmap
- [x] Install ArduPilot, Gazebo, ROS2 on the VM
- [x] Run ArduPilot SITL
- [x] Run STIL + Gazebo
- [x] Read camera feed in Gazebo
- [x] Install DroneKit
- [x] Run DroneKit + SITL, control drone via python
- [ ] Run DroneKit + SITL + Gazebo, read camera feed in python
# Dependency installation
This guide is appliable for a fresh install of Ubuntu 22.04 arm64. Gotten from: https://github.com/ArduPilot/ardupilot_gz?tab=readme-ov-file

- [[AdruPilot installation]]
- [[ROS2 Humble installation]]
- [[Gazebo Harmonic installation]]
- This is weird and didn't really work
	- [!] [[Setup ROS2 environment and micro-ROS]]
	- [!] [[ardupilot_gz installation]]

# Steps
- [[Using SITL with gazebo]]
- [[Run Gazebo + ArduPilot STIL with a camera feed]]
- [[Run DroneKit to control ArduPilot STIL]]
- [[Read drone camera feed in python]]

# Research
> SCHONBERGER, Johannes L.; FRAHM, Jan-Michael. Structure-from-motion revisited. In: _Proceedings of the IEEE conference on computer vision and pattern recognition_. 2016. p. 4104-4113.
> [https://www.cv-foundation.org/openaccess/content_cvpr_2016/papers/Schonberger_Structure-From-Motion_Revisited_CVPR_2016_paper.pdf](https://www.cv-foundation.org/openaccess/content_cvpr_2016/papers/Schonberger_Structure-From-Motion_Revisited_CVPR_2016_paper.pdf)

>[https://cloud.sdsc.edu/v1/AUTH_opentopography/www/shortcourses/18SGTF/2_nissen-GSA-sept-2016-SfM-lecture1-Intro-Motivations-FINAL.pdf](https://cloud.sdsc.edu/v1/AUTH_opentopography/www/shortcourses/18SGTF/2_nissen-GSA-sept-2016-SfM-lecture1-Intro-Motivations-FINAL.pdf)

> SIFT (Scale Invariant Feature Transform) - Robustní algoritmus pro extrakci rysů, který umožňuje nalézt shodné body i v obrazech s odlišným měřítkem, úhlem pohledu nebo osvětlením.
> https://www.youtube.com/watch?v=ram-jbLJjFg
> https://weitz.de/sift/

> Structure-From-Motion
> https://youtu.be/JlOzyyhk1v0?si=kY-hb6UncmXVEBmB
> https://link.springer.com/content/pdf/10.1007/BFb0014857.pdf - orthografické structure from motion
> TOMASI, Carlo; KANADE, Takeo. Shape and motion from image streams: a factorization method. _Proceedings of the National Academy of Sciences_, 1993, 90.21: 9795-9802.
> https://www.pnas.org/doi/epdf/10.1073/pnas.90.21.9795

![[Pasted image 20241013122718.png]]
![[Pasted image 20241013122725.png]]
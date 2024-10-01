---
tags:
  - bp
---
As DroneKit is not in development anymore, there were troubles with latest Python versions. Hence using `pyenv` and using python `3.9.20` is a good way to prevent troubles.
```bash
# Install dronekit
pip install dronekit
pip install dronekit-sitl # Doesn't work on arm64 architecture :D
```

Runing the SITL and connecting to it from the Python code:
![[Pasted image 20240923172927.png]]
Using the python code to fly, spin around in a cricle, and land the drone.
![[Pasted image 20240923174419.png]]

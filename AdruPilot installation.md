---
tags:
  - bp
---
https://ardupilot.org/dev/docs/building-setup-linux.html
```bash
# Install git
sudo apt-get update    
sudo apt-get install git
sudo apt-get install gitk git-gui

# Clone the repository
git clone --recurse-submodules https://github.com/ArduPilot/ardupilot.git
cd ardupilot

# Install the prerequirements
Tools/environment_install/install-prereqs-ubuntu.sh -y

# Reload the path (log-out-it to make it permanent)
. ~/.profile
```
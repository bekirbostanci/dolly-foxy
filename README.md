[![Build Status](https://travis-ci.org/chapulina/dolly.svg?branch=master)](https://travis-ci.org/chapulina/dolly)
# Important 

This is not original dolly repository. 
[original_repo](https://github.com/chapulina/dolly)

# Changes 

* Created dolly_description package
* SDF File  
    * Changed wheels pose 
    * 2 caster wheel 
    * Changed robot dimentions 
    * Changed laser range finder configuration  
* Created urdf files 

## Packages

This repository contains the following packages:

* `dolly`: Metapackage which provides all other packages.
* `dolly_follow`: Provides node with follow logic.
* `dolly_gazebo`: Robot model, simulation world and launch scripts for Gazebo-classic.
* `dolly_description`: Robot model URDF file, robot state publisher .

### From source

Install instructions for Ubuntu Bionic.

1. Install at least one simulator,
   [Gazebo](http://gazebosim.org/tutorials?cat=install) or
   [Ignition](https://ignitionrobotics.org/docs/citadel/install)

1. Install the appropriate ROS 2 version as instructed
   [here](https://index.ros.org/doc/ros2/Installation/Linux-Install-Debians/).

1. Clone Dolly, choose the branch according to your ROS distro:

        mkdir -p ~/ws/src
        cd ~/ws/src
        git clone https://github.com/chapulina/dolly -b <distro>

1. Install dependencies:

        cd ~/ws
        rosdep install --from-paths src --ignore-src -r -y \
            --skip-keys=ignition-math6 \
            --skip-keys=ignition-msgs5 \
            --skip-keys=ignition-transport8 \
            --skip-keys=ignition-gazebo3

    > **Tip**: On Ubuntu Focal, there's no need to skip keys.

1. Build and install:

        cd ~/ws
        colcon build

## Run

### Gazebo-classic

If you had Gazebo installed when compiling Dolly's packages, Gazebo support
should be enabled.

1. Setup environment variables (the order is important):

        . /usr/share/gazebo/setup.sh
        . ~/ws/install/setup.bash

    > *Tip*: If the command `ros2 pkg list | grep dolly_gazebo` comes up empty
      after setting up the environment, Gazebo support wasn't correctly setup.

1. Launch Dolly in a city (this will take some time to download models):

        ros2 launch dolly_gazebo dolly.launch.py world:=dolly_city.world

1. Launch Dolly in an empty world:

        ros2 launch dolly_gazebo dolly.launch.py world:=dolly_empty.world

  
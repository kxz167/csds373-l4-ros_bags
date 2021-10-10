# CSDS 373 Lab 4: Ros Bags

## Completed by Team 2: 

Kris Zhao (kxz167)\
Sanhita Kumari (sxk1409)\
Michael Koltisko (mek169)

## Important information:

### Development:

Developement was done in Ros Melodic for Ubuntu 18.04 installed natively on hardware.

## Ros Package:

### Name:

```
team2_ros_bags
```

### Dependencies:

This package depends on two other packages that should be installed into the same workspace (cloned into `catkin_ws/src`).

- `navvis_descriptions` by Kris Zhao (kxz167)
    - Found at: `https://github.com/cwru-courses/csds373_f21_kxz167_l2_navvis_descriptions`
- `glennan_maps`
    - Found at: `https://github.com/cwru-eecs-373/maps_glennan`

### Package directory structure:
- team2_ros_bags (from github)
    - bags (downloaded pre-recorded bags)
        - glennan_5_basic_short.bag (ignored)
        - glennan_5_basic.bag (ignored)
    - config (rviz configuration)
        - laser_topic_config.rviz
    - launch (new launch files)
        - navvis_descriptions_link.launch
        - ros_bags.launch
    - urdf (modified robot description)
        - navvis_imu.xacro
    - CMakeLists.txt
    - package.xml
    - README.md

### Important Notes:
- Launch files:
    - While the assignment called for modifications to the previous lab package, Dr Lee has mentioned that making a copy of the primary launch file and making the edits within this package was satisfactory. `navvis_descriptions_link.launch` represents the modified launch file from previous laboratories and provides a modular link into past packages without modifying them.
- RVIZ Visualization:
    - The robot LaserScan displays have been modified to have a `decay time` of 1 second. I found this provides the best representation of the environment around the robot.
    - There are a couple pre-specified views that aid in visualizing the 3D enviroment around the robot.

## Installation:

### Ros installation:

Make sure that ros melodic was installed into /opt following the installation procedure listed in the [wikis](http://wiki.ros.org/melodic/Installation/Ubuntu).

Then proceed to source ROS so that your shell is ROS aware:

```
source /opt/ros/melodic/setup.bash
```

### Package pre-requirements:
Before installing the team2_ros_bags package, prepare the workspace with the two other required components.

#### glennan_maps

Open a terminal in the `catkin_ws/src` directory. Then perform the following commands:

```
git clone git@github.com:cwru-eecs-373/maps_glennan.git
```

#### navvis_descriptions

Open a terminal in the `catkin_ws/src` directory. Then perform the following commands:

```
git clone git@github.com:cwru-courses/csds373_f21_kxz167_l2_navvis_descriptions.git
```

### Installing the package:

After the dependencies can be loaded, the package can also be cloned into the `catkin_ws/src`:

```
git clone git@github.com:cwru-courses/team2_ros_bags.git
```

Then, all the packages can be built after navigatin to `catkin_ws`:

```
catkin_make
```

And the shell can be made aware of the built packages:

```
source devel/setup.bash
```

### Loading the bags:

As all bag files have been ommitted from the github repository, they need to be downloaded and placed into the `bags` directory following the package structure and naming listed above. They can be found at:

```
https://drive.google.com/drive/u/1/folders/1ptmPrQc8g12GmbfNCklQ2fOF5rFum46-
```

## Running:
Once all of the packages and files have been installed as specified above, the visualizations can be launched. The following possibilities have been provided:

1. Broadcasting Bags (GUI or not)
    - Options: use --clock by default, re-broadcast, no gui default.
2. Broadcasting the map.
3. Launching the visualization
    - Options: use external clock by default
    - Launch map
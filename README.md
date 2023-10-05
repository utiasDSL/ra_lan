# Range-aided Localization and Navigation
This repository hosts other repositories targeted towards range-aided localization and navigation.

## Dependencies
The main dependencies are ROS for communication and [GTSAM](https://github.com/borglab/gtsam) for locaization.

1. Installation instructions for ROS can be found here: [ROS Noetic instllation](http://wiki.ros.org/noetic/Installation/Ubuntu).

2. Install necessary dependencies.
```
sudo apt-get install libboost-all-dev
sudo apt-get install cmake
```

3. We require a slightly modified version of GTSAM:
```
git clone https://github.com/abhigoudar/gtsam.git -b custom_feature
cd gtsam
mkdir build
cmake ..
make check
make install
```

### Setup ROS workspace

1. Setup a ROS workspace and clone the necessary ROS dependencies:
```
mkdir -p ~/catkin_ws/src
cd ~/catkin_ws/src
git clone https://github.com/utiasDSL/ra_lnc.git
cd ra_lnc
git submodule init && git submodule update
```

2. Build the code
```
cd ~/catkin_ws
catkin_make -DCMAKE_BUILD_TYPE=RelWDebInfo
```

## [Range-aided localization](https://github.com/utiasDSL/ra_sam)
This repository contains core localization algorithms. Instructions on running the algorithms can be found in the corresponding repository: [link](https://github.com/utiasDSL/ra_sam)


## Range-aided navigation
Coming soon


## Known issues
1. In some cases, after installing GTSAM, `libmetis-gtsam.so` might not be found during roslaunch, resulting in `ra_sam` node ending abruptly. This can be addressed by updating the library path:
   ```
   echo export LD_LIBRARY_PATH="$LD_LIBRARY_PATH:/usr/local/lib" >> ~/.bashrc
   source ~/.bashrc
   ```

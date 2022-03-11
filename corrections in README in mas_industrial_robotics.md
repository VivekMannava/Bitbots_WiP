# 1. TODO: update readme.md file using/with ssh [Link](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent)

#### Error: 

```
Cloning into 'mas_industrial_robotics'...
git@github.com: Permission denied (publickey).
fatal: Could not read from remote repository.

Please make sure you have the correct access rights
and the repository exists.

```

While cloning the mas_insudtrial_robotics the command given below wont work: 

```
git clone git@github.com:b-it-bots/mas_industrial_robotics.git
```


#### Solution:  

- so clone the repo directly using this command  
`git clone https://github.com/b-it-bots/mas_industrial_robotics.git`


-----

# 2. Done

#### Error:

```
ERROR: the following packages/stacks could not have their rosdep keys resolved
to system dependencies:
rosplan_planning_system: No definition of [python-yaml] for OS version [focal]
```

#### Solution:

Reference: [Official ROS Noetic Migration webpage](http://wiki.ros.org/action/fullsearch/noetic/Migration?action=fullsearch&context=180&value=linkto%3A%22noetic%2FMigration%22)

- For rosplan_planning_com error -- modify the package.xml file in 
`catkin_ws/src/ROSplan/ros_planning_system/package.xml` 

change the last line from 

```
 <run_depend>python-yaml</run_depend> 
 ```
 
 to 

 ```
  <run_depend>python3-yaml</run_depend> 
```
-----

# 3. Done (created issue on  b-it-bots/mas_industrial_robotics git repo)

#### Error:

To avoid Cmake warnings

#### Solution: 

Reference: [Official ROS Noetic Migration webpage](http://wiki.ros.org/action/fullsearch/noetic/Migration?action=fullsearch&context=180&value=linkto%3A%22noetic%2FMigration%22)

- Change all `cmake_minimum_required(VERSION 2.8.3)` to `cmake_minimum_required(VERSION 3.0.2)` in CMakeLists.txt files

- Change all `xacro.py` to `xacro` in launch files 

- Change in all `setup.py` files,
from
`from distutils.core import setup`  
to
`from setuptools import setup`

-----

# 4.Done

#### Error:

```
error: #error PCL requires C++14 or above
```

#### Solution:

Reference: [Link](https://github.com/PointCloudLibrary/pcl/issues/2968)

- Change line number #4 to `add_compile_options(-std=c++14)`  in the file `catkin_ws/src/mas_industrial_robotics/mir_perception/mir_ppt_detection/CMakeLists.txt`
- Change line number #1, cmake_minimum_required version from `2.8.3` to `3.0.2`

-----

# 5. Done

#### Error:

```
error: ‘CvMemStorage’ was not declared in this scope
   34 |     CvMemStorage* storage = cvCreateMemStorage(0);
```

```
error: ‘CV_BGR2GRAY’ was not declared in this scope
   20 |     cv::cvtColor(image, gray_image, CV_BGR2GRAY);
```

#### Solution:

Reference: [Link](https://stackoverflow.com/a/11604986/6920365)

In files 
`catkin_ws/src/mas_industrial_robotics/mir_perception/mir_cavity_detector/common/src/cavity_finder.cpp`

- Add line `#include <opencv2/imgproc/imgproc_c.h>`

-----

# 6. Done (change to python_orocos official git repo instead of b-it-bit)

#### Error:

For python_orocos_kdl,
```
CMake Error at /opt/ros/noetic/share/catkin/cmake/empy.cmake:30 (message):
  Unable to find either executable 'empy' or Python module 'em'...  try
  installing the package 'python3-empy'
```

#### Solution:

Reference: [python-orocos-kdl github repo link](https://github.com/orocos/orocos_kinematics_dynamics.git)

- For `python_orocos_kdl`, pull latest changes from the official git repo,

  then go to `catkin_ws/src/orocos_kinematics_dynamics/python_orocos_kdl`, then run

      - `git remote add upstream https://github.com/orocos/orocos_kinematics_dynamics.git`

      - `git pull upstream master`

      - go to  `pybind11`  directory, run  `git submodule update --init --recursive`

      - Build the package, if error comes up then go to  `catkin_ws/build` and delete `python_orocos_kdl` directory

-----

# 7. Done

#### Error:

```
Errors     << youbot_driver_ros_interface:make /home/kvnptl/catkin_ws/logs/youbot_driver_ros_interface/build.make.000.log     
make[2]: gksudo: Command not found
make[2]: *** [CMakeFiles/youbot_driver_ros_interface.dir/build.make:160: /home/kvnptl/catkin_ws/devel/.private/youbot_driver_ros_interface/lib/youbot_driver_ros_interface/youbot_driver_ros_interface] Error 127
make[2]: *** Deleting file '/home/kvnptl/catkin_ws/devel/.private/youbot_driver_ros_interface/lib/youbot_driver_ros_interface/youbot_driver_ros_interface'
make[1]: *** [CMakeFiles/Makefile2:303: CMakeFiles/youbot_driver_ros_interface.dir/all] Error 2
make: *** [Makefile:141: all] Error 2
```

#### Solution:

Reference: [Link](https://askubuntu.com/a/1192202/922137)

In file `catkin_ws/src/youbot_driver_ros_interface/CMakeLists.txt`, change line 44, `set(SUDO_COMMAND gksudo)`, to `set(SUDO_COMMAND pkexec)`

-----

# 8. Done

#### Error:

```
make[3]: python: Command not found
make[3]: * [Makefile.tarball:12: lama_planner] Error 127
make[2]: * [CMakeFiles/lama_planner.dir/build.make:57: CMakeFiles/lama_planner] Error 2
make[1]: * [CMakeFiles/Makefile2:276: CMakeFiles/lama_planner.dir/all] Error 2
make: * [Makefile:141: all] Error 2
```

#### Solution:

Reference: NA

- In the file `catkin_ws/src/lama_planner/Makefile.tarball`, change line number #12, to `python3 fast-downward/build.py`

# 9. Done

#### Error:

```
mcr_perception_tools: Cannot locate rosdep definition for [mcr_object_recognition_bounding_box]
```

#### Solution

Reference: NA

- Comment `<run_depend>mcr_object_recognition_bounding_box</run_depend>` in `catkin_ws/src/mas_perception/mcr_perception_tools/package.xml` 
- Comment `mcr_object_recognition_bounding_box` under catkin_package in `catkin_ws/src/mas_perception/mcr_perception_tools/CMakeLists.txt`

1. FLAG = 1
# Error
```
mcr_perception_tools: Cannot locate rosdep definition for [mcr_object_recognition_bounding_box]
```
## Solution
- Comment `<run_depend>mcr_object_recognition_bounding_box</run_depend>` in `/src/mas_perception/mcr_perception_tools/package.xml` and also comment `mcr_object_recognition_bounding_box` in `/src/mas_perception/mcr_perception_tools/CMakeLists.txt`

2. 
# Error
```
mir_object_recognition: Cannot locate rosdep definition for [mir_pointcloud_object_recognition_models] 
mir_object_recognition: Cannot locate rosdep definition for [mir_rgb_object_recognition_models]
```
## Solution
- Copy the mir_perception_models folder from catkin_ws to the src folder of the new workspace

3. FLAG = 1
# Error
```
In file included from /usr/include/pcl-1.10/pcl/pcl_macros.h:77,
                 from /usr/include/pcl-1.10/pcl/PCLHeader.h:10,
                 from /usr/include/pcl-1.10/pcl/point_cloud.h:47,
                 from /home/tharun/Desktop/temp/noetic_catkin_ws/src/mas_industrial_robotics/mir_perception/mir_ppt_detection/include/mir_ppt_detection/min_distance_to_hull_calculator.hpp:5,
                 from /home/tharun/Desktop/temp/noetic_catkin_ws/src/mas_industrial_robotics/mir_perception/mir_ppt_detection/src/min_distance_to_hull_calculator.cpp:1:
/usr/include/pcl-1.10/pcl/pcl_config.h:7:4: error: #error PCL requires C++14 or above
    7 |   #error PCL requires C++14 or above

```
## Solution

- Change line number #4 to `add_compile_options(-std=c++14)`  in the file `catkin_ws/src/mas_industrial_robotics/mir_perception/mir_ppt_detection/CMakeLists.txt`
- Change line number #1, cmake_minimum_required version from `2.8.3` to `3.0.2`


4. 
# Error
```
CMake Error at /opt/ros/noetic/share/catkin/cmake/empy.cmake:30 (message):
  Unable to find either executable 'empy' or Python module 'em'...  try
  installing the package 'python3-empy'
```
## Solution
- previous correction file
5. 
# Error
```CMake Error at /opt/ros/noetic/share/catkin/cmake/empy.cmake:30 (message):
  Unable to find either executable 'empy' or Python module 'em'...  try
  installing the package 'python3-empy'
```
## Solution
previous correction file

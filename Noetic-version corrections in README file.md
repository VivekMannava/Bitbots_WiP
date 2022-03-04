# Error
```
mcr_perception_tools: Cannot locate rosdep definition for [mcr_object_recognition_bounding_box]
```
## Solution
- Copy the mcr_object_recognition_bounding_box from already created catkin ws and paste it in the noetic_catkin_ws/src/mas_perception/

# Error
```
noetic_catkin_ws/src/mas_industrial_robotics/mir_perception/mir_cavity_detector/common/src/cavity_finder.cpp: In member function ‘std::vector<std::__cxx11::basic_string<char> > CavityFinder::recognize2DCavities(const cv::Mat&, cv::Mat&, std::vector<cv::Mat>&, const std::vector<cv::Point_<float> >&)’:
/home/tharun/Desktop/temp/noetic_catkin_ws/src/mas_industrial_robotics/mir_perception/mir_cavity_detector/common/src/cavity_finder.cpp:84:43: error: ‘CV_BGR2GRAY’ was not declared in this scope
   84 |     cv::cvtColor(small_image, gray_image, CV_BGR2GRAY);
```
## Solution
- To the file `noetic_catkin_ws/src/mas_industrial_robotics/mir_perception/mir_cavity_detector/common/src/cavity_finder.cpp` Add line 
`#include <opencv2/imgproc/imgproc_c.h>`

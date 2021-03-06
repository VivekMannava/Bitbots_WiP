# Initial setup

## To source everything on opening a terminal

1. open ~/.bashrc - `nano ~/.bashrc`
2. In the bashrc file add `source <path of catkinws from home>`
3. Make sure your pc is connected to `b-it-bots` wifi
4. In bashrc, To export ros_master - `export ROS_MASTER_URI=http://<ip_address:port>`
5. To add ssh for robot - `alias <any_name>="ssh robocup@<ip_address>`
6. After adding the above line, save and source the bashrc - `source ~/.bashrc`
7. In your pc open /etc/hosts - `nano /etc/hosts
8. Add the ip address of robot and its name
9. In the robot open /etc/hosts - `nano /etc/hosts`
10. Add the ip address of your pc and its name

# To control manipulator

1. Login to the robot using ssh : `ssh robocup@<ip_address>` and enter password
2. Source the setup.sh in the catkin workspace
3. Launch brinup - `roslaunch mir_bringup robot.launch`
4. Launch pregrasp planner - `roslaunch mir_planning_bringup robot.launch`
5. Run the command - `rosrun moveit_commander moveit_commander_cmdline.py`
6. Run - `use arm_1`
7. Then run predefined commands like - `go candle`, `go folded`, `go look_at_workspace`

# Waypoint trajectory generation
1. Login to the robot using ssh : `ssh robocup@<ip_address>` and enter password
2. Source the setup.sh in the catkin workspace
3. Launch brinup - `roslaunch mir_bringup robot.launch`
4. Launch pregrasp planner - `roslaunch mir_planning_bringup robot.launch`
5. In your pc - export ros master : `ROS_MASTER_URI=http://192.168.1.114:11311`. Here replace the ip address of the respective robot
6. Then in your pc launch pose mock up gui - `roslaunch mir_pregrasp_planning pose_mock_up_gui.launch`. It will open a gui window to set pose to be reached. Eg: x= 0.450, y=0.125, z=0.95 (This pose can be achieved)
7. In robot run the command - `rostopic pub /pregrasp_planner_node/event_in std_msgs/String "data: 'e_start'" -1`
8. In robot run the command - `rostopic pub /waypoint_trajectory_generation/event_in std_msgs/String "data: 'e_start'" -1`
9. If it shows error as "unable to transform to base_link" then run `rostopic pub /static_transform_publisher_node/event_in std_msgs/String "data: 'e_start'"`


## Barrier tape detection
1. Run `roslaunch mir_planning_bringup robot.launch`
2. Run `rostopic pub /mir_perception/barrier_tape_detection/event_in std_msgs/String "data: 'e_start'"` , instead of "e_start", try "e_reset" ,"e_stop"
3. Visualise it in rviz by subscriping to "Laserscan"-topic:"/barrier_tape/scan_<front/back>" and "Image"-topic:"mir_perception/<front/back>_camera/barrier_tape_detection/debug_image"


# Whole body motion calculator

1. run bringup - "roslaunch mir_bringup robot.launch
2. launch planning pringup - `roslaunch mir_planning_bringup robot.launch`
3. To set base_link_static run - `rostopic pub /static_transform_publisher_node/event_in std_msgs/String "data: 'e_start'"`
4. launch pose mock up gui in your pc : `roslaunch mir_pregrasp_planning pose_mock_up_gui.launch`
5. In robot publish pregrasp_planner event in - `rostopic pub /pregrasp_planner_node/event_in std_msgs/String "data: 'e_start'"`
6. Then publish whole body motion controller event in to move - `rostopic pub /wbc/event_in std_msgs/String "data: 'e_start'"`

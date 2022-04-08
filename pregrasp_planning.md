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

## To source everything on opening a terminal

1. open ~/.bashrc - `nano ~/.bashrc`
2. In the bashrc file add `source <path of catkinws from home>`
3. In bashrc, To export ros_master - `export ROS_MASTER_URI=http://<ip_address:port>`
4. To add ssh for robot - `alias <any_name>="ssh robocup@<ip_address>`

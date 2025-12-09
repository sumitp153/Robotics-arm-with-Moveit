<img width="1758" height="969" alt="Screenshot 2025-12-07 232735" src="https://github.com/user-attachments/assets/7a332fe5-fd0c-41a1-af03-aa3d54d27388" />
# Robotics-arm-with-Moveit
This repository features a custom robotic arm integrated with MoveIt for motion planning and control. It includes a URDF/xacro robot model, MoveIt configuration (planning groups, joints &amp; links), RViz visualization, and demo motion plans with joint and pose goals — perfect for students and beginner roboticists learning the MoveIt.
This project launches a custom robotic arm in ROS2 with:
--A robot model 🦾
--MoveIt for motion planning 🎯
--ros2_control for controlling joints ⚙️
--RViz to see the robot visually 👀
my_robot_bringup/
 ├── launch/           # Launch files
 │   └── my_robot.launch.xml
 ├── config/           # Controllers setup
 │   └── ros2_controllers.yaml
 ├── CMakeLists.txt    # Build instructions
 └── package.xml       # Dependencies information
 Open a terminal and run:

source ~/ros2_ws/install/setup.bash
ros2 launch my_robot_bringup my_robot.launch.xml
FOR MOVEIT CONFIG THIS IS GUIDE 
What does this package do?
This package allows your robot arm to:
1.Connect to MoveIt
2.Plan a path to reach a target position
3.Execute robot motion inside simulation
4.Try different goal types (Named Goal / Joint Goal / Pose Goal)
Everything is implemented inside one file:
src/test_moveit.cpp
How the Code Works:-
1️⃣ Node is created → ROS2 starts
2️⃣ MoveIt connects to the “arm” planning group
3️⃣ It sets movement speed
4️⃣ It defines a target position in space
5️⃣ It asks MoveIt to plan a valid path
6️⃣ If planning succeeds → Robot executes the path
7️⃣ ROS shuts down gracefully
And the folder test_moveit.cpp
Contains robot movement code using MoveIt                                                             
2>CMakeLists.txt
Compiles program & finds dependencies
3>package.xml
Defines required packages like rclcpp & MoveIt
How to Build
Inside your ROS2 workspace:
cd ~/ros2_ws
colcon build --packages-select my_robot_commander_cpp
Then source your workspace:
source install/setup.bash



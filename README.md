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


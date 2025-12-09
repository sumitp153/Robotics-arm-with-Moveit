Welcome! 👋
**LEVEL 1**
This project helps you launch your custom robotic arm in ROS2 with:
A robot model
-MoveIt for motion planning.
-ros2_control for controllers️.
-RViz to see the robot visually.
-Even if you are a beginner, don’t worry — this README explains everything clearly!
What this package does:-
When you run this package:
1}It loads the robot model (URDF/Xacro)
2}It publishes the robot’s joint states to update the robot in RViz
3}It loads the robot controllers (arm + gripper)
4}MoveIt starts to plan robot motions
5}RViz opens so you can see and test motion planning
All of these steps happen automatically through the launch file
📍 (my_robot.launch.xml)

 **What Each File Does**
*my_robot.launch.xml* -->> Tells ROS2 what to start -->> Robot model, controllers, MoveIt & RViz all launch here 
*package.xml* -->> Lists required ROS packages -->> Makes sure nothing is missing when building the package
*CMakeLists.txt* -->> Helps build + install files -->> Ensures launch/config are available after build   
*ros2_controllers.yaml* -->> Configures arm & gripper controllers -->> Required for moving robot joints
**IMP**
Open a terminal and run:
source ~/ros2_ws/install/setup.bash
ros2 launch my_robot_bringup my_robot.launch.xml
Then you will be able to arm robotics structure <img width="1213" height="884" alt="Screenshot 2025-12-09 185558" src="https://github.com/user-attachments/assets/9e9225d3-2658-485d-b4ce-512e74817208" />

**LEVEL 2**
My Robot Commander C++ wit MoveIt + ROS2
--This package contains a simple C++ program to control a robotic arm using MoveIt in ROS2.
--It helps beginners understand how to write a MoveIt motion-planning program in C++
What does this package do?
-This package allows your robot arm to:
1. Connect to MoveIt
2. Plan a path to reach a target position
3.Execute robot motion inside simulation
4.Try different goal types (Named Goal / Joint Goal / Pose Goal)
What Each File Does???
test_moveit.cpp >>Contains robot movement code using MoveIt
CMakeLists.txt >>Compiles program & finds dependencies
package.xml >>Defines required packages like rclcpp & MoveIt

How to Build
Inside your ROS2 workspace:
type this in terminal 
cd ~/ros2_ws
colcon build --packages-select my_robot_commander_cpp
Then source your workspace:
source install/setup.bash
How to Run:-
Make sure your robot + MoveIt + RViz are already running (e.g., using your bringup launch).
Then run:
ros2 run my_robot_commander_cpp test_moveit
Your robot should plan and move to the pose goal automatically then you will see <img width="1216" height="872" alt="image" src="https://github.com/user-attachments/assets/137a9baf-6f4b-4ccb-876e-a71487d3ac87" />





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

**LEVEL 3**

URDF/Xacro files --	Define the physical structure of the robot (arm + gripper + links + joints)
RViz config --Opens RViz with correct robot display settings
Launch file --	Shows the robot and lets you move each joint manually
What does each file do?
my_robot.urdf.xacro -->	Main robot model that combines arm + gripper
arm.xacro -->	Contains robotic arm structure joints & links
gripper.xacro -->	Defines fingers / gripper mechanism
common_properties.xacro -->	Shared parameters like materials, colors
my_robot.ros2_control.xacro	--> ros2_control configuration for future hardware support
display.launch.xml -->	Open robot in RViz and allow joint control
display.launch.xml -->	Open robot in RViz and allow joint control
urdf_config.rviz -->	Pre-setup RViz view for your robot
CMakeLists.txt -->	Installs urdf, rviz & launch folders during build
package.xml -->	Defines package basics & build system

How to Launch Robot in RViz
After building your workspace, run:
source ~/ros2_ws/install/setup.bash
ros2 launch my_robot_description display.launch.xml
then you will able to see <img width="1919" height="1079" alt="image" src="https://github.com/user-attachments/assets/cde38ae2-1468-4090-841a-10d4d1fcac8a" />

**LEVEL4**
Editing MoveIt Configuration
You can edit the MoveIt setup using:
put this in terminal 
ros2 launch my_robot_moveit_config setup_assistant.launch.py
then you can see this <img width="1165" height="753" alt="image" src="https://github.com/user-attachments/assets/991f7c8e-1026-40e5-85ef-94945944dfe3" />

Here you can:
--Add planning groups
--Add end effectors
--Fix robot self-collisions
--Configure controllers

Folder Contents (What Each Launch File Does)???
spawn_controllers.launch.py -->This file starts the robot’s controllers so MoveIt can actually move the joints.
static_virtual_joint_tfs.launch.py-->Publishes a virtual transform between the robot and the world. This helps RViz understand where the robot is placed.
demo.launch.py --> Full MoveIt demo without real hardware
setup_assistant.launch.py --> Open MoveIt Setup Assistant to edit planning config
warehouse_db.launch.py	Optional database for saving motion plans	
warehouse_db.launch --> rsp.launch.py	Loads robot model & TFs for MoveIt	
rsp.launch --> move_group.launch.py	Runs the MoveIt core services (planning + execution)	
move_group.launch --> moveit_rviz.launch.py	Launches RViz with MoveIt UI panel	
*All files load configuration using:*
MoveItConfigsBuilder("my_robot", package_name="my_robot_moveit_config")

How to Run MoveIt Demo:-
Make sure your workspace is built:
cd ~/ros2_ws
colcon build --packages-select my_robot_moveit_config
source install/setup.bash
Start the Motion Planning + RViz:
ros2 launch my_robot_moveit_config demo.launch.py
after this you will see this <img width="1919" height="1079" alt="image" src="https://github.com/user-attachments/assets/c9b3c14f-c010-47c4-b00c-83265c0f9233" />



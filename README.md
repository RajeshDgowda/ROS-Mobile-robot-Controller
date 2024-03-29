# Mobile Robot Controller
 
- TurtleBot3 Waffle is used as the robot.
- Hybrid Automata with Go To Goal, Obstacle Avoidance and Follow Wall modes governed by SlidingModeSwitch are implemented.

# Getting Started
## Prerequisites
- [ROS Melodic](http://wiki.ros.org/melodic/Installation/Ubuntu) with Gazebo-9 (Desktop-Full Install)
- [TurtleBot3](http://wiki.ros.org/turtlebot3)  package for ROS Melodic.

## Installation
1. Clone the contents of this repository to the `src/` folder of your catkin workspace.
2. Navigate to your catkin workspace folder.
3. Invoke `catkin_make` in your terminal at the root of the catkin workspace.
4. Check if the compilation was successful by invoking `rospack find mobile_robot_controller` in your terminal. It should print out the location of the `mobile_robot_controller` folder.


*\*=Goal Point*


You can try out the package by following these steps:
1. Load the Gazebo Environment. By default, the world is empty. You can add obstacles using the `insert` tab in Gazebo or changing the `turtlebot3_world.world` file in the `worlds/` folder.

    ```
    $ roslaunch mobile_robot_controller turtlebot3_world.launch
    ```

2. Start the `mr-controller` node. The default goal location is `[3.0,-2.0]`. You can change this by modifying the variable `x_d` and `y_d` in the `mr-controller.cpp` file.
    ```
    $ rosrun mobile_robot_controller mr-controller_node
    ```
3. Watch the robot go to the goal location and avoiding obstacles on the way.

## Usage
Although this package is written for the `Turtlebot3 Waffle` robot, it can be easily modified for controlling any custom mobile robot.
- The package has 2 main files: `mr-controller.cpp` and `hybridAutomata.h`. 
- The `mr-controller.cpp` file is responsible for the ROS side of the controller. It subscribes to the `/scan` topic for the Lidar Scan and `/odom` topic for the robot odometry. The node publishes on velocity commands on the `/cmd_vel` topic. All topics use the standard ROS message types. For a custom robot, these are the topics that need to be set.
- The `hybridAutomata.h` file is where the switching logic resides. The class `hybrid_automata` is what you can modify to implement your own custom switching logic.




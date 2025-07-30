# Moving Robot

## Overview
This project demonstrates a ROS 2-based simulation of a differential drive robot. The robot's state is published and visualized in RViz2, showcasing its movement in a circular path. The simulation includes joint state publishing and transformation broadcasting for visualization.

## Features
- Differential drive simulation.
- ROS 2 integration with `rclpy`.
- Visualization in RViz2 using URDF and TF.
- Circular motion simulation with configurable parameters.

## Prerequisites
Ensure the following are installed:
- ROS 2 (Humble or later).
- Python 3.
- RViz2.

## Build Instructions
To build the package, run the following command:
```bash
colcon build --symlink-install --packages-select urdf_robot
```

## Installation
Source the setup script to overlay the local workspace:
```bash
source install/setup.bash
```

## Running the Simulation
Launch the robot simulation with:
```bash
ros2 launch urdf_robot launch.py
```

## Viewing in RViz2
To view the robot in RViz2, open a new terminal and run:
```bash
rviz2 -d install/urdf_robot/share/urdf_robot/my_robot.rviz
```

## Project Structure
The following is the file structure of the project, along with descriptions of key files:

```plaintext
moving-robot/
├── src/
│   ├── urdf_robot/
│   │   ├── launch/
│   │   │   └── launch.py          # ROS 2 launch file to start the simulation.
│   │   ├── urdf/
│   │   │   └── my_robot.urdf.xml  # URDF file defining the robot's physical structure and properties.
│   │   ├── rviz/
│   │   │   └── my_robot.rviz      # RViz2 configuration file for visualizing the robot.
│   │   ├── state_publisher.py     # Python script to publish joint states and transformations.
│   │   └── CMakeLists.txt         # Build configuration for the ROS 2 package.
├── install/                       # Directory containing built files after running `colcon build`.
├── README.md                      # Documentation for the project.
└── LICENSE                        # License file for the project.
```
### Explanation of Key Files 
- launch.py: Launches the simulation environment, initializing the robot and its components.
- my_robot.urdf.xml: Defines the robot's physical structure, including links and joints, using URDF.
- my_robot.rviz: Configuration file for RViz2, specifying visualization settings for the robot.
- state_publisher.py: Publishes the robot's joint states and transformation data to ROS 2 topics for simulation and visualization.
- CMakeLists.txt: Specifies build instructions for the ROS 2 package.
## License
This project is licensed under the Apache License 2.0.


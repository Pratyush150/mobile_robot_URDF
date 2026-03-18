# Mobile Robot URDF

This repository contains a simple URDF (Unified Robot Description Format) model of a differential drive mobile robot. The model is designed for learning and basic simulation in ROS 2.

---

## Overview

The robot consists of:

* A rectangular **base chassis**
* Two **drive wheels** (left and right)
* One **caster wheel** for support
* A top-mounted **LiDAR sensor**

This structure represents a basic differential drive robot commonly used in robotics.

---

## Robot Structure

### Links

* **base_link**
  Main body of the robot (blue box)

* **lidar**
  Cylindrical sensor mounted on top (white)

* **wheel_left**
  Left driving wheel (red)

* **wheel_right**
  Right driving wheel (red)

* **caster_wheel**
  Supporting spherical wheel (green)

---

### Joints

* **lidar_joint (fixed)**
  Connects LiDAR to the top of the base

* **wheel_left_joint (continuous)**
  Allows continuous rotation of left wheel

* **wheel_right_joint (continuous)**
  Allows continuous rotation of right wheel

* **caster_wheel_joint (continuous)**
  Allows free rotation of caster wheel

---

## Dimensions

| Component    | Shape    | Size                     |
| ------------ | -------- | ------------------------ |
| Base         | Box      | 0.6 x 0.4 x 0.2          |
| Wheels       | Cylinder | radius 0.05, length 0.02 |
| LiDAR        | Cylinder | radius 0.1, length 0.2   |
| Caster Wheel | Sphere   | radius 0.05              |

---

## Coordinate Frames

* The **base_link** is the reference frame.
* All other links are positioned relative to it using joints.
* Wheels rotate around the **Y-axis**.

---

## How to Use

### 1. Place URDF in a ROS 2 package

```bash
mkdir -p ~/ros2_ws/src/mobile_robot_urdf/urdf
cp my_robot.urdf ~/ros2_ws/src/mobile_robot_urdf/urdf/
```

---

### 2. Build workspace

```bash
cd ~/ros2_ws
colcon build
source install/setup.bash
```

---

### 3. Visualize in RViz

```bash
ros2 run robot_state_publisher robot_state_publisher my_robot.urdf
```

Then open RViz:

```bash
rviz2
```

Add:

* RobotModel

---

## Notes

* This model is purely **visual** (no inertial or collision properties defined).
* Not suitable for physics simulation yet (Gazebo requires inertial tags).
* Wheel positions and axes are simplified.

---

## Future Improvements

* Add **inertial properties** for simulation
* Add **collision elements**
* Add **transmissions** for control
* Integrate with **Gazebo / Ignition**
* Add **ROS2 control plugins**

---

## Purpose

This URDF is intended for:

* Learning ROS 2 robot modeling
* Understanding links and joints
* Basic visualization in RViz

---

## Author

Pratyush150

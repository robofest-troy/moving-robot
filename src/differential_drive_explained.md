# Differential Drive Explained

## Overview
A differential drive system is a common method for controlling wheeled robots. It uses two independently driven wheels to achieve both linear and rotational movement. This explanation breaks down the math behind differential drive, making it accessible even for those without a math background.

---

## Key Concepts

### Linear and Angular Velocity
- **Linear Velocity (\(v\))**: The speed at which the robot moves forward or backward.
- **Angular Velocity (\(\omega\))**: The rate at which the robot rotates around its center.

In a differential drive system:
- The robot's movement is controlled by varying the speeds of the left and right wheels.
- The difference in wheel speeds determines the robot's rotation.

---

## Robot Geometry
The robot's geometry plays a crucial role in the calculations:
- **Wheel Radius (\(r\))**: The radius of the wheels.
- **Track Width (\(L\))**: The distance between the left and right wheels.

---

## Differential Drive Math

### Linear Velocity of Each Wheel
The linear velocity of the $$ v_{\text{left}} $$ and $$ v_{\text{right}}$$  wheels is calculated based on the robot's linear velocity (\(v\)) and angular velocity (\(\omega\)):

#### Formula:
$$
v_{\text{left}} = v - \left(\frac{\omega \cdot L}{2}\right)
$$
$$
v_{\text{right}} = v + \left(\frac{\omega \cdot L}{2}\right)
$$

#### Explanation:
- The robot's angular velocity (\(\omega\)) causes the wheels to move at different speeds.
- The left wheel slows down, while the right wheel speeds up (or vice versa) depending on the direction of rotation.

---

### Angular Velocity of Each Wheel
The angular velocity of the wheels (\(\omega_{\text{left}}\) and \(\omega_{\text{right}}\)) is derived from their linear velocities and the wheel radius (\(r\)):

#### Formula:
$$
\omega_{\text{left}} = \frac{v_{\text{left}}}{r}
$$
$$
\omega_{\text{right}} = \frac{v_{\text{right}}}{r}
$$

#### Explanation:
- The angular velocity is the rate at which the wheels rotate.
- It is calculated by dividing the linear velocity of each wheel by the wheel radius.

---

### Robot's Circular Motion
When the robot moves in a circular path, its position and orientation change over time. The following formulas describe this motion:

#### Position:
The robot's position (\(x, y\)) on the circular path is calculated using trigonometric functions:
$$
x = \cos(\theta) \cdot R
$$
$$
y = \sin(\theta) \cdot R
$$
Where:
- \(\theta\) is the robot's current angle (orientation).
- \(R\) is the radius of the circular path.

#### Orientation:
The robot's orientation (\(\theta\)) changes based on its angular velocity (\(\omega\)):
$$
\theta_{\text{new}} = \theta + \omega \cdot \Delta t
$$
Where:
- \(\Delta t\) is the time step.

---

## Example from Code

### Parameters:
- **Wheel Radius (\(r\))**: \(0.041275\) meters.
- **Track Width (\(L\))**: \(0.2658\) meters.
- **Circular Path Radius (\(R\))**: \(2.0\) meters.
- **Angular Velocity (\(\omega\))**: \(\frac{\pi}{180}\) radians per frame.

### Step-by-Step Calculation:
1. **Linear Velocity (\(v\))**:
   $$
   v = R \cdot \omega
   $$
   Substituting values:
   $$
   v = 2.0 \cdot \frac{\pi}{180} \approx 0.0349 \, \text{m/s}
   $$

2. **Wheel Linear Velocities (\(v_{\text{left}}\) and \(v_{\text{right}}\))**:
   $$
   v_{\text{left}} = v - \left(\frac{\omega \cdot L}{2}\right)
   $$
   $$
   v_{\text{right}} = v + \left(\frac{\omega \cdot L}{2}\right)
   $$
   Substituting values:
   $$
   v_{\text{left}} = 0.0349 - \left(\frac{\frac{\pi}{180} \cdot 0.2658}{2}\right) \approx 0.0302 \, \text{m/s}
   $$
   $$
   v_{\text{right}} = 0.0349 + \left(\frac{\frac{\pi}{180} \cdot 0.2658}{2}\right) \approx 0.0396 \, \text{m/s}
   $$

3. **Wheel Angular Velocities (\(\omega_{\text{left}}\) and \(\omega_{\text{right}}\))**:
   $$
   \omega_{\text{left}} = \frac{v_{\text{left}}}{r}
   $$
   $$
   \omega_{\text{right}} = \frac{v_{\text{right}}}{r}
   $$
   Substituting values:
   $$
   \omega_{\text{left}} = \frac{0.0302}{0.041275} \approx 0.731 \, \text{rad/s}
   $$
   $$
   \omega_{\text{right}} = \frac{0.0396}{0.041275} \approx 0.960 \, \text{rad/s}
   $$

4. **Wheel Rotations**:
   Over a time step (\(\Delta t = \frac{1}{30}\) seconds), the wheel rotations are updated:
   $$
   \text{rotation}_{\text{left}} += \omega_{\text{left}} \cdot \Delta t
   $$
   $$
   \text{rotation}_{\text{right}} += \omega_{\text{right}} \cdot \Delta t
   $$

5. **Robot Position (\(x, y\))**:
   $$
   x = \cos(\theta) \cdot R
   $$
   $$
   y = \sin(\theta) \cdot R
   $$

6. **Robot Orientation (\(\theta\))**:
   $$
   \theta_{\text{new}} = \theta + \omega \cdot \Delta t
   $$

---

## Summary
The differential drive system uses simple math to control a robot's movement:
- **Linear Velocity** determines forward/backward motion.
- **Angular Velocity** determines rotation.
- By adjusting the speeds of the left and right wheels, the robot can move in straight lines, turn, or follow a circular path.

This approach is widely used in robotics due to its simplicity and effectiveness.
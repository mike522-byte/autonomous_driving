# Monocular Camera and 2D LiDAR-Based Vision System for Autonomous Navigation
This project implements a **monocular camera and 2D LiDAR-based vision system** to enable lane-following and obstacle avoidance for a **differential drive autonomous vehicle**. Developed within the **ROS framework**, the system utilizes modular nodes for perception, decision-making, and control, achieving efficient autonomous navigation.  


## Lane Tracking
![Image](https://github.com/user-attachments/assets/1f9c7c82-c445-442d-a9a6-d26b829239cd)
- A **monocular camera** captures road images, which are processed for **lane line detection** using classical computer vision techniques (e.g., **Canny edge detection, Hough transform, Perspective transform**).
- The detected lane boundaries determine the vehicle’s **differential drive kinematics**, the instantaneous steering angle is then computed and published via the control topic.

  
## Obstacle Detection and Avoidance
![Image](https://github.com/user-attachments/assets/85ea2942-973c-4a9f-9cd7-3affd045741c)
- A **LiDAR** continuously scans the environment, generating a **2Dpoint cloud** of nearby objects.  
- The obstacle avoidance node subscribes to the **LiDAR scan data**, analyzing the frontal sector to identify the nearest obstacle and its angular position.  


#### **Decision and Motion Control**  
- The control node subscribes to both **lane detection** and **obstacle detection** topics, maintaining a global state for **real-time decision-making**.  
- Depending on the active mode (lane following or obstacle avoidance), the system computes an optimal **steering angle**.  
- The final motion commands, including **mode, velocity, steering, and gear state**, are published to the actuator node for execution.  

# Monocular Camera and 2D LiDAR Fusion Vision System for Autonomous Navigation
This project implements a **monocular camera and 2D LiDAR fusion vision system** to enable lane-following and obstacle avoidance for a **differential drive vehicle**. The system consists of modular nodes for perception, decision-making, and control developed within the **ROS framework**.


## Lane Tracking
![Image](https://github.com/user-attachments/assets/1f9c7c82-c445-442d-a9a6-d26b829239cd)
- A **monocular camera** captures road images, which are processed for **lane line detection** using classical computer vision techniques (e.g., **Canny edge detection, Hough transform, Perspective transform**).
- Optimized for low computational cost and minimal memory embedded systems.
- Successfully detects lane boundaries under varied lighting conditions, including shadows, glare, and dim environments.
  
## Obstacle Detection and Avoidance
![Image](https://github.com/user-attachments/assets/85ea2942-973c-4a9f-9cd7-3affd045741c)
- A **LiDAR** continuously scans the environment, generating a **2Dpoint cloud** of nearby objects.  
- The obstacle avoidance node subscribes to the **LiDAR scan data**, analyzing the frontal sector to identify the nearest obstacle and its angular position.  


## **Decision and Motion Control**  
The control node subscribes to lane detection and obstacle detection topics, continuously updating a global state to support real-time decisions. Based on the active mode—either lane-following or obstacle avoidance, the system calculates the optimal steering angle. Finally, it publishes motion commands, including mode, velocity, steering angle, and gear state, to the actuator node for execution.

# <div align="center">IMU Integration Donkeycar Framework</div>
![image](https://github.com/WinstonHChou/winter-2024-final-project-team-7/assets/68310078/0ba1c6cb-c9e0-4cf7-905a-f5f16e6bb2ca)
### <div align="center"> MAE 148 Final Project </div>
#### <div align="center"> Team 7 Winter 2025 </div>

<div align="center">
     <img src="Images\bumblebee.png" width="800" height="600">
</div>

## Table of Contents
  <ol>
    <li><a href="#team-members">Team Members</a></li>
    <li><a href="#abstract">Abstract</a></li>
    <li><a href="#what-we-promised">What We Promised</a></li>
    <li><a href="#accomplishments">Accomplishments</a></li>
    <li><a href="#challenges">Challenges</a></li>
    <li><a href="#final-project-videos">Final Project Videos</a></li>
    <li><a href="#software">Software</a></li>
        <ul>
            <li><a href="#slam-simultaneous-localization-and-mapping">SLAM (Simultaneous Localization and Mapping)</a></li>
            <li><a href="#obstacle-avoidance">Obstacle Avoidance</a></li>
        </ul>
    <li><a href="#hardware">Hardware</a></li>
    <li><a href="#gantt-chart">Gantt Chart</a></li>
    <li><a href="#course-deliverables">Course Deliverables</a></li>
    <li><a href="#project-reproduction">Project Reproduction</a></li>
    <li><a href="#acknowledgements">Acknowledgements</a></li>
    <li><a href="#contacts">Contacts</a></li>
  </ol>

<hr>

## Team Members
Brandon Lopez - MAE  - Class of 2025 - [LinkedIn](https://www.linkedin.com/in/brandon26/) 

Francisco Garcia - ECE - Class of 2025 - [LinkedIn](https://www.linkedin.com/in/francisco-garcia-351270219/) 

Atharva Kedia - ECE - Class of 2026 - [LinkedIn](https://www.linkedin.com/in/atharvakedia/)

Bree Stram - BENG - Class of 2025 


<hr>

## Abstract
This project enhances the DonkeyCar autonomous driving framework by integrating Inertial Measurement Unit (IMU) data with GPS for more accurate path tracking. To improve localization, this project modifies the existing path.py module to incorporate IMU data (acceleration, gyroscope, and magnetometer readings). These additional sensor inputs enable sensor fusion techniques such as Kalman Filtering or Complementary Filtering, allowing for more precise position estimation.
The modifications involve:

*    Extending the CsvThrottlePath class to record IMU data alongside GPS.
*    Updating manage.py to pass IMU readings through the DonkeyCar vehicle pipeline.
*    Developing a fusion algorithm that combines GPS and IMU data to enhance path accuracy.
*    Visualizing real-time IMU-GPS data for debugging and optimization.

The result is a more robust navigation system, capable of handling GPS inaccuracies by leveraging IMU-based dead reckoning, improving path-following performance in autonomous driving applications.

<hr>

## What We Promised
### Must Have
*    Integrate GPS and IMU sensors into the DonkeyCar framework.
*    Modify the existing path recording system to log both GPS and IMU data for enhanced localization.
*    Implement a sensor fusion algorithm (e.g., Kalman Filter or Complementary Filter) to improve path accuracy using IMU and GPS.
*    Ensure the DonkeyCar can record and follow an autonomous path with improved precision.

### Nice to Have
*    Develop a real-time visualization tool to display IMU-GPS sensor data for debugging and optimization.
*    Implement basic drift correction using IMU data when GPS signal quality is low.
*    Extend the system to allow for future integration with additional sensors (e.g., LiDAR, depth cameras) for enhanced mapping and navigation.
<hr>

## Accomplishments
* SLAM development accomplished
  * It enables the robot to map an unknown environment, and to locate its position.
  * Seeed IMU setup for better localization (Extended Kalman Filter).
* Obstacle Avoidance
  * Utilize its depth sensing capabilities to generate a point cloud representation of the environment. (Rviz2 and Foxglove Studio)
  * Simple obstacle detection algorithm
<hr>

## Challenges
* Nav2 Stack is a complex but useful system for developing an autonomous robot.
* Futher Actions:
  * PointCloud Dynamic Obstacle Detection:  
    - Develop an algorithm to mark down position of obstacle group, and add them to Nav2 obstacle layer
  * Nav2 Path Planning & ROS 2 Control:  
    - Path Planning Server Development, and communication to ROS 2 Control System
<hr>

## Final Project Videos
**Click** any of the clips below to **reroute to the video**. 

#### **Mapping**

[<img src="images\mapping.webp" width="300">](https://youtu.be/1juHBhWz0MQ?si=Pjw60vCCNlXvP-IJ)

#### **Localization**

[<img src="images\localization.webp" width="300">](https://youtu.be/MX7kB6Jm7y0?si=0zmViTiaanLxiC1R)

#### **PCL Obstacle Detection**

[<img src="images\foxglove_pcl.webp" width="300">](https://youtu.be/iBNiwRAd4vU?si=_p8UwEmmzGuZwT1X)


#### Odom Frame Demo

[<img src="images\odom.webp" width="300">](https://youtu.be/PYMze0eOyS8?si=Nz3BIUGNAnoSLkpe)

#### Scan Correction Demo

[<img src="images\laser_frame.webp" width="300">](https://youtu.be/-2ELt_U10Mc?si=TWcBfC-b9EcZiGpV)

<hr>

## Software

### Overall Architecture
The project was successfully completed using the **Slam-Toolbox** and **ROS2 Navigation 2 Stack**, with a significant adaptation to the [djnighti/ucsd_robocar container](https://hub.docker.com/r/djnighti/ucsd_robocar). The adaptation allowed for seamless integration and deployment of the required components, facilitating efficient development and implementation of the robotic system.

### SLAM (Simultaneous Localization and Mapping)
- The **Slam Toolbox** proved indispensable in our project, enabling us to integrate the LD19 Lidar – firmware-compatible with the LD06 model – into the ROS2 framework. This integration allowed us to implement SLAM, empowering our robot to autonomously map its environment while concurrently determining its precise location within it. Additionally, we enhanced this capability by incorporating nav2 amcl localization, further refining the accuracy and dependability of our robot's localization system. By combining these technologies, our robot could navigate confidently, accurately mapping its surroundings and intelligently localizing itself within dynamic environments.<br>

- The **Online Async Node** from the Slam Toolbox is a crucial component that significantly contributes to the creation of the map_frame in the project. This node operates asynchronously, meaning it can handle data processing tasks independently of other system operations, thereby ensuring efficient utilization of resources and enabling real-time performance. The map_frame is a fundamental concept in SLAM, representing the coordinate frame that defines the global reference frame for the environment map being generated. The asynchronous online node processes Lidar data, and fuses this information together to construct a coherent and accurate representation of the surrounding environment.<br>

- The **VESC Odom Node** plays a pivotal role in supplying vital odometry frame data within the robotics system. This node is responsible for gathering information from the VESC (Vedder Electronic Speed Controller), and retrieves essential data related to the robot's motion, such as wheel velocities and motor commands. The odometry frame, often referred to as the "odom_frame," is a critical component in localization and navigation tasks. It represents the robot's estimated position and orientation based on its motion over time. This information is crucial for accurately tracking the robot's trajectory and determining its current pose within the environment. By utilizing the data provided by the VESC Odom Node, the system can update the odometry frame in real-time, reflecting the robot's movements and changes in its position. This dynamic updating ensures that the odometry frame remains synchronized with the robot's actual motion, providing an accurate representation of its trajectory.

<br>
<div align="center">
    <img src="images\Frames_Relationships.png" height="300"><br>
    <b>from https://answers.ros.org/question/387751/difference-between-amcl-and-odometry-source/</b><br>
    <img src="images\tf_tree.webp" height="600"><br>
    <b>Our Robot TF Tree</b><br>
</div><br>

- The **URDF Publisher** is a tool used to generate and publish Unified Robot Description Format (URDF) models within the ROS 2 ecosystem.
<br>
<div align="center">
    <img src="images\URDF.png" height="300"><br>
    <b>URDF Model of the robot</b><br>
    <img src="images\robot_on_ground.webp" height="300"><br>
    <b>Physical Robot</b><br>
</div><br>

- The **Seeed IMU Node** is used to publish IMU data Seeed Studio XIAO nRF52840 Sense. By integrating the Seeed Studio XIAO nRF52840 Sense's 6-Axis IMU and implementing an Extended Kalman Filter (Not Done), the robot gains improved localization accuracy and reduced odometry drift. The IMU provides orientation and acceleration data, complementing other sensors like wheel encoders and GPS. The Extended Kalman Filter fuses IMU and odometry measurements, dynamically adjusting uncertainties to mitigate noise and inaccuracies, resulting in enhanced navigation performance and reliability.<br>

<div align="center">
    <img src="https://github.com/WinstonHChou/winter-2024-final-project-team-7/assets/68310078/897b3a72-5760-4389-8faf-1873f8b8709a" height="300"><br>
    <b><a href="https://youtu.be/QrzTvfnHyqE">Seeed IMU Demo</a></b>
</div><br>

- The **Scan Correction Node** becomes particularly useful when there are specific sections of Lidar data that we wish to exclude from being collected by SLAM. This node allows us to define undesired ranges within the Lidar data and effectively filter them out, ensuring that only relevant and accurate information is utilized in the SLAM process. This capability enhances the overall quality and reliability of the generated map by preventing erroneous or irrelevant data from influencing the mapping and localization algorithms.
<br>
<div align="center">
    <img src="images\Non-filtered_map.png" height="300"><br>
    <b>Before filtered</b><br><br>
    <img src="images\Filtered_map.png" height="300"><br>
    <b>After filtered</b>
</div>

### Obstacle Avoidance
We utlized the OAK-D Lite depth camera to implement obstacle avoidance functionality within the ROS2 framework. Leveraging its depth sensing capabilities, we utilized the camera to generate a point cloud representation of the environment. The program logic is straightforward: the robot detects obstacles by identifying areas where the height is less than 2 meters (customizable) in front of it. If an object is detected within this distance threshold, the robot dynamically adjusts its trajectory to avoid collision, typically by making a turn. This simple yet effective approach allows the robot to navigate safely through its environment, reacting to potential obstacles in real-time to ensure smooth and obstacle-free movement.
<br>
<div align="center">
    <img src="images\rviz_pcl.jpg" height="300"><br>
    <b>PointCloud Visualization with Rviz2</b><br><br>
    <img src="images\foxglove_pcl.webp" height="300"><br>
    <b>PointCloud Visualization with Foxglove Studio</b>
</div><br>

We integrated the DepthAI ROS package into our ROS2 setup to enable object detection functionality. Within the package, we utilized the provided YOLO (You Only Look Once) neural network setup for object detection. This configuration allowed our robot to detect objects in its environment in real-time using deep learning techniques. By leveraging the YOLO neural network, our robot could accurately identify and classify various objects, enhancing its perception and autonomy for effective navigation in dynamic environments.
<br>
<div align="center">
    <img src="images\6_yolo_v3_tf_object_detection.webp" height="300"><br>
    <b>yolo_v3_tf_object_detection</b><br><br>
</div>

<hr>

## Hardware 

* __3D Printing:__ Camera Stand, Jetson Nano Case, GPS Plate, Lidar Mount
* __Laser Cut:__ Base plate to mount electronics and other components.

__Parts List__

* Traxxas Chassis with steering servo and sensored brushless DC motor
* Jetson Nano
* WiFi adapter
* 64 GB Micro SD Card
* Adapter/reader for Micro SD Card
* Logitech F710 controller
* OAK-D Lite Camera
* LD19 Lidar (LD06 Lidar)
* VESC
* Point One GNSS with antenna
* Anti-spark switch with power switch
* DC-DC Converter
* 4-cell LiPo battery
* Battery voltage checker/alarm
* DC Barrel Connector
* XT60, XT30, MR60 connectors
* SparkFun OpenLog Artemis (DEV-16832)

*Additional Parts used for testing/debugging*

* Car stand
* USB-C to USB-A cable
* Micro USB to USB cable
* 5V, 4A power supply for Jetson Nano

### __Mechanical Design Highlight__

__Base Plate__
<div align="center">
<img src="Images\Base.png" height="350"> 
</div>
__Camera Stand__

Camera Stand components were designed in a way that it's an adjustable angle and height This design feature offers versatility and adaptability, ensuring optimal positioning of the camera to capture desired perspectives and accommodate various environments or setups.

<div align="center">
<img src="Images\Isometric View.png" height="350">
</div>
__GPS Plate__
<div align="center">
<img src="Images\GPS_Stand.png" height="300">
</div>
__Circuit Diagram__

Our team made use of a select range of electronic components, primarily focusing on the OAK-D Lite camera, Jetson NANO, a GNSS board / GPS, and an additional SparkFun OpenLog Artemis (DEV-16832) for IMU recording.
<div align="center">
<img src="Images\circuit_diagram.png" width="900" height="600">
</div>
<hr>

## Course Deliverables
Here are our autonomous laps as part of our class deliverables:

* DonkeySimulator Autonomous Laps: https://youtu.be/k4IBv1xpOJo
* DonkeySimulator Autonomous (Remote Server) Laps: https://youtu.be/6-3juWUL2Wc
* Lane Following Autonomous Laps: https://youtu.be/3gb0JS8ZidY
* GPS Autonomous Laps: https://youtu.be/-sfzaUusQJ4
* OpenCV Autonomous Laps: https://youtu.be/kRCSMZZy2x0

Weekly Project Status Update and Final Presentation:  
* [Google Slides](https://docs.google.com/presentation/d/1NeJFdNSlSz2XIg3V0_UelSlysrG5QyMZ0-aBoINpIxE/edit#slide=id.g335b997d1d9_0_5)
[![Google Slides](Images/updates.png)](https://docs.google.com/presentation/d/1NeJFdNSlSz2XIg3V0_UelSlysrG5QyMZ0-aBoINpIxE/edit#slide=id.g335b997d1d9_0_5)
<hr>

## Project Reproduction
If you are interested in reproducing our project, here are a few steps to get you started with our repo:

<ol>
  <li>Follow instuctions on <a href="https://docs.google.com/document/d/1YS5YGbo8evIo9Mlb0J-w2r3bZfju37Zl4UmdaN2CD2A/">UCSD Robocar Framework Guidebook</a>, <br> pull <code>devel</code> image on your JTN: <code>docker pull djnighti/ucsd_robocar:devel</code></li>
  <li>
      <code>sudo apt update && sudo apt upgrade</code><br>
      (make sure you upgrade the packages, or else it won't work; maybe helpful if you run into some error <url>https://askubuntu.com/questions/1433368/how-to-solve-gpg-error-with-packages-microsoft-com-pubkey</url>)<br>
      check if <code>slam_toolbox</code> is installed and launchable:<br>

## Acknowledgements
Special thanks to Professor Jack Silberman and both TA's Winston and Alexander for delivering the course!  
Thanks to Aryan on Triton AI giving suggestions and supporting on our project!  

**Programs Reference:**
* [UCSD Robocar Framework](https://gitlab.com/ucsd_robocar2)

README.md Format, reference to [winter-2024-final-project-team-7](https://github.com/UCSD-ECEMAE-148/winter-2024-final-project-team-7)

<hr>

## Contacts

* Francisco Garcia - frgarcia@ucsd.edu | frgarciaa1@gmail.com | [LinkedIn](https://www.linkedin.com/in/francisco-garcia-351270219/)
* Brandon Lopez - blopez@ucsd.edu | brandon.lopez.miramontes@gmail.com | [LinkedIn](https://www.linkedin.com/in/brandon26/) 
* Atharva Kedia - atkedia@ucsd.edu | [LinkedIn](https://www.linkedin.com/in/atharvakedia/)
* Bree Stram - bstram@ucsd.edu

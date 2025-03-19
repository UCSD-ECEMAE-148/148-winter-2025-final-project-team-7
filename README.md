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
    <li><a href="#hardware">Hardware</a></li>
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
* Sparkfu
  * It enables the robot to map an unknown environment, and to locate its position.
  * Seeed IMU setup for better localization (Extended Kalman Filter).
* Obstacle Avoidance
  * Utilize its depth sensing capabilities to generate a point cloud representation of the environment. (Rviz2 and Foxglove Studio)
  * Simple obstacle detection algorithm
<hr>

## Challenges
* Establishing I2C communication between the BNO085 IMU and the Jetson Nano was difficult due to permission conflicts and dependency issues, requiring extensive troubleshooting.
* Integrating the IMU with the DonkeyCar Framework proved challenging because the existing codebase was fragmented. We struggled to determine the correct approach for adding a new component to log data and utilize it in real-time processing within the framework.
* We aimed to fuse GPS data with the IMU to improve path accuracy, but implementing sensor fusion was complex due to synchronization issues and the need for an effective filtering method, such as a Kalman filter or complementary filtering.
<hr>

## Final Project Videos
**Click** any of the images below to **reroute to the video**. 
<div align="center">
     
#### **IMU Data Reading**

[<img src="Images\IMU_Data_Reading.png" width="500">](https://youtu.be/060TtfnaJ5Q)

#### **IMU Real Time Data Plotting**

[<img src="Images\IMU_Real_Time_Data.png" width="500">](https://youtu.be/KJVEJFGC0Ec)
</div>

<hr>

## Software

### Overall Architecture
The project was successfully completed using the **Slam-Toolbox** and **ROS2 Navigation 2 Stack**, with a significant adaptation to the [djnighti/ucsd_robocar container](https://hub.docker.com/r/djnighti/ucsd_robocar). The adaptation allowed for seamless integration and deployment of the required components, facilitating efficient development and implementation of the robotic system.

### SLAM (Simultaneous Localization and Mapping)


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
If you are interested in reproducing our project, here are a few steps to get you started:
* Jetson Nano Configuration [Link](https://docs.google.com/document/d/1TF1uGAFeDARNwbPkgg9xg4NvWPJvrsHW2I_IN9dWQH0/edit?tab=t.0#heading=h.b0ghgbcoid6m)
* Jetson Xavier Configuration [Link](https://docs.google.com/document/d/1mXgN9DcAj30HAsbfrHNCP-YEYqKWPTbcUssRI1Xab1A/edit?tab=t.0#heading=h.qfnzubgcn5p6)
* OpenCV CUDA Accelerated [Link](https://docs.google.com/document/d/1HX2zmjbVsyLnliEQ8wp97Y453g5qNAYHWtFQiKQ0elA/edit?tab=t.0#heading=h.uieq3bo7w218)
* UCSD Robocar Framework [Link](https://docs.google.com/document/d/1Onft0sIWhEd9UH7fItJ0atC1hKnxpTxKKmUFHtqC-sA/edit?tab=t.0)

Follow instruciton on UCSD Robocar Framework [Link](https://docs.google.com/document/d/1Onft0sIWhEd9UH7fItJ0atC1hKnxpTxKKmUFHtqC-sA/edit?tab=t.0) pull `devel` image on your Jetson Nano:
```
docker pull djnighti/ucsd_robocar:devel
```
```
sudo apt update
```
```
sudo apt upgrade
```



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

<hr>

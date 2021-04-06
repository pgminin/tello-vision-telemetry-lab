# Tello Vision Telemetry Lab

![2d motion reconstruction gif](/doc/img/2d-motion-reconstruction/2d-track-orbit.gif)

![3d motion reconstruction gif](/doc/img/3d-motion-reconstruction/3d-track-orbit.gif)

## Topics of interest
- Data Analysis and Visualization
- Algorithm learning, coding, and development
- Sensor Fusion
- Realtime Vision-based Control
- Object/Person Detection and tracking
- 3D Person localization
- Drone Odometry
- 2D/3D Motion Reconstruction
- ...

## How it works
- Experiment: fly your Tello with Tello Vision 1D Android App 
- Download Tello Vision Telemetry as a .txt file to your PC
- Process telemetry and learn using Python, Jupyter Notebook, Matlab, or Excel
- Experiment some more

![Tello Vision Telemetry Lab Cover Figure](/doc/img/tello-vision-telemetry-lab-cover.jpg)

## How to download telemetry data on your PC
- From Tello Vision 1D App:
1. At the end of your fligths with the Tello Vision 1D App stop the video live and telemetry recording using the "VIDEO OFF" button. 
2. Go to Statistics using the "STATS" button. 
3. Share last flight telemetry pressing the "SHARE TELEMETRY" button.
4. Send an email to yourself with the telemetry file as an attachment.
5. Download the attachment to your pc.
- As an alternative use the provided telemetry demo files.
You can play around with Tello Vision Telemetry Lab even without a Tello!

## Get the Tello Vision 1D Android App (it's free!)
[Tello Vision 1D Android App on Google Play](https://play.google.com/store/apps/details?id=com.vision.pgminin.tellovision1d) 

### NOTE
#### This Project is intended as a simple learning platform and it was developed as a tool for rapid prototyping and development of algorithms for the Tello Vision 1D Android App.

## Telemetry Data Explanation <a class="anchor" id="data-explanation"></a>

### timestamp 
Data timestamp (milliseconds).

### trackMode
Tracking Mode coded as follows:

0 -> None, 
1 -> Spotlight,
2 -> Follow,
3 -> Orbit, 
4 -> Profile, 
5 -> Party,
6 -> Forward with person avoidance.

### telSeqId
An incremental number used to manually mark flight phases. Use the Tello Vision 1D app button "Tel ID ++" to mark sequences of interest.

### personCount
Detected person count.

### personConfidence
Detection confidence for the foreground person (%).

### faceXPx, faceYPx, faceRadiusPx
Detection center and apparent face radius for the foreground person (pixels).

### angle_err
Horizontal angle error between the detected face and the center of the image (degrees)

### estimatedDistance
3D Distance between the drone and the detected face (cm).

### estimatedXPos, estimatedYPos, estimatedZPos
estimatedDistance decomposed in the (X,Y,Z) drone frame reference (cm).

X is in the drone right direction, Y is in the drone down direction, Z is in the drone forward direction.

### Uyaw, Uz, Ux, Uy
Speed commands sent to the drone (approximated deg/s and cm/s)

### pitch, roll, yaw
Eulerian angles from the IMU (degrees).

### vx, vy, vz
Velocities from the IMU (decimeter/s).

X is drone's initial forward direction, Y is drone's initial right direction, Z is drone's down direction.

### tof
Drone height from the Time Of Flight sensor (cm).

### batt
Drone battery level (%).

### temp
Drone temperature (°C).

## Telemetry Data Filtering
Displaying many minutes of telemetry data all in the same plot can be difficult to interpret.
The key is to filter and select data to make the analysis simpler.
It is possible to leverage Python powerful Pandas Data Analysis Library and Tello Vision Telemetry Lab data columns definition.
For example, the trackMode column classifies data by the flight tracking mode active in each moment.
Autonomous tracking modes are coded as follows:
0 -> None, 
1 -> Spotlight,
2 -> Follow,
3 -> Orbit, 
4 -> Profile, 
5 -> Party,
6 -> Forward with person avoidance.

The following lines  of code:

*tofFollow=(tof[trackMode==2])*

*tofOrbit=(tof[trackMode==3])*

select only Time of Flight data of the Follow Mode and the Orbit mode giving the possibility to plot them in two separate figures.

## Jupyter Notebook Demo Code

### Sensors Inspector (01_inspect_sensors.ipynb)

![Time of flight Figure](/doc/img/sensors/tof.jpg)![Battery Figure](/doc/img/sensors/battery.jpg)
![IMU pitch and roll Figure](/doc/img/sensors/pitch-roll.jpg)![IMU velocity Figure](/doc/img/sensors/vx-vy-vz-trackMode.jpg)

Inspect IMU, tof, temperature, battery sensors telemetry.

### Control Inspector (02_inspect_control.ipynb)

![Person Estimated Distance Figure](/doc/img/control/estimatedDistance.jpg)![Control Speed Command Uz Figure](/doc/img/control/Uz.jpg)

### Person detection Inspector (03_inspect_person_detection.ipynb)

![Face radius Figure](/doc/img/detection/face-radius.jpg)![Radius confidence Figure](/doc/img/detection/radius-confidence.jpg)

Inspect person detection telemetry.

### 2D/3D Vision for Spotlight tracking mode (04_spotlight_3d_vision.ipynb)

![Polar map 2D Figure](/doc/img/spotlight3d/polar-map-2d.jpg)![Polar map 3D figure](/doc/img/spotlight3d/polar-map-3d.jpg)

2D/3D person localization referred to drone position (polar map).

### Drone IMU Odometry (05_drone_imu_odometry.ipynb)

![2D odometry and camera pose figure](/doc/img/IMU-odometry/odometry-camera-pose.jpg)![3D odometry and camera pose figure](/doc/img/IMU-odometry/odometry-camera-pose-tof.jpg)

IMU velocities integration using telemetry timestamp. 2D drone tracks, IMU yaw and tof heigth data fusion for camera pose and 3D tracks.

### 2D Motion Reconstruction (06_2d_motion_reconstruction.ipynb)

![2D odometry animation](/doc/img/2d-motion-reconstruction/2d-track-orbit.gif)![2d odometry and person localization figure](/doc/img/2d-motion-reconstruction/2d-motion-reconstruction-trackMode-5.jpg)

2D Person Localization in Drone IMU Odometry tracks.

### 3D Motion Reconstruction (07_3d_motion_reconstruction.ipynb)

![3D odometry animation](/doc/img/3d-motion-reconstruction/3d-track-orbit.gif)

3D Person Localization in Drone IMU Odometry tracks.









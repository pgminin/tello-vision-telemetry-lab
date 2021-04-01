# Tello Vision Telemetry Lab

## Topics of interest
- Data Analysis and Visualization
- Algorithm learning, coding and development
- Sensor Fusion
- Realtime Vision based Control
- Object/Person Detection and tracking
- 3D Person localization
- Drone Odometry
- 2D/3D Motion Reconstruction
- ...

## How it works
- Experiment: fly your Tello with Tello Vision 1D Android App 
- Download Tello Vision Telemetry as a .txt file to your PC
- Process telemetry and learn using Python, Jupyter Notebook, Matlab or Excel
- Experiment some more

## How to download telemetry data on your PC
- From Tello Vision 1D App:
1. At the end of your fligth with Tello Vision 1D App stop the video live and telemetry recording using "VIDEO OFF" button. 
2. Go to Statistics using "STATS" button. 
3. Share last flight telemetry pressing "SHARE TELEMETRY" button.
4. Send an email to yourself with telemetry file as an attachment.
5. Download the attachment to your pc.
- As an alternative use the provided telemetry demo files.
You can play around with Tello Vision Telemetry Lab even without a Tello!

# NOTE
## This Project is intended as a simple learning platform and it was developed as a tool for rapid prototyping and development of algorithms for the Tello Vision 1D Android App.

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
Incremental number used to manually mark flight phases. Use Tello Vision 1D app button "Tel ID ++" to mark sequences of interest.

### personCount
Detected person count.

### personConfidence
Detection confidence for the foreground person (%).

### faceXPx, faceYPx, faceRadiusPx
Detection center and apparent face radius for the foreground person (pixels).

### angle_err
Horizontal angle error between the detected face and the center of the image (degrees)

### estimatedDistance
3D Distance between drone and the detected face (cm).

### estimatedXPos, estimatedYPos, estimatedZPos
estimatedDistance decomposed in the (X,Y,Z) drone frame reference (cm).

X is in the drone right direction, Y is in the drone down direction, Z is in the drone forward direction.

### Uyaw, Uz, Ux, Uy
Speed commands sent to the drone (approximated deg/s and cm/s)

### pitch, roll, yaw
Eulerian angles from the IMU (degrees).

### vx, vy, vz
Velocities from the IMU (decimeter/s).

X is drone initial forward direction, Y is drone initial right direction, Z is drone down direction.

### tof
Drone heigth from the Time Of Flight sensor (cm).

### batt
Drone battery level (%).

### temp
Drome temperature (°C).




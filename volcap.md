
## **Volumetric Capture 4020 Documentation**

**Steps to perform Volumetric Capture in 4020:**
 1. Turn the PC in room 4020 on, and login using your PID. (the name in front of your VT email address)
 2. The Software you will need:
    - Azure Kinect Viewer
    - [DepthKit](Depthkit.md)
    - [Git Bash](Gitbash.md)
    - Unity
    - [Adobe Premiere](adobe.md)
    - [Reaper (Optional)](reaper.md)
  
  **Azure Kinect Viewer**
1. To confirm that the device is streaming data, follow these steps:
2. Launch the Azure Kinect Viewer
5. Click on "Open Device" in the top left corner of the window.
      <p align="center"> <img src="images/AZV/open Device.PNG" width="300 height="350"> </p>
7. Select "Start" from the dropdown menu.
8. The device should start streaming data
9. Verify that the tool visualizes each sensor stream:
    - Infrared camera: Visualize Active Brightness, a grayscale IR brightness image.
      <p align="center"> <image src="images/AZV/inf cam.PNG" width="300 height="350"> </p>
    - Depth camera: View the colorized depth data representation.
      <p align="center"> <image src="images/AZV/depth cam.PNG" width="300 height="350"> </p>
    - Color camera: You can control RGB camera settings from the configuration window during the streaming.
      <p align="center"> <image src="images/AZV/color cam control.PNG" width="300 height="350"> </p>
    - IMU Data: Monitor the accelerometer and gyroscope for rotational movement.
    - Microphones Data: Observe the sound representation. 
 10. Now you are done with Azure Kinect Viewer
 11. Next step: [Go to Depthkit](Depthkit.md)

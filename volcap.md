
## **Volumetric Capture 4020 Documentation**

**Steps to perform Volumetric Capture in 4020:**
 1. Turn the PC in room 4020 on, and login using your PID. (the name in front of your VT email address)
 2. The Software you will need:
    - Azure Kinect Viewer
    - DepthKit
    - Git Bash
    - Unity
    - Adobe Premiere
    - Reaper (Optional)
  
  **Azure Kinect Viewer**
1. To confirm that the device is streaming data, follow these steps:
2. Launch the Azure Kinect Viewer
      <p align="center"> <image src="images/AZV/AKV logo.PNG" width="70 height="80"> </p>
5. Click on "Open Device" in the top left corner of the window.
      <p align="center"> <image src="images/AZV/open Device.PNG" width="250 height="300"> </p>
7. Select "Start" from the dropdown menu.
8. The device should start streaming data
9. Verify that the tool visualizes each sensor stream:
    - Infrared camera: Visualize Active Brightness, a grayscale IR brightness image.
    - Depth camera: View the colorized depth data representation.
    - Color camera: You can control RGB camera settings from the configuration window during the streaming.
    - IMU Data: Monitor the accelerometer and gyroscope for rotational movement.
    - Microphones Data: Observe the sound representation. 
 10. Now you are done with Azure Kinect Viewer
 
 **DepthKit**
1. Next You will need to launch DepthKit (image)
2. To use the existing calibration, double-click on the project folder named "Volcap_4020". (image)
 7. Place your subject at the center marking of the room. 
	>(Please ensure that the subject avoids wearing black/ white/ glasses/ ripped clothes for the best texture output.)
	> For optimal results, it's important to remain within the marked boundaries of the room throughout the entire recording session.
 8. [If you want to record audio, please click here.]()
 9. When you are confident with your setup, click on the "Start Streaming" button under the Controls section of Depthkit. (image)
 10. You have the option to name your take under Recording Prefix.
 11. Remember to use a visual and audible cue at the beginning of each take, such as clapping your hands, to help with the syncing process. (image)
 12. In DepthKit, hit the Record button, a Diagnostics panel will be displayed. (image)
 13. After finishing your recording session, click on "End Recording" button.
 14. Click on the "Stop Streaming" button when you have finished recording. (You can refer to this [link](https://docs.depthkit.tv/docs/studio-recording) for more information)
 15. Head to the recording library tab. (image)
 16. To refine the capture, go to the Refine panel and select Enable Refinement. From there, you can proceed directly to the exporting process. Perform this refinement process for every capture from each sensor perspective. (For more information refer: [Processing Studio captures](https://docs.depthkit.tv/docs/processing-studio-captures) and [Creating Refinement masks](https://docs.depthkit.tv/docs/creating-refinement-masks)) (image)
 17. To create an asset that can be quickly placed into  the  Unity project, you can export a Multiperspective CPP Video. To do this, click on "Multiperspective CPP Video" from the export drop-down menu. Then, go to the location where the files were saved and copy the generated files from Depthkit. ( For more information refer to this link : [Exporting](https://docs.depthkit.tv/docs/exporting)) (image)

**Git Bash**
3. For best results make sure that you Convert your Combined Per Pixel Asset export in 3x2 columns and rows.
 20. Open Git Bash
		- Enter ‘cd desktop’.
		-   Type ‘python ./DepthkitCPPToRows.py’
		-   Leave a space and drag and drop your metadata file.
		-   Leave a space and drag and drop the image sequence folder.
		-   Leave a space and drag and drop a new folder for the export directory. This can be named anything you like.
		-   Press enter and you will see the new image sequence and metadata file write to the export directory.
	
**Demo Command :** 
>python ./DepthkitCPPToRows.py
[metadata file: /c/Users/nehasurana/Desktop/metadata.txt ]
[image sequence folder: /c/Users/nehasurana/Desktop/image_sequence_folder ]
export directory: /c/Users/nehasurana/Desktop/final_folder_directory]
	
**Adobe Premiere**
1. Open Adobe Premiere to synchronize your audio and video files. (image)
	>For more information refer to this link: [[AdobePremiereDemo.mp4](https://drive.google.com/file/d/1SWDYjDCX9tPOOgktKO-BIUdQUT021DJS/view?usp=share_link) or [Embedding audio in Depthkit assets](https://docs.depthkit.tv/docs/embedding-audio)]
2. To sync your audio and video files in Adobe Premiere Pro, follow these steps:
	-   Import both your audio and video files into your project panel.
	-   Drag both files onto your timeline.
	-   Select both the audio and video clips by holding down the shift key and clicking on each clip.
	-   Right-click on one of the selected clips and choose "Synchronize" from the context menu.
	-   In the Synchronize dialog box, make sure that "Audio" is selected as the synchronization point.
	-   Click "OK" to synchronize your clips.
	-   Check the synced clips by playing the timeline to make sure that the audio and video are in sync. (image for each)

3. You can encode your video files using FFmpeg by following this tutorial: [[Image Sequence encoding](https://docs.depthkit.tv/docs/asset-encoding)]. 
4. Open the command prompt and type these commands:

	**For Video Encoding:**
	> ffmpeg -i [C:\Users\nehasurana\Desktop\location of your video file] -c:v libx264 -x264-params mvrange=511 -c:a  aac -b:a 320k -shortest -vf scale='min(4096,iw)':'min(ih,4096)':force_divisible_by=2:out_color_matrix=bt709:out_range=full,setsar=1:1 -colorspace bt709 -color_primaries bt709 -color_trc bt709 -color_range pc -b:v 5M -pix_fmt yuv420p [ name of your final output file].mp4

	**For Image Sequence Encoding :**
    

	> ffmpeg -r 30 -f image2 -start_number 0 -i [ location of your first image sequence padded by “%06d”.png e.g: D:\Volcap_4030_Final\Exports\welcome3x2\TAKE_Welcome02_27_11_58_41_Export_04_03_13_20_49%06d.png] -c:v libx264 -x264-params mvrange=511 -c:a  aac -b:a 320k -shortest -vf scale='min(4096,iw)':'min(ih,4096)':force_divisible_by=2:out_color_matrix=bt709:out_range=full,setsar=1:1 -colorspace bt709 -color_primaries bt709 -color_trc bt709 -color_range pc -b:v 5M -pix_fmt yuv420p [ name of your output file].mp4

	 



 

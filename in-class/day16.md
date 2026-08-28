---
title: "CA Lecture: Light Fields // Camera Calibration // Studio Time"
toc_sticky: true
toc_data:
  - title: Today
    link: in-class/day16/#today
  - title: For Next Time
    link: in-class/day16/#for-next-time
  - title: CA Lecture - Light Fields
    link: in-class/day16/#ca-lecture-light-fields
  - title: Camera Calibration
    link: in-class/day16/#camera-calib
---

# WORK IN PROGRESS! CHECK BACK FOR UPDATES!


## Today
* CA Lecture: 3D Dynamic Reconstruction for Soft Corals with Light Fields
* Camera Calibration (For Your Consideration)
* Studio Time

## For Next Time
* Work on the [Broader Impacts assignment Part 2](../assignments/broader_impacts), due on **November 4th at 7PM** 
  * In class discussions on **Monday November 3rd**
* Work on the [Machine Vision Project Document](../assignments/computer_vision_project).
    * Project Shareouts will be **Monday November 10th in class**
    * Project Materials are due on **Tuesday November 11th at 7PM**
* Consider whether there is [feedback you'd like to share about the class](https://forms.gle/giCwA1pkr4y3e4T37)


## CA Lecture: 3D Dynamic Reconstruction for Soft Corals with Light Fields
Today we're going to hear from Vivian on current research work she is conducting on using a unique camera configuration to generate high quality 3D reconstructions of dynamic objects, applied to ecological studies of coral reefs. This is an example of how some of the concepts you're exploring in your machine vision projects can be adapted to frontier research questions. You can follow along [with slides here](https://docs.google.com/presentation/d/1UxAYL3YCDhmglfxgEfTMvhmOqyRLfkY2P92FtGlfPwc/edit?slide=id.g38e10bf72ea_0_13#slide=id.g38e10bf72ea_0_13).

## Camera Calibration (For Your Consideration)
One of the _essential_ practical aspects of machine vision is camera calibration: knowing the intrinsic and extrinsic parameters of your imaging system. 

* _Intrinsic Calibration_ refers to the sensor and lens characteristics of your imaging system; calibrating here allows you to correct for image distortions. This is a "projective transformation" between your camera coordinates and your image pixel coordinates.
* _Extrinsic Calibration_ refers to the way in which your imaging system is set up. For instance, if you have two cameras, this would include their relative poses to one another. This is a "rigid transformation" between your world coordinates and your camera coordinates.

### Pinhole Camera Model 
The "pinhole camera model" is among the most commonly used for performing basic camera calibration. These [slides for today](https://docs.google.com/presentation/d/1jbJkz_u_BJDghaP0nMZa_itgEjCnrFBh6eht8NBBD38/edit?usp=sharing) go through the key details. Please use this as a resource!

### Camera Calibration Resources
Here are several different tutorials on how to do (intrinsic) camera calibration in ROS2:

* [Using the Camera Calibration module](https://navigation.ros.org/tutorials/docs/camera_calibration.html)
* [Using the Nav2 module](https://docs.ros.org/en/rolling/p/camera_calibration/tutorial_mono.html)
* [A Medium Post walk-through](https://medium.com/starschema-blog/offline-camera-calibration-in-ros-2-45e81df12555)

You can also checkout the [brief OpenCV demo](https://docs.opencv.org/4.x/dc/dbb/tutorial_py_calibration.html) if you'd like to just test this out on your webcam.

Note that you'll need checkerboards for this! You can (and should!) print your own; this [calib.io pattern generator](https://calib.io/pages/camera-calibration-pattern-generator) is an excellent resource!

### Additional Resources
* An article on <a-no-proxy href="https://www.ri.cmu.edu/pub_files/pub2/willson_reg_1993_1/willson_reg_1993_1.pdf"> What is the Center of an Image? </a-no-proxy> 
* <a-no-proxy href="https://www.youtube.com/watch?v=nOQvjG7Jbao"> Youtube lecture on pinhole camera model </a-no-proxy> (includes a fun demo on finding the focal length of your phone camera at around 7:30)
* MatLab has a nice [high-level explainer](https://www.mathworks.com/help/vision/ug/camera-calibration.html) with follow-on articles worth a look. 


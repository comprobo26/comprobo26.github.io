---
title: "Keypoints and Descriptors // Studio Time"
toc_sticky: true
toc_data:
  - title: Today
    link: in-class/day15/#today
  - title: For Next Time
    link: in-class/day15/#for-next-time
  - title: Kaypoints and Descriptors
    link: in-class/day15/#keypoints-and-descriptors
---

# WORK IN PROGRESS! CHECK BACK FOR UPDATES!


## Today
* Keypoints, Descriptors, and Keypoint Matching
* Studio Time

## For Next Time
* Work on the [Broader Impacts assignment Part 2](../assignments/broader_impacts), due on **November 4th at 7PM** 
  * In class discussions on **Monday November 3rd**
* Work on the [Machine Vision Project Document](../assignments/computer_vision_project).
    * Project Shareouts will be **Monday November 10th in class**
    * Project Materials are due on **Tuesday November 11th at 7PM**
* Consider whether there is [feedback you'd like to share about the class](https://forms.gle/giCwA1pkr4y3e4T37)

## Human-Robot Interaction: Search and Rescue Continued

### Setting Standards for SAR
In the US, the Federal Emergency Management Agency (FEMA), Homeland Security, and the Department of Defense are among the largest customers of SAR robots. In partnership with NIST (the National Institute of Standards and Technology), the guidelines for an effective/useable SAR system for urban environments has been defined ([you can read more here](https://www.nist.gov/system/files/documents/el/isd/ks/Prelim_Requirements_Report.pdf)) and covers the following:

* Human-System Interaction (23 requirements)
* Logistics (10 requirements)
* Operating Environment (5 requirements)
* System (physical robot) (65 requirements; 32 of which are for sensing)

One of the fascinating things about these requirements is that "Human-System Interaction" primarily covers the _robot operator_ but not the interaction with a possible human rescuee. In your small groups, consider the following questions from the perspective of a NIST engineer tasked with setting requirements for a SAR robot (I recommend picking one or two to focus on):

* What would/should official standards for Human-System Interaction cover for the rescuee of a SAR robot? 
  * You may want to consider: interfaces (virtual, sensory, or physical); accessibility; meta-safety; inclusivity...
* How would these standards interact with your robot's sensors? Algorithms?
  * You may want to consider: role of automation/autonomy; consequences of perceptual limitations; edge-cases for perception choices; introduction of bias (implicit or explicit); verifiability; explainability...
* Who should be involved in co-designing this set of standards for this group of stakeholders?
  * The current standards were set based on several workshops with experts in the field (peep the list in the linked report above...notice anything interesting about this group?)
* What tests would need to be designed to assess whether a robot met these standards?


## Keypoints, Descriptors, and Keypoint Matching
These [slides on keypoints and descriptors](https://docs.google.com/presentation/d/1ULK3Rt7bfijohKa5ZSGI-LJDIPumeGCdq-fGGaJNczg/edit?usp=sharing) provide a detailed look at this topic. As many projects in the class will likely build on the notion of keypoints/descriptors, we highly recommend using this as a resource to learn more!

To get a brief impression of keypoints, descriptors, and matching, there is some demonstration code available in the [``class_activities_and_resources`` repository](https://github.com/comprobo25/class_activities_and_resources) under the subdirectory ``keypoints_and_descriptors``. Since this directory is not a ROS package, you do *NOT* need to worry about running ``colcon build``. Remember to pull from upstream!

### Keypoint-based Tracking

You can use keypoints to track an object as it moves around in an image.  Go to the ``keypoints_and_desciptors`` directory and run the following command.

```bash
$ ./track_meanshift_keypoints.py
```

You should see an image from your computer's webcam appear on the screen.  Click the image once to pause it, a second time to mark the upper-left corner of the tracking image, and a third and final time to mark the lower-right corner of the tracking image.

At this point you should be able to move the object around and the program will attempt to track its position.

> What do you notice about the keypoints that are selected? What changes when you adjust the "corner threshold" and why? What changes when you adjust the "ratio threshold" and why?

> Look at the code for this example. What types of features are being used? What happens if you change them to one of the other common feature types (e.g., ORB -- check the slides and OpenCV documentation for others!)


### Matching Keypoints
You can use keypoints to match corresponding points in two images.  Go to the ``keypoints_and_desciptors`` directory and run the following command.

```bash
$ ./match_keypoints.py
```
Note that as you move the sliders around, you'll need to click on the image to refresh it.

> What do you notice about the keypoints that are selected? What changes when you adjust the "corner threshold" and why? What changes when you adjust the "ratio threshold" and why?

> Look at the code for this example. What types of features are being used? What happens if you change them to one of the other common feature types (e.g., ORB -- check the slides and OpenCV documentation for others!)


### Visualizing SIFT Descriptors
You can visualize the SIFT descriptors, which we used in the previous two demos. Go to the ``keypoints_and_desciptors`` directory and run the following command.

```
$ ./visualize_sift.py
```

This visualization is showing the SIFT descriptors as described in the slides.  The only thing that it doesn't do is rotate the descriptor relative to the dominant orientation.  Draw in the left pane by clicking and dragging, make sure that you understand why the SIFT descriptor changes the way that it does.  Note, that in order to reset the sketch, you need to hit the spacebar.

> What are the advantages of using SIFT descriptors? When might you not want to use a SIFT descriptor?


### Machine Learning-based Tracking
You may want to try out Magic Leap's SuperGlue model for keypoint identification and tracking.  They [have a repository](https://github.com/magicleap/SuperGluePretrainedNetwork) that is pretty easy to get going with.

> Why might using learned descriptors be attractive? What are challenges associated with using these descriptors?

YOLO is another well-known learned descriptor / keypoints detector, often used for human pose estimation, that many of you are looking at for your projects. You can learn more about how it may connect to robotics [by reading academic papers](https://arxiv.org/pdf/2510.13625) in this space.
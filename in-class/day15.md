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
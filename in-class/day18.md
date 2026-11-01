---
title: "Image Segmentation // Studio"
toc_sticky: true
toc_data:
  - title: Today
    link: in-class/day18/#today
  - title: For Next Time
    link: in-class/day18/#for-next-time
  - title: Image Segmentation Basics
    link: in-class/day18/#image-seg-basics
---

## Today
* Image Segmentation
* Studio Time

## For Next Time
* Work on the [Machine Vision Project Document](../assignments/computer_vision_project).
    * Project Shareouts will be **Monday November 9th in class**
    * Project Materials are due on **Tuesday November 10th at 7PM**
* Please provide feedback and weigh-in on an extra credit opportunity! [Poll](https://forms.gle/zVMMPGQrxwBxWfj86)


## Image Segmentation Basics
During this unit we've so far discussed classical methods for parsing images and extracting metric information like keypoints, creating descriptors, and performing the correspondence task. For your consideration today, here is a brief set of materials which cover the concept of _image segmentation_, which encompasses a variety of techniques with the goal of subdividing an image into regions which may contain more than just metric information.

Image segmentation techniques are commonly separated into three groups:
* **Instance Segmentation**: each pixel is assigned a "belonging instance" (e.g., every pedestrian in an image is separately sorted)
* **Semantic Segmentation**: each pixel is assigned a "belonging class" (e.g., a landscape is divided into sand, rock, tree, grass, sky, cloud, etc.)
* **Panoptic Segmentation**: each pixel is assigned a "belonging class" and individual instances of a class are further identified.

Each technique yields a slightly different output, which is important to consider when thinking about what downstream work you would like to do. For instance, in an object tracking scenario, being able to distinguish different types of objects, and identify a specific instance, may be important. Alternatively, in simple mapping, it may be enough to know the mixture of classes of objects in an environment.

Like everything in machine vision, there are classical and learned techniques that can be adopted to perform image segmentation.

### Classical Techniques
These classical techniques for image segmentation will likely look familiar to you -- they often leverage the same processes that we've been using to identify keypoints!

**Thresholding and Clustering** Using simple thresholding values on an image, we can isolate regions that "look similar" and assign them to various classes (by simply keeping track of what pixels meet certain criteria). Histogram methods are a variation on this technique. Enhancing this idea, we can process an image using a clustering algorithm, for instance, [K-Means Clustering](https://www.ibm.com/topics/k-means-clustering), to assign pixels to classes.

**Edge and Contour Detection** You can sort edges in an image (detected using gradient based methods that we might apply when looking for keypoints...) in order to assist with image segmentation. Hough transforms (for lines and for circles) look at edges and use a set of criteria to determine whether a set of edges are geometric matches to a target geometry. 

**Getting Advanced** Methods like variational partitioning, topic modeling, Markov random fields, and parameteric partial-differential equations, have all been adopted for processing images and extracting regions of interest. [The Wikipedia page](https://en.wikipedia.org/wiki/Image_segmentation) on Image Segmentation gives a nice overview of each of these in turn.


Some code tutorials or documentation you might find interesting here:
* OpenCV's Python [Tutorial on the Watershed Algorithm](https://docs.opencv.org/4.x/d3/db4/tutorial_py_watershed.html)
* OpenCV's Python [Tutorial on the GrabCut Method](https://docs.opencv.org/4.x/d8/d83/tutorial_py_grabcut.html)
* A Kaggle Walkthrough of [Image Segmentation with OpenCV](https://www.kaggle.com/code/mielek/image-segmentation-with-opencv)
* Examples of implementing segmentation with [multiple OpenCV methods](https://github.com/niconielsen32/opencv-python-tutorials/blob/main/13_image_segmentation/README.md)
* [K-Means Clustering in SKLearn](https://scikit-learn.org/1.5/modules/generated/sklearn.cluster.KMeans.html)
* [Hough Line Transform in OpenCV](https://docs.opencv.org/3.4/d9/db0/tutorial_hough_lines.html)
* [Hough Circle Transform in OpenCV](https://docs.opencv.org/3.4/d4/d70/tutorial_hough_circle.html)


### Learning / AI Techniques
Often, we want to segment an image, it is because there are particular "things" we're hoping to find. Learning-based techniques have really opened the door for advanced image segmentation that allows us to select for certain objects that may be challenging to heuristically select for using classical techniques (for instance, pedestrians in a busy street scene, objects in a cluttered kitchen, or specific types of animals in an environment we're monitoring).

[MathWorks has a nice explainer](https://www.mathworks.com/solutions/image-video-processing/semantic-segmentation.html) on semantic segmentation that is absolutely worth a read, including how you can use their toolboxes to performed learned segmentation.

Learned segmentation models often make use of _convolutional neural networks_ (CNNs). If you'd like to learn more about specific architectures, [Papers with Code](https://paperswithcode.com/task/semantic-segmentation) is an excellent resource for papers + repositories + datasets you can run. 

One of the most popular modern techniques, one that many of you are considering in your projects, is [YOLO](https://www.geeksforgeeks.org/machine-learning/yolo-you-only-look-once-real-time-object-detection/) (an interesting [guide on this model here](https://roboflow.com/blog/guide-to-yolo-models)), the "You Only Look Once" learned model composed of convolutional layers that can take input imagery and output semantic labels and object bounding boxes. Understanding how YOLO works is a great starting point for anyone who is interested in getting into learning-based methods for machine vision. Let us know if you want to discuss in more detail!


## Studio
Please work with your team on your machine vision projects. Let the teaching team know if you have any questions about the demos or final materials!
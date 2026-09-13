---
title: "RoboBehaviors Debrief // Intro To State Estimation"
toc_sticky: true
toc_data:
  - title: Today
    link: in-class/day06/#today
  - title: For Next Time
    link: in-class/day06/#for-next-time
  - title: RoboBehaviors Debrief
    link: in-class/day06/#robobehaviors-debrief
  - title: Conceptual Introduction to the Particle Filter
    link: in-class/day06/#conceptual-introduction-to-the-particle-filter
  - title: Coordinate Frames and Coordinate Transforms in Robotics
    link: in-class/day06/#coordinate-frames-and-coordinate-transforms-in-robotics
---

# WORK IN PROGRESS! CHECK BACK FOR UPDATES!


## Today
* RoboBehaviors Debrief
* An Introduction to State Estimation
* Conceptual Introduction to the Particle Filter
* Studio Time

## For Next Time
* Work on the <a href="../assignments/warmup_project">the RoboBehaviors</a>.
  * The final project deliverables are due tomorrow **Tuesday 23rd at 7PM**!
  * A rubric for the project is available [on Canvas](https://canvas.olin.edu/courses/942/assignments/16078).*
* Work on the [Broader Impacts assignment Part 1](../assignments/broader_impacts), due on **September 30th at 7PM**.
  * We will have a class discussion on **Thursday Oct. 2nd**.
* Read over the description of the [Robot Localization project](../assignments/robot_localization).
  * For more reinforcement of the concepts behind the particle filter, watch this <a href="https://www.youtube.com/watch?v=aUkBa1zMKv4">video</a>.


## RoboBehaviors Debrief
While the final deliverables are still being polished, let's share-out some of what we've been learning and doing with one another. Slides are <a href="https://docs.google.com/presentation/d/1Aa63PUPe-afBzpv647Qvuj_C0xe-lIBMh9_3bc42kvs/edit?slide=id.p#slide=id.p">available here</a>.


## An Introduction to State Estimation
We're about to launch our next project into _State Estimation and Localization_. This is a very rich subfield in robotics; a <a href="https://docs.google.com/presentation/d/1IslrQmigazEP4l0cHZUHa8N8RLeWmJAn1iHkq9uQShQ/edit?usp=sharing">short presentation</a> will introduce some of the concepts and lead into our activity on a conceptual introduction to a particle filter.


## A Conceptual Introduction to the Particle Filter
How does a robot know where it is? We'll be doing an activity to introduce our next major topic in the class: robot localization. This is supposed to be a fun activity to get you thinking about the basic concepts of one tool for localization, the particle filter.

## Coordinate Frames and Coordinate Transforms in Robotics

> Likely you've encountered the notion of multiple coordinate systems before at some point in your academic career.  Depending on your path through Olin, you may already be familiar with the mechanics of how to map vectors between different coordinate systems (either in 2D or 3D).  In this exercise, you'll get a chance to refresh some of this knowledge and to also gain a conceptual understanding of how the notion of multiple coordinate systems plays out in robotics.

### `tf2` and You

We've encountered a funny logistical matter when using Rviz2 to visualize our /my_point topic -- we needed to change our "Fixed Frame" from /map to /odom. What's going on? These are two different _coordinate frames_ ROS2 uses to track a robot in a world. There are actually loads of coordinate frames we might want to be thinking about in robotics. (And you [can read more about how ROS has thought about coordinate transforms here](https://www.ros.org/reps/rep-0105.html)).

Let's get a sense for how we might encounter more coordinate transforms in ROS2 by walking through [this tutorial](https://docs.ros.org/en/humble/Tutorials/Intermediate/Tf2/Introduction-To-Tf2.html). ROS2 uses a utility called `tf2` in order to track the relationships between various entities in a world. When we walk through this tutorial, we'll be seeing how to inspect all the different transforms that are going on.

### Creating a `world` coordinate frame

Understanding the math behind what `tf2` is doing for us can be super helpful -- especially when we start thinking about debugging robot behavior, adding sensors to our robots, and interacting in increasingly complex environments.

Suppose your Neato is at position 3.0m, 5.0m with a heading of 30 degrees (where counter-clockwise rotation is positive) in a coordinate system called ``world``.  Draw a picture.  Make sure to label the axes of the ``world`` coordinate system (don't worry about the z-axis).In robotics, we frequently need to express the position of various entities (e.g., obstacles, goal locations, other robots, walls, doorways, etc.).  While we could express all of these positions in terms of the coordinate system ``world``, in many situations this will be cumbersome.

**Exercise:** Taking the Neato as an example, make a list of the coordinate systems that you feel would be convenient to define.  For each coordinate system, define its origin and give a few examples of entities that would be natural to express in that coordinate system. 

### ``base_link``

Next, we'll define ``base_link``, which will serve as our robot-centric coordinate system.  The origin of this coordinate system will be at the midpoint of the line connecting the robot's wheels.  The x-axis will point forwards, the y-axis will point to the left, and the z-axis will point up.  Update your drawing to indicate the position of the ``base_link`` coordinate axes (again, don't worry about the z-axis).

Now that we have defined our new coordinate system, we'd like to be able to take points expressed in this coordinate system and map them to the ``world`` coordinate system (and vice-versa).  In order to do this, we need to specify the relationship between these two coordinate systems.  A natural way to specify the relationship between two coordinate systems is to specify the position of the origin of one coordinate system in the other as well as the directions of the coordinate axes of one frame in the other.  Going back to our original example we can say that the coordinate axes of the Neato's ``base_link`` coordinate system are at position 3.0m, 5.0m with a rotation of 30 degrees relative to the coordinate axes of the ``world`` coordinate frame.  We usually think of this information as defining the transformation from ``world`` to ``base_link``.  It turns out that with just this information, we can map vectors between these two coordinate systems.

### From ``base_link`` to ``world``

**Exercise:** Determine the coordinates of a point located at (1.0m, 0.0m) in the ``base_link`` coordinate system in the ``world`` coordinate system.  First draw the point on the board to make sure everyone agrees what its location is.  Once you've determined your answer, how can you tell if you are right?

**Exercise:** Determine the coordinates of a point located at (0.0m, 1.0m) in the ``base_link`` coordinate system in the ``world`` coordinate system.  First draw the point on the board to make sure everyone agrees what its location is.  Once you've determined your answer, how can you tell if you are right?

**Exercise:** Determine the coordinates of a point located at (x, y) in the ``base_link`` coordinate system in the ``world`` coordinate system.  If you are having trouble operationalizing your answer in terms of equations, you can define it in terms of high-level operations (e.g., translations, rotations, etc.).


### From ``world`` to ``base_link``

There are multiple ways to tackle this one.  We think it's easiest to do algebraically (with your good-old i-hat and j-hat notation), but you can do it in terms of geometry / trigonometry too.  Don't get too hung up on the mechanics, try to understand conceptually how you would solve the problem.

**Exercise:** Determine the coordinates of a point located at (0.0m, 1.0m) in the ``world`` coordinate system in the ``base_link`` coordinate system.  First draw the point on the board to make sure everyone agrees what its location is.  Once you've determined your answer, how can you tell if you are right?

**Exercise:** Determine the coordinates of a point located at (1.0m, 0.0m) in the ``world`` coordinate system in the ``base_link`` coordinate system.  First draw the point on the board to make sure everyone agrees what its location is.  Once you've determined your answer, how can you tell if you are right?

**Exercise:** Determine the coordinates of a point located at (x, y) in the ``world`` coordinate system in the ``base_link`` coordinate system.  If you are having trouble operationalizing your answer in terms of equations, you can define it in terms of high-level operations (e.g., translations, rotations, etc.).


### Possible Notation

Sometimes, it can be helpful to lead with notation.  Other times, it can obfuscate and confuse.  Here is some notation that you could use to reason about and define coordinate systems. If this is useful to you, please go for it!

$$\begin{eqnarray}
\mathbf{p}_{/W} &\triangleq& \mbox{a point, p, expressed in coordinate system W} \\
\mathbf{p}_{/N} &\triangleq& \mbox{a point, p, expressed in coordinate system N} \\
\hat{\mathbf{i}}_{N} &\triangleq& \mbox{a unit vector in the i-hat direction of coordinate system N} \\
\hat{\mathbf{j}}_{N} &\triangleq& \mbox{a unit vector in the j-hat direction of coordinate system N} \\
\hat{\mathbf{r}}_{W\rightarrow N} &\triangleq& \mbox{a vector pointing from the origin of W to the origin of N} \\
\mathbf{r}_{W \rightarrow N / N} &\triangleq& \hat{\mathbf{r}}_{W\rightarrow N}\mbox{ expressed in coordinate system N} \\
\hat{\mathbf{i}}_{N/W} &\triangleq& \hat{\mathbf{i}}_{N}\mbox{ expressed in coordinate system W} \\
\hat{\mathbf{j}}_{N/W} &\triangleq& \hat{\mathbf{j}}_{N}\mbox{ expressed in coordinate system W}\end{eqnarray}$$


### Static Versus Dynamic Coordinate Transformations

The relationship between some coordinate systems are dynamic (meaning they change over time) and some are static (meaning they are constant over time).

**Exercise:**  Assume that our Neato robot can move about in the ``world`` by using its wheels.  Is the relationship between ``world`` and ``base_link`` static or dynamic?  Given the coordinate systems you came up with earlier, list some examples of coordinate system relationships that are static and some that are dynamic.


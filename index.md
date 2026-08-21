---
layout: splash
title: "A Computational Introduction to Robotics 2026"
header:
  overlay_image: "website_graphics/robo_splash.jpg"
  overlay_color: "#000"
  overlay_filter: "0.4"

feature_row_TODO:
  - image_path: https://img.youtube.com/vi/MFL4gd2IMm8/0.jpg
    alt: "A thumbnail image for a video.  The text QEA Olin College of Engineering appears on a textured blue background"
    title: "Key Features of QEA"
    excerpt: "QEA is a highly interdisciplinary, integrated course for teaching technical content."
    url: "#course-philosophy"
    btn_label: "More details about QEA"
    btn_class: "btn--primary"
  - image_path: website_graphics/faces_collage.png
    alt: "A 5 by 5 grid of face images with labels of whether each of them are smiling."
    title: "Computational Platform"
    excerpt: "Students use Python as a programming language during this module.  Use the button below to see sample code and other materials."
    url: "#supporting-resources"
    btn_label: "Supporting Resources"
    btn_class: "btn--primary"
  - image_path: website_graphics/eigface1_stretched.jpg
    alt: "A sample Eigenface calculated from the class dataset."
    title: "Module Overview"
    excerpt: "The module introduces fundamental ideas in linear algebra through a deep dive into creating a facial recognition system."
    url: "#module-details"
    btn_label: "Module Details"
    btn_class: "btn--primary"

feature_row_robot:
  - image_path: website_graphics/neato_overview.jpeg
    alt: "A picture of a Neato robotic vacuum with a custom remote control interface based on Raspberry Pi"
    excerpt: "The documentation describes both how to connect to the the physical robot or a simulator and how to build your own customized Neato.

    ### Student Facing Documentation\n
    * [Setting up Your Computer](How to/setup_your_environment), [Using the Neatos](How to/use_the_neatos), and [Using the Turtlebot 4](How to/use_the_turtlebot4)\n
    * [Useful Resources](useful_resources) and [Sample Code](Sample_code/sample_code)\n

    ### Teaching Team Documentation\n
    * [Shopping list](How to/shopping_list) and [Platform Conversion Instructions](How to/Platform Conversion Instructions.pdf)\n
    * [Raspberry Pi Setup](How to/setup_raspberry_pi)"

feature_row_warmup_project:
  - image_path: website_graphics/barrel_follow.gif
    alt: "The Neato robot in a simulated world tracking a barrel"
    excerpt: "
   The first project, RoboBehaviors and FSMs (finite state machines) provides a scaffolded assignment for students to get up to speed with important concepts in ROS through implementing compelling behaviors on a robot.  The project emphasizes the establishment of good practices such as debugging techniques and visualization.

    ### Supporting Documents

* [RoboBehaviors and FSMs Assignment Document](assignments/warmup_project)\n
* [Class-generated Tips and Tricks](https://docs.google.com/document/d/1x3NjmOhbd8oq020Vt0etsZLnNtvLpK2AasJFirAi96Q/edit?usp=sharing)\n
* [Troubleshooting](How to/troubleshoot)\n"

feature_row_robot_localization_project:
  - image_path: website_graphics/rviz_mapping_frontpage.png
    alt: "The Neato robot in the simulated Guantlet world with a small number of laser scans collected to localize."
    excerpt: "
   The Robot localization project is a scaffolded assignment for students to learn about the particle filter algorithm. Along the way they will learn some basics of Bayesian inference and some new ROS tools and workflows.

    ### Supporting Documents

* [Robot Localization Assignment Document](assignments/robot_localization)\n
* [Dude, where's my robot? A Localization Challenge for Undergraduate Robotics](https://dl.acm.org/doi/abs/10.5555/3297863.3297895)\n"

feature_row_robots_society:
  - image_path: website_graphics/real_robots.png
    alt: "A collage of robots including AUV Sentry, Asimo, Waymo car, a coffee maker, factory assembly arms, and a Boston Dynamics Spot."
    excerpt: "
   By virtue of being embodied, robots can literally change the world. Daily in-class activities and a 3-part assignment examine the impacts and implications of robotic systems and algorithmic choices made in their design.

    ### Supporting Documents

* [3-Part Broader Impacts Project](assignments/broader_impacts)\n"

feature_row_computer_vision_project:
  - image_path: website_graphics/keypoint_matching.png
    alt: "An example of a keypoint matching algorithm working on indoor images"
    excerpt: "
The machine vision project is an open-ended project on using computer vision in the context of robotics.

    ### Supporting Documents

* [Machine Vision Project Document](assignments/computer_vision_project)\n"

feature_row_final_project:
  - image_path: website_graphics/final_projects_collage_2024.png
    alt: "A series of 3 images, moving clockwise starting on the top left, two Neatos coordinating paths around one another, an RViz diagram for a Neato moving quickly through unknown space, and a 6DOF manipulator playing chess."
    excerpt: "
   The final project is an open-ended project that lets students explore a robotics topic and algorithms in depth.

    ### Supporting Documents

* [Final Project Assignment Document](assignments/final_project)\n
* [2024 Final Projects Showcase](final_project_showcase)"

---

The Olin College course "A Computational Introduction to Robotics" (CompRobo) serves as a tour through some of the most important ideas at the heart of modern robotics.  The course utilizes a project-based learning pedagogy that allows students to build mastery of key concepts while also allowing for a great deal of student choice and autonomy.  The major focal points of the course are state estimation, localization, computer vision, decision-making, and societal implications of embodied systems. 

<!-- {% include feature_row %}-->

## <a name="robot-details"/> Robot Details and Documentation

{% include feature_row id="feature_row_robot" type="left" %}

## <a name="module-details"/> RoboBehaviors and Finite State Machines Project

{% include feature_row id="feature_row_warmup_project" type="right" %}

## <a name="module-details"/> Robot Localization Project

{% include feature_row id="feature_row_robot_localization_project" type="left" %}

## <a name="module-details"/> The Broader Impacts of Robots

{% include feature_row id="feature_row_robots_society" type="right" %}

## <a name="module-details"/> Machine Vision Project

{% include feature_row id="feature_row_computer_vision_project" type="left" %}

## <a name="module-details"/> Final Project

{% include feature_row id="feature_row_final_project" type="right" %}

## In-class Activities

Note: see [Site-wide TOC for an easy to navigate outline of each day's activities](toc)
Note: Subject to change as the semester unfolds!

### RoboBehaviors and Finite State Machines (+ Broader Impacts of Robots Discussions)
* [Day 1: Welcome!](in-class/day01)
* [Day 2: The Landscape of Modern Robotics // Basic ROS Concepts + Teleoperation](in-class/day02)
* [Day 3: Writing Sensory-Motor Loops in ROS2](in-class/day03)
* [Day 4: What are Broader Impacts? // Threading, Params, Propostional Control, and Wall-Following](in-class/day04)
* [Day 5: Debugging, Coordinate Frames, and Finite State Machines](in-class/day05)

### State Estimation and Localization (+ Robot Application Contexts Discussions)
* [Day 6: RoboBehaviors Debrief // Intro to State Estimation](in-class/day06) 
* [Day 7: Broader Impacts Discussions I // The Particle Filter for Robot Localization](in-class/day07)
* [Day 8: Applications I // Conceptual Particle Filter](in-class/day08)
* [Day 9: Broader Impacts Part 1 // Conceptual Particle Filter](in-class/day09)
* [Day 10: Applications II // Bayesian Estimation](in-class/day10)
* [Day 11: Debugging Strategies and Extensions // Studio Day](in-class/day11)
* [Day 12: Beyond Particle Filtering and Studio Time](in-class/day12)

### Machine Vision (+ Influences on Robotics Development Discussions)
* [Day 13: Localiztion Debrief // Machine Vision Project Ideation](in-class/day13)
* [Day 14: Applications III // Neato Soccer + Discuss Project Proposals](in-class/day14)
* [Day 15: Keypoints // Studio Time](in-class/day15)
* [Day 16: CA Lecture: Light Fields // Camera Calibration // Studio Time](in-class/day16)
* [Day 17: Broader Impacts Discussions II // Image Segmentation](in-class/day17)
* [Day 18: Studio Time](in-class/day18)
* [Day 19: Machine Vision Showcase + Final Project Kickoff](in-class/day19)

### Final Project (+ Implications of Robots Discussions)
* [Day 20: Project Proposal Generation](in-class/day20)
* [Day 21: Applications IV // Project Work Time](in-class/day21)
* [Day 22: CA Lecture: Launch Files // Project Work Time](in-class/day22)
* [Day 23: Applications V // Project Work Time](in-class/day23)
* [Day 24: Mini-Lectures // Project Work Time](in-class/day24)
* [Day 25: Applications VI // Project Work Time](in-class/day25)
* [Day 26: Project Work Time](in-class/day26)
* [Day 27: Final Project Showcase and Semester Reflection](in-class/day27)

## Bonus Materials (e.g., Recitations)
* [Recitation Example Code](https://github.com/comprobo25/recitation_examples)
* [On Kalman Filtering](https://github.com/comprobo25/recitation_examples/tree/main/kalman_filters)
* [On Computing Tools for Machine Vision](https://docs.google.com/presentation/d/1grR6uVaMEtdOn7u8L0aYVQq3NUlKZGraBVoBiZiWSqc/edit?usp=sharing)
* [On Simple Image Handling with OpenCV](https://github.com/comprobo25/recitation_examples/tree/main/image_processing)
* [Resources for an Introduction to Factor Graphs](recitations/factor_graphs.md)
* [An A* and RRT* Crash Course](https://github.com/comprobo25/recitation_examples/tree/main/path_planning)
* [Basics of Manipulation](recitations/manipulation.md)

## Conclusion and Learning More
CompRobo serves as a fun, hands-on introduction to key ideas in robotics algorithms and toolsets.  Despite the fact that the course is successful at Olin, we realize that everyone's institutional context is different. To connect with folks at Olin College to learn more about this module or determine how you might build off of this at your own institution, e-mail <a href="mailto:oepp@olin.edu">Olin's External Programs and Partnerships</a> to start the conversation.

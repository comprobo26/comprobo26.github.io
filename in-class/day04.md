---
title: "What are Broader Impacts? // Threading, Params, Proportional Control, and Wall-Following"
toc_sticky: true
toc_data:
  - title: Today
    link: in-class/day04/#today
  - title: For Next Time
    link: in-class/day04/#for-next-time
  - title: What are Broader Impacts?
    link: in-class/day04/#broader-impacts
  - title: ROS and Threading
    link: in-class/day04/#ros-and-threading
  - title: ROS Params and Proportional Control
    link: in-class/day04/#proportional-control
---


# WORK IN PROGRESS! CHECK BACK FOR UPDATES!

## Today
* What are Broader Impacts?
* ROS and Threading
* ROS Params and Proportional Control
* Studio Time (Wall-Following)

## For Next Time
* Work on the <a href="../assignments/warmup_project">the RoboBehaviors Project</a>, due Sept 23rd at 7PM!
  * If you haven't already, please list your team and add a link to your project Github on the [Teaming Sheet](https://docs.google.com/spreadsheets/d/1emh5tDNNhTiepzegO7q-Sy2jM3CaAhRC5oynsSDrPUY/edit?gid=0#gid=0), and update the [Canvas Teaming Page](https://canvas.olin.edu/courses/942/groups#).
  * A rubric for the project is available [on Canvas](https://canvas.olin.edu/courses/942/assignments/16078).
  * We will have a shareout for the project on Sept. 22nd in class (with a [short deliverable](https://canvas.olin.edu/courses/942/assignments/16079)).
* Work on the [Broader Impacts assignment Part 1](../assignments/broader_impacts), due on September 30th at 7PM. (changed date!)
  * We will have a class discussion on Thursday Oct. 1st. (changed date!)


## What are Broader Impacts?
As we touched on during the first class meeting, and as you've started chewing on in the Broader Impacts assignment, robots -- by virtue of being embodied in the world -- uniquely engage with the world in a way that other forms of computing-based technology may not. "Robo-ethics" is a subfield within robotics that formally designs and ascribes methods of analyzing the impact of robotic systems. Some resources you might find interesting as a launch point to learning more about the robo-ethics field are below:
* Standford Encyclopedia of Philosophy entry on [Ethics of Artificial Intelligence and Robotics](https://plato.stanford.edu/entries/ethics-ai/)
* [Building and Evaluating Ethical Robotics Systems workshop](https://www.ers-workshop.com/) at IROS (one of the two largest and most well-known robotics conferences in the world)
* [An Economics Perspective on "Robotics at Work"](https://watermark.silverchair.com/rest_a_00754.pdf?token=AQECAHi208BE49Ooan9kkhW_Ercy7Dm3ZL_9Cf3qfKAc485ysgAAA7YwggOyBgkqhkiG9w0BBwagggOjMIIDnwIBADCCA5gGCSqGSIb3DQEHATAeBglghkgBZQMEAS4wEQQMZLkTwB9HgtoaRAFMAgEQgIIDadCNISVVMpDrlENyL-Jky9bDY4JksfzRpkUohr3IiokebXqXNcQ5to_uhPN9mlXocCy7kXBIrmww_m7bxSg58f1uSiP0mNsXD4gr0A1gHsS-lfScqhxgzsmRa80sCiGGM_mUBJ_U7dZ9JusK8Vg78oVNd5CdsplbQBrX4aiQPps61Mb5ZP7SRBDatg0clLlj7t6MgdcZ1KX1Pv9Ln_ZBuRNPIaNpMNAJMzSqADaFYfkrSVWbdcqRTy20E56gJ-rtEEIK10Q6PUQbnY7x052YFrIFYCbiMBBaubvfrWmkLeHStxCSUKpr3FaThIQQ0LnvRQtM1ewsFdRqEidrtldPnYAQofVqfVfPXY93pTTdGGDj2nhmjYPqTOjGevXktJg9H9jO8ilHe4k07zjGtLxCWH4Px_5jfSFw0QhdvhPDTw1Y_ofl_xacRisFejQIuaCvxnFny0RMMtXexdUB_NbTp2eP070sYXOYfqhzHCFjfyBN9xDhefECQxptToCI5wXxZV2LpblRousIFu5cUpomLMO1EITaVroluTau0tMLqY_8q-0B2Ab2TugxhMmC6HNKShzeIF7kQf3LEBkOiiOA1LLWsAZH5YZiC9mHqWYSd6NHrttRCcj9c-mL6kxI4gz0S6dPQqqDXnG1z9bJor0JNnKlIO_CpSE1WE8MiXLDZNNxdF-1rYa91fs4boLHN9SRr88tOQYj08oi8cMk2pycMxyeCrfPMyj_rTeoL27wICb-39MEp6eT8Uxp7AbPFd_B_0dlulpORaK1fpDxEdUnv2wngwbeY8cgzRQE-yEd_hWGyDhlh67gkIQ5X6MIVA1b0GlMWAMgoKGpJpn5q9jDmTwuV4X4ln3RgsD384ozZBf3hkXu-RVQKUcPFiSCrQLE6j97KE5yahSVJnPd_bAor5t4XgASyeQ3chDKatR5oBPyUrft3X9ksQK1GJz0Hr9Q3hZbnjzKXQCwlgxCZz0CRmWAx4HbdXG-IkKqQLObUNi55_0F-La1zsIMoxp69dCeimP33UkwSdfLi0R7KnX6XSHUAtwEEXRfJMg6_P_aoFxYRb_CDyLyLrrOSKYLRPolzE3PRgAz2f5xKu3eHo1YBbGhIKRHirJkMoVe8qHJPpCYKFl6D4HKQWvDg3wZJAEubGQ6eG24URt-TA) which analyzes the impact of robots on labor and implications
* [An Academic Discussion of Fairness and Abstraction in Sociotechnical Systems](https://dl.acm.org/doi/pdf/10.1145/3287560.3287598) which highlights the "traps" that fair practices can encounter when actually deploying systems at-scale

While robo-ethicists make it their primary vocation to understand the nuances of robotics use, every roboticist or robotics-adjacent engineer, manager, researcher, or entrepreneur deals with practical quandaries each day that require applying (implicitly or explicitly) a values-based framework -- from the design of a particular interface (for whom will this interface be for? how much information from the backend should be legible?), selection of components (what is the lifecycle of this part? who is supplying this part?), and creation of design specifications (what is the intended use of the robot? how will that intended use be protected?).

### Open-Ended Discussion - Broader Impacts and Robotics Funding

"Broader Impacts" is a term that attempts to make apparent the values or ethics based systems that people apply to the technology they produce or work that they engage in. [The National Science Foundation (NSF) in the US requires a "broader impacts" component to research proposals](https://new.nsf.gov/funding/learn/broader-impacts), where the definition of a broader impact is expansive, and may cover:
* Public engagement in the work to be completed
* Developing partnerships across academic / industrial sectors, or across disciplines
* Explicitly working on a project that contributes to societal well-being
* Contributing to national security
* Building STEM talent through broadening participation and strengthening infrastructure for supporting success

Let's have a look at a broader impacts statement from a NSF proposal submitted to the NSF National Robotics Initiative solicitation, entitled ["Never-ending Multimodal Collaborative Learning"](http://www.cs.cmu.edu/~cga/proposals/nsf-nri-19.pdf), which proposes to develop algorithms for robot-learning and task-generalization through natural language and visual/kinesthetic demonstrations performed by a human teacher:

> The National Robotics Initiative was a three part solicitation over a decade that aimed to support fundamental research in the US. This flavor of the NRI was aimed at "Ubiquitous Collaborative Robots" and research to advance the development and use of co-robots (robots that work with/near people). Ubiquity was defined as "seamless integration of co-robots to assist humans in every aspect of life." You can read the full solicitation [here](https://nsf-gov-resources.nsf.gov/solicitations/pubs/2019/nsf19536/nsf19536.pdf?VersionId=CHKRGmHnTh_vEx4KZmJkbN.mz30N7kPV). This program was sunset in 2022.

>```The proposed research will reduce the cost of programming robots and other technology, such as personal assistants. Non-experts will be able to program and personalize robots similarly to how we program fellow humans and especially children: by communicating in natural language (e.g., "stop fidgeting") and demonstrating visually the desired way to do things (e.g., "open it like this"), as opposed to being programmed by writing code or through millions of positive and negative examples. Robots will be able to acquire new concepts and skills adapting to individual users' needs through interaction with end-users, as opposed to maintaining a fixed set of functionalities predetermined at the factory. The simplicity and directness of grounded natural language interfaces will help robots better serve older adults and people with disabilities. This is just one example of the proposed technology's potential for social good. This research is tightly coupled to the educational program of the PIs, which currently includes a course on language grounding on vision and control, and another on architectures for never-ending learning, with the goal of teaching students that there is more to AI than learning from a large number of positive and negative examples.```

Get together with some folks around you, and consider the following questions (~15 minutes):
1. Using the definitions from the NSF broader impacts page, what key themes do you see emerge in this paragraph? 
2. What evaluation metrics would you use to assess whether the broader impacts goals were met over the course of this project? 
3. Are there other broader impacts that the authors don't mention, but might be relevant to their project? Are there any unintended impacts of the work that could/should be considered by the project?
4. What critiques, if any, do you have to make to this abstract based on your understanding of Broader Impacts?
5. Would you fund this work? Why or why not?

We'll do a brief report out (~5 minutes) with the whole class.

As you work on your Broader Impacts Part 1 project, you might want to consider developing your own definition of "broader impacts" and using that as a means of guiding your research and artifact development.


## ROS and Threading
A "thread" is an independent flow of execution in a computer program; "threading" refers to creating multiple concurrent pathways for execution. When using ROS2, the concept of threading can arise in multiple ways, but one common one is when we utilize our subscription callbacks _and_ create running loops within our code.

We'll go over some points regarding how ROS2 deals with different threads of execution.  In order to structure our work, we're going to be looking at two pieces of sample code:

> Note: you might find looking at these pieces of code quite useful for the Warm-Up Project!

* [Drive Square Sample 1](../Sample_code/drive_square_sample_1): Single-Threaded Task Execution in ROS2
  * [C++ Version](../Sample_code/drive_square_sample_2) for those interested.
* [Drive Square Sample 2](../Sample_code/drive_square_sample_3): Multi-Threaded Task Execution in ROS2

Why would we want to perform threading, as opposed to timing (as we have been)?
* **Avoiding "blocked" callbacks**: in sequential execution, the callbacks are executed one at a time, and blocked from being triggered until the previous has finished. If we happen to put a lot of "work" in a callback, we could delay execution down the line. Threading avoids this issue (kinda...in Python there isn't truly a way for parallel processing, but nonetheless execution can _overlap_ which can be incredibly helpful.).
* **Timing can be fraught**: if we sent a timer, then anything in that loop must execute within that time or weird / unintended behavior can occur. Threading allows callbacks to occur at their own time.
* **Threading gives us control of information flow**: within ROS2, the use of threading allows us the flexibility to choose what callbacks occur when in execution (and therefore what work or data is consistently protected from deadlocking).

If you want to learn more, [this conversation on the ROS discourse](https://discourse.ros.org/t/how-to-use-callback-groups-in-ros2/25255) is an excellent source!

## Wall-Following and Proportional Control

So far we've programmed robots to choose between a small set of motor commands (move forward, stop, etc.) based on sensor readings.  Today, we will be experimenting with setting the motor command proportional to the error between the robot's current position and the desired position.

To get the idea, program the Neato to adjust its position so that it is a specified (target) distance away from the wall immediately in front of it. The Neato's forward velocity should be proportional to the error between the target distance and its current distance. It's tricky to get the sign correct, run through a few mental simulations to make sure the robot will move in the right direction. 

> Note: you might be interested in adapting this in your Warm-Up project wall-follower or person-follower code!

To get started, create a package somewhere in your ``ros2_ws/src`` directory for your work.  In this example, we can put the package directly in ``ros2_ws/src/class_activities_and_resources`` directory then rebuild the workspace:

```bash
$ cd ~/ros2_ws/src/class_activities_and_resources
$ ros2 pkg create in_class_day04 --build-type ament_python --node-name wall_approach --dependencies rclpy std_msgs geometry_msgs sensor_msgs neato2_interfaces
$ cd ~/ros2_ws
$ colcon build --symlink-install
$ source ~/ros2_ws/install/setup.bash
```

You may have noticed at this point that ROS requires a certain amount of [boiler-plate code](https://en.wikipedia.org/wiki/Boilerplate_code) to get going.  If you are having trouble with this, or would rather skip ahead to the proportional control part, [you can grab some starter code for ``wall_approach.py``](../Sample_code/wall_approach_starter).

A helpful tool for visualizing the results of your program is to use <a-no-proxy href="https://docs.ros.org/en/humble/Concepts/About-RQt.html">rqt</a-no-proxy>.  First, start up the GUI:

```bash
$ rqt
```

Next, go to ``plugins -> visualization -> plot``.

Type ``/scan/ranges[0]`` (if that is in fact what you used to calculate forward distance) into the topic field and then hit `+`. 

> Tip: to change the zoom in the plot, hold down the right mouse button and drag up or down on the body of the plot (it's pretty finicky, but it does work).

You can use this link to find [a sample solution to this task](https://github.com/comprobo25/class_activities_and_resources/blob/main/in_class_day04_solutions/in_class_day04_solutions/wall_approach.py).

### Getting Fancy: ROS Params

To make a node more configurable, you can use ROS Params, which allow us pass in arguments to a node from the commandline (or control them through tools like `rqt`). This is super powerful, because it can let you, in real time, adjust your robot performance and behavior without killing, re-writing, and re-running your nodes. For proportional control, we could set our proportional coefficient and our wall distance in this way.
* See the [ros param command line tools documentation](https://docs.ros.org/en/humble/Tutorials/Beginner-CLI-Tools/Understanding-ROS2-Parameters/Understanding-ROS2-Parameters.html) for more information
* [Code for accessing parameters in Python documentation from The Robotics BackEnd](https://roboticsbackend.com/rclpy-params-tutorial-get-set-ros2-params-with-python/) (which might be a bit easier to parse than the [official one](https://docs.ros.org/en/humble/Tutorials/Beginner-Client-Libraries/Using-Parameters-In-A-Class-Python.html)). 

For instance, if you follow the documentation you can create a node similar to our [sample solution, ``wall_approach_fancy.py``](https://github.com/comprobo25/class_activities_and_resources/blob/main/in_class_day04_solutions/in_class_day04_solutions/wall_approach_fancy.py) that supports the following customization via the command line:

```bash
$ ros2 run in_class_day04_solutions wall_approach_fancy --ros-args -p target_distance:=1.5 -p Kp:=0.5
```

Here is a demo of the script, ``wall_approach_fancy.py`` that uses ROS parameters as well as the tool ``dynamic_reconfigure`` for easy manipulation of various node parameters.
> Note that in order to support ``dynamic_reconfigure`` in your nodes, you have to call ``add_on_set_parameters_callback`` and implement an appropriate callback function (see sample solution for more on this).

![An animated Gif that shows a robot attempting to maintain a particular distance from a wall](day04images/wall_approach_fancy_ros2.gif)

### Wall-Following
When you feel like you have a sense of the example code, or have working sample code of your own, consider how you might adjust the code to work for wall-following (approaching and driving parallel to a wall at a certain distance). Have a look at the assignment document for a sample diagram (hint: you might want to draw a lot of pictures before you think about coding anything). 

---
title: "What are Broader Impacts? // Threads and Driving in a Square"
toc_sticky: true
toc_data:
  - title: Today
    link: in-class/day04/#today
  - title: For Next Time
    link: in-class/day04/#for-next-time
  - title: What are Broader Impacts?
    link: in-class/day04/#broader-impacts
  - title: ROS, Threading, and Driving in the Square
    link: in-class/day04/#ros-threading-square
---

## Today
* What are Broader Impacts?
* ROS and Threading
* Studio Time (Driving in a Shape)

## For Next Time
* Work on the <a href="../assignments/warmup_project">the RoboBehaviors Project</a>, due Sept 22nd at 7PM!
  * **In-Class Shareout**: September 21st, 1PM ([Canvas description](https://canvas.olin.edu/courses/1070/assignments/20110))
  * **Project Due Date**: September 22nd, 7PM ([Canvas description](https://canvas.olin.edu/courses/1070/assignments/20109))
  * **Individual Survey**: September 22nd, 9PM ([Canvas description](https://canvas.olin.edu/courses/1070/quizzes/2973))
  * By next class, it is recommended that:
    * You have implemented your own "drive a shape" and integrated it into your project package
    * You have designed your FSM and have started to write skeleton code of the behaviors
* Work on your [Broader Impacts](../assignments/broader_impacts) assignment (Due Sept 29th at 7PM).
  * We will have a [class discussion](https://canvas.olin.edu/courses/1070/assignments/20094) on Thursday Oct. 1st.


## What are Broader Impacts?
As we touched on during the first class meeting, and as you've started chewing on in the Broader Impacts assignment, robots -- by virtue of being embodied in the world -- uniquely engage with the world in a way that other forms of computing-based technology may not. "Roboethics" is a subfield within robotics that formally designs and ascribes methods of analyzing the impact of robotic systems. Some resources you might find interesting as a launch point to learning more about the roboethics field are below:
* Stanford Encyclopedia of Philosophy entry on [Ethics of Artificial Intelligence and Robotics](https://plato.stanford.edu/entries/ethics-ai/)
* [Building and Evaluating Ethical Robotics Systems workshop](https://www.ers-workshop.com/) at IROS (one of the two largest and most well-known robotics conferences in the world)
* [An Economics Perspective on "Robotics at Work"](https://watermark.silverchair.com/rest_a_00754.pdf?token=AQECAHi208BE49Ooan9kkhW_Ercy7Dm3ZL_9Cf3qfKAc485ysgAAA7YwggOyBgkqhkiG9w0BBwagggOjMIIDnwIBADCCA5gGCSqGSIb3DQEHATAeBglghkgBZQMEAS4wEQQMZLkTwB9HgtoaRAFMAgEQgIIDadCNISVVMpDrlENyL-Jky9bDY4JksfzRpkUohr3IiokebXqXNcQ5to_uhPN9mlXocCy7kXBIrmww_m7bxSg58f1uSiP0mNsXD4gr0A1gHsS-lfScqhxgzsmRa80sCiGGM_mUBJ_U7dZ9JusK8Vg78oVNd5CdsplbQBrX4aiQPps61Mb5ZP7SRBDatg0clLlj7t6MgdcZ1KX1Pv9Ln_ZBuRNPIaNpMNAJMzSqADaFYfkrSVWbdcqRTy20E56gJ-rtEEIK10Q6PUQbnY7x052YFrIFYCbiMBBaubvfrWmkLeHStxCSUKpr3FaThIQQ0LnvRQtM1ewsFdRqEidrtldPnYAQofVqfVfPXY93pTTdGGDj2nhmjYPqTOjGevXktJg9H9jO8ilHe4k07zjGtLxCWH4Px_5jfSFw0QhdvhPDTw1Y_ofl_xacRisFejQIuaCvxnFny0RMMtXexdUB_NbTp2eP070sYXOYfqhzHCFjfyBN9xDhefECQxptToCI5wXxZV2LpblRousIFu5cUpomLMO1EITaVroluTau0tMLqY_8q-0B2Ab2TugxhMmC6HNKShzeIF7kQf3LEBkOiiOA1LLWsAZH5YZiC9mHqWYSd6NHrttRCcj9c-mL6kxI4gz0S6dPQqqDXnG1z9bJor0JNnKlIO_CpSE1WE8MiXLDZNNxdF-1rYa91fs4boLHN9SRr88tOQYj08oi8cMk2pycMxyeCrfPMyj_rTeoL27wICb-39MEp6eT8Uxp7AbPFd_B_0dlulpORaK1fpDxEdUnv2wngwbeY8cgzRQE-yEd_hWGyDhlh67gkIQ5X6MIVA1b0GlMWAMgoKGpJpn5q9jDmTwuV4X4ln3RgsD384ozZBf3hkXu-RVQKUcPFiSCrQLE6j97KE5yahSVJnPd_bAor5t4XgASyeQ3chDKatR5oBPyUrft3X9ksQK1GJz0Hr9Q3hZbnjzKXQCwlgxCZz0CRmWAx4HbdXG-IkKqQLObUNi55_0F-La1zsIMoxp69dCeimP33UkwSdfLi0R7KnX6XSHUAtwEEXRfJMg6_P_aoFxYRb_CDyLyLrrOSKYLRPolzE3PRgAz2f5xKu3eHo1YBbGhIKRHirJkMoVe8qHJPpCYKFl6D4HKQWvDg3wZJAEubGQ6eG24URt-TA) which analyzes the impact of robots on labor and implications
* [An Academic Discussion of Fairness and Abstraction in Sociotechnical Systems](https://dl.acm.org/doi/pdf/10.1145/3287560.3287598) which highlights the "traps" that fair practices can encounter when actually deploying systems at-scale
* [The OpenRoboEthics Institue](https://openroboethics.org//) a non-profit founded by roboticist AJung Moon which discusses modern topics in robotics and their intersection with ethical domains

While roboethicists make it their primary vocation to understand the nuances of robotics use, every roboticist or robotics-adjacent engineer, manager, researcher, or entrepreneur deals with practical quandaries each day that require applying (implicitly or explicitly) a values-based framework -- from the design of a particular interface (for whom will this interface be for? how much information from the backend should be legible?), selection of components (what is the lifecycle of this part? who is supplying this part?), and creation of design specifications (what is the intended use of the robot? how will that intended use be protected?).

### Open-Ended Discussion - Broader Impacts, Robotics Funding, and Ethics Screening

"Broader Impacts" is a term that attempts to make apparent the values or ethics based systems that people apply to the technology they produce or work that they engage in. [The National Science Foundation (NSF) in the US requires a "broader impacts" component for all research proposals](https://new.nsf.gov/funding/learn/broader-impacts), where the definition of a broader impact is expansive, and may cover:
* Public engagement in the work to be completed
* Developing partnerships across academic / industrial sectors, or across disciplines
* Explicitly working on a project that contributes to societal well-being
* Contributing to national security or economic competitiveness
* Building STEM talent through broadening participation and strengthening infrastructure for supporting success

Let's have a look at a broader impacts statement from a NSF proposal submitted to the NSF _National Robotics Initiative_ solicitation, entitled ["Never-ending Multimodal Collaborative Learning"](http://www.cs.cmu.edu/~cga/proposals/nsf-nri-19.pdf), which proposes to develop algorithms for robot-learning and task-generalization through natural language and visual/kinesthetic demonstrations performed by a human teacher:

> The National Robotics Initiative was a three part solicitation over a decade that aimed to support fundamental research in the US. This flavor of the NRI was aimed at "Ubiquitous Collaborative Robots" and research to advance the development and use of co-robots (robots that work with/near people). Ubiquity was defined as "seamless integration of co-robots to assist humans in every aspect of life." You can read the full solicitation [here](https://nsf-gov-resources.nsf.gov/solicitations/pubs/2019/nsf19536/nsf19536.pdf?VersionId=CHKRGmHnTh_vEx4KZmJkbN.mz30N7kPV). This program was sunset in 2022.

>```The proposed research will reduce the cost of programming robots and other technology, such as personal assistants. Non-experts will be able to program and personalize robots similarly to how we program fellow humans and especially children: by communicating in natural language (e.g., "stop fidgeting") and demonstrating visually the desired way to do things (e.g., "open it like this"), as opposed to being programmed by writing code or through millions of positive and negative examples. Robots will be able to acquire new concepts and skills adapting to individual users' needs through interaction with end-users, as opposed to maintaining a fixed set of functionalities predetermined at the factory. The simplicity and directness of grounded natural language interfaces will help robots better serve older adults and people with disabilities. This is just one example of the proposed technology's potential for social good. This research is tightly coupled to the educational program of the PIs, which currently includes a course on language grounding on vision and control, and another on architectures for never-ending learning, with the goal of teaching students that there is more to AI than learning from a large number of positive and negative examples.```

Get together with some folks around you, and consider the following questions (~15 minutes):
1. Using the definitions from the NSF broader impacts page, what key themes do you see emerge in this paragraph? 
2. What evaluation metrics would you use to assess whether the broader impacts goals were met over the course of this project? 
3. If you were working on this project, what [would you prioritize](../How%20to/ethics_screening_tool.md) as part of your project management workflow to ensure that the intended broader impacts were met?
4. What critiques, if any, do you have to make to this abstract based on your understanding of Broader Impacts?
5. Would you fund this work? Why or why not?

We'll do a brief report out (~5 minutes) with the whole class.

As you work on your Broader Impacts Part 1 project, you might want to consider developing your own definition of "broader impacts" and using that as a means of guiding your research and artifact development. To help you with this, our [Ethics Screening Tool](../How%20to/ethics_screening_tool.md) may be useful.


## ROS, Threading, and Driving in the Square

### Single-Threading
So far, we've been writing code that would be considered _single-threaded_ -- we have a single thing we want to do, so have a single function in our code which typically executes the work of what we want to do. 

Let's make this more concrete and look at a particular example of a ROS node designed to command a Neato to drive in a square:

* [Drive Square Sample 1](../Sample_code/drive_square_sample_1): Single-Threaded Task Execution in ROS2
  * [C++ Version](../Sample_code/drive_square_sample_2) for those interested.

With your project partner, read and annotate this code to make sure you know what's happening. You might specifically want to think about the following:

* How often is `run_loop` called? Does the code inside `run_loop` ever block the callback for the function? 
* Can you draw the finite state machine that is described in the code? What is the trigger between states?
* Will this node stop drawing squares after the fourth side is made?


### Multi-Threading
A "thread" is an independent flow of execution in a computer program; "threading" refers to creating multiple concurrent pathways for execution. When using ROS2, the concept of threading can arise in multiple ways, but one common one is when we utilize our subscription callbacks _and_ create running loops within our code.

Let's make this more concrete -- suppose we would like our Neato to draw a square, but also we would like it to stop if some other piece of code indicates that an emergency stop situation has arisen, and then carry-on drawing a square from where it left off once the emergency stop has been resolved. How might we handle this gracefully in one piece of code? What would break about the example we just looked at?

One way of handling this situation would be through threading. Let's look at this example:

* [Drive Square Sample 2](../Sample_code/drive_square_sample_3): Multi-Threaded Task Execution in ROS2

With your project partner, read and annotate this code to make sure you know what's happening. You might specifically want to thikn about the following:

* How often is `run_loop` called? Is there anything in `run_loop` that might block updating the `estop` variable?
* Can you draw the finite state machine that is described in the code? What is the trigger between states?
* What happens when the e-stop is triggered? Will this code handle resuming drawing a square correctly if it is resolved?
* Will this node stop drawing squares after the fourth side is made?

### Design Considerations

Why would we want to perform threading, as opposed to using pure timing (as we have been)?
* **Avoiding "blocked" callbacks**: in sequential execution, the callbacks are executed one at a time, and blocked from being triggered until the previous has finished. If we happen to put a lot of "work" in a callback, we could delay execution down the line. Threading avoids this issue (kinda...in Python there isn't truly a way for parallel processing, but nonetheless execution can _overlap_ which can be incredibly helpful.).
* **Timing can be fraught**: if we set a timer, then anything in that loop must execute within that time or weird / unintended behavior can occur. Threading allows callbacks to occur at their own time.
* **Threading gives us control of information flow**: within ROS2, the use of threading allows us the flexibility to choose what callbacks occur when in execution (and therefore what work or data is consistently protected from deadlocking).

If you want to learn more, [this conversation on the ROS discourse](https://discourse.ros.org/t/how-to-use-callback-groups-in-ros2/25255) is an excellent source!


## Studio Time
Using what we just covered in this unit, incorporate your own drive-in-a-shape behavior into your project (you are allowed to use an edited version of one of these drive-in-a-square examples). For an additional challenge, consider whether you might use any additional (sensor) information to reduce error in turns or distances. In your write-up for your drive-in-a-shape behavior, make sure to note your design decision for selecting between single-threading or multi-threading!

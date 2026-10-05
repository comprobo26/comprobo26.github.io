---
title: "Debugging Strategies and Extensions // Studio Time"
toc_sticky: true
toc_data:
  - title: Today
    link: in-class/day11/#today
  - title: For Next Time
    link: in-class/day11/#for-next-time
  - title: Particle Filter Debugging Techinques
    link: in-class/day11/#particle-filter-debugging-techinques
  - title: Extensions to the Particle Filter
    link: in-class/day11/#extensions-to-the-particle-filter
---

# WORK IN PROGRESS! CHECK BACK FOR UPDATES!


## Today
* Debugging Your Particle Filter + Extensions
* Bayesian Filtering Mathematical Principles
* Studio Time

## For Next Time
* Work on the [Robot Localization project](../assignments/robot_localization)
  * Demos due on **Thursday October 16 by Class**
  * Code + Writeups due on **Friday October 17th 7PM**
* Review your Broader Impacts Phase 1 feedback (emailed)
* Review the project description for [Broader Impacts Phase 2](../assignments/broader_impacts)
  * In class discussions on **Monday November 3rd**
  * Materials due **Tuesday November 4th**
* Consider whether there is [feedback you'd like to share about the class](https://forms.gle/kPjvgWb4ETDKMHRD7)

## Particle Filter Debugging Techniques

### Using Python Debugger ``pdb``

In order to use ``pdb`` you'll want to change your workflow a little bit.  Instead of launching your particle filter and the map server through the ``test_pf.py`` launch file, you will be starting the map server separately and then launching your particle filter through your Python IDE (e.g., VSCode).

You can start the ``map_server`` using the following command:

{% include codeHeader.html %}
```bash
ros2 launch robot_localization launch_map_server.py map_yaml:=path-to-map-yaml 
```

If all went well, you will see the following output.

```bash
[INFO] [launch]: All log files can be found below /home/pruvolo/.ros/log/2022-10-07-11-30-28-273830-pruvolo-Precision-3551-7847
[INFO] [launch]: Default logging verbosity is set to INFO
[INFO] [lifecycle_manager-2]: process started with pid [7851]
[INFO] [map_server-1]: process started with pid [7849]
[lifecycle_manager-2] [INFO] [1665156628.380768047] [lifecycle_manager]: Creating
[map_server-1] [INFO] [1665156628.382319035] [map_server]: 
[map_server-1] 	map_server lifecycle node launched. 
[map_server-1] 	Waiting on external lifecycle transitions to activate
[map_server-1] 	See https://design.ros2.org/articles/node_lifecycle.html for more information.
[map_server-1] [INFO] [1665156628.382390679] [map_server]: Creating
[lifecycle_manager-2] [INFO] [1665156628.385117900] [lifecycle_manager]: Creating and initializing lifecycle service clients
[lifecycle_manager-2] [INFO] [1665156628.385653406] [lifecycle_manager]: Starting managed nodes bringup...
[lifecycle_manager-2] [INFO] [1665156628.385678064] [lifecycle_manager]: Configuring map_server
[map_server-1] [INFO] [1665156628.385812580] [map_server]: Configuring
[map_server-1] [INFO] [map_io]: Loading yaml file: gauntlet.yaml
[map_server-1] [DEBUG] [map_io]: resolution: 0.05
[map_server-1] [DEBUG] [map_io]: origin[0]: -1.36
[map_server-1] [DEBUG] [map_io]: origin[1]: -3.09
[map_server-1] [DEBUG] [map_io]: origin[2]: 0
[map_server-1] [DEBUG] [map_io]: free_thresh: 0.25
[map_server-1] [DEBUG] [map_io]: occupied_thresh: 0.65
[map_server-1] [DEBUG] [map_io]: mode: trinary
[map_server-1] [DEBUG] [map_io]: negate: 0
[map_server-1] [INFO] [map_io]: Loading image_file: ./gauntlet.pgm
[map_server-1] [DEBUG] [map_io]: Read map ./gauntlet.pgm: 71 X 76 map @ 0.05 m/cell
[lifecycle_manager-2] [INFO] [1665156628.391201344] [lifecycle_manager]: Activating map_server
[map_server-1] [INFO] [1665156628.391262492] [map_server]: Activating
[lifecycle_manager-2] [INFO] [1665156628.391473752] [lifecycle_manager]: Managed nodes are active
```

Now that the ``map_server`` is running, you can start the debugger through ``VSCode`` (as an example) by selecting ``Run`` and then ``Start with Debugging``.  Next, choose ``Python`` as your debugging configuration.  Make sure you have set the focus of ``VSCode`` to your ``pf.py`` script before doing this.  You can now set breakpoints or inspect your program's state in the event of a crash.

### Debugging Using Matplotlib

Sometimes it's easier to get a quick and dirty visualization going using a familiar tool like matplotlib.  You could consider using this for things like plotting particle weights or motion updates.

### Create Tests for Class Functions
You can create test scripts that confirm the logic in certain key functions of your particle filter using exemplar inputs with outputs you can hand compute.

### Use ROS2 Commandline Tools
Tools like `tf2`, `topic list/echo`, `node list`, and `rqt` are all really useful for checking on the status of your network. 

### Grab a Bagfile
In the midst of debugging some tricky logic error, it can be nice to be able to see all the data at once (not just visually, but quantitatively) and parse it using graphing tools, text editors, or other process. You can record a bagfile of your system in action, then convert that to .csv files per topic, putting them in an easy to interact with form for plotting, parsing, etc. with your standard set of tools like `pandas` or `matplotlib`. 


## Bayesian Filtering and the Particle Filter

> Legacy notes about Bayes Filters and the Particle Filter from Paul Ruvolo are available: [as a video lecture](https://www.youtube.com/embed/l7CrjOTlioU) and as [physical notes](updated_bayes_filter.pdf). 

> Slides walking through our in-class derivation [here](https://docs.google.com/presentation/d/1ekeHfD7YOJLc6mHo8z4BHfnu2JCXtsvNfszsGDPM4Js/edit#slide=id.p).

For your projects, you're implementing a particle filter, which is a subclass of algorithm under the more general category of _Bayesian filters_. A Bayesian filter is a recursive, or sequential, algorithm -- for localization, this means that the robot's state estimate is refined iteratively as observations or actions are taken.

There is a bit of vocabulary to know before we get started:
* Markov process: a chain of events in which the probability of each event depends only on the state of the previous event ("what happens next only requires me to think about what's happening now")
  * This is a useful _assumption_ about the way the world works, because now we don't have to consider the entire history of a robot, just what happened most recently.
* Monte Carlo algorithms: repeated random sampling is used to estimate a solution to a complex (often nonlinear) problem

We're going to walk through the steps of the Bayesian filter:
```
Steps of a Bayesian Filter:
1) Initialize with an estimate of the first pose
2) Take an action, and predict the new pose based on the motion model
3) Correct the pose estimate, given an observation
4) Repeat steps 2 and 3, ad nauseum (or until your robot mission is over)
```

### Prediction
During the prediction step, the current estimated pose of the robot is updated based on a _motion model_. The motion model captures how a control input may be mapped to the real world (what noise may be applied, for instance). Prediction will always increase the uncertainty we have about where the robot is in the world (unless we have perfect motion knowledge). Prediction asks: given where I think I am, where will I end up after I take this action?

### Correction
To reduce (or attempt to reduce) our uncertainty, we can look around us with an _observation model_ (which will also capture noise in our measurements). Correction asks: given what I am measuring, what is my likely pose based on my estimate of where I may be?

### Mathematical Details
In the breakout session, we'll walk through the mathematical details of this for a simple world in which a robot can open and close a door, and can measure whether a door is open or closed. This example is borrowed from [Probabilistic Robotics](https://docs.ufpr.br/~danielsantos/ProbabilisticRobotics.pdf); a highly influential book in modern robotics.

### The Particle Filter
A Bayesian filter, in its purest form, asks us to work with continuous probability distributions, and that is computationally challenging (nigh intractable) most of the time for practical robotics problems. The particle filter addresses these computational challenges by allowing us to _draw samples from our probability distributions_ and apply our prediction and correction steps to each of those samples in order to get an empirical estimate of a new probability distribution. In this way, the particle filter is a Monte Carlo algorithm, and leverages the law of large numbers to "converge" towards the optimal answer. (You can get a sense about why sampling works to find complex distributions by [playing with this applet](http://chi-feng.github.io/mcmc-demo/app.html?algorithm=GibbsSampling&target=banana)).




## Extensions to the Particle Filter

### Make your particle filter more efficient computationally

Advice:
* Find the critical path (what runs the most often and therefore what would give the biggest return on your investment of work).
* The ``OccupancyField`` class has support for processing multiple points simultaneously (vectors of $$(x,y)$$ coordinates).
* Matrix multiplication is your friend (how can a multiplication remove a loop?)
* Benchmark sections of your code by adding timers to see if your efforts are paying off.

### Experiment with laser scan likelihood functions

Advice:
* Look in the Probabilistic Robotics book to see read about ``z_hit``, ``z_random``, etc.

### Robot Kidnapping Problem (no initial pose guess)

Advice:
* Make your code faster first (it will let you use more particles)
* You may need to come up with ways to initialize the particle cloud in smart ways
* Past comprobo projects may provide good clues (look at examples from the [localization assignment](../assignments/robot_localization)). 

### Connection Between the Particle Filter and the Bayes Filter

Advice:
* The core idea is this concept of sequential importance sampling (SIS).  The writeup of this are pretty technical, but you may start with this resource from [Columbia by Frank Wood](http://www.stat.columbia.edu/~fwood/Tutorials/sequential_monte_carlo.pdf). You can also check out section 4.2 of the [Probabilistic Robotics book](https://docs.ufpr.br/~danielsantos/ProbabilisticRobotics.pdf). 

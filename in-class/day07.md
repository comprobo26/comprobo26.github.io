---
title: "Tough Conversations // The Particle Filter for Robot Localization"
toc_sticky: true
toc_data:
  - title: Today
    link: in-class/day07/#today
  - title: For Next Time
    link: in-class/day07/#for-next-time
  - title: Frameworks for Challenging Conversations
    link: in-class/day07/#challenging-conversations
  - title: Living in a 1D World Part 1
    link: in-class/day07/#living-1d-part1
  - title: The Particle Filter Algorithm
    link: in-class/day07/#the-particle-filter-algorithm
  - title: Living in a 1D World Part 2
    link: in-class/day07/#living-1d-part2
  - title: Project Kick-Off
    link: in-class/day07/#project_kickoff
---

# WORK IN PROGRESS! CHECK BACK FOR UPDATES!


## Today 

* Frameworks for Challenging Conversations
* We're All Living in a 1D World! Part 1: Simulation Intuition
* The Particle Filter Algorithm
* We're All Living in a 1D World! Part 2: Code Dissection
* Project Kick-Off

## For Next Time
* Work on the [Broader Impacts assignment Part 1](../assignments/broader_impacts), due on **September 30th at 7PM**.
  * We will have a class discussion on **Thursday Oct. 2nd**.
* [Form a team](https://docs.google.com/spreadsheets/d/1-YlG0zlFozc0oo_GY-xu_2HTyY3RUPz8JD785Cf7zkw/edit?usp=sharing) and review [a view of the finish line](../assignments/robot_localization#a-view-of-the-finish-line-and-getting-set-with-rviz)
* Work on the [Particle Filter Conceptual Overview](https://canvas.olin.edu/courses/942/assignments/16068), due on **Friday October 3rd at 7PM**.
* Consider whether there is [feedback you'd like to share about the class](https://forms.gle/kPjvgWb4ETDKMHRD7)

## Frameworks for Challenging Discussions (For Your Consideration)
Soon, you'll be asked to host an in-class discussion on your selected robot to gather different perspectives on the robotic system and its context. Discussions about perspective, context, values, and ethics can sometimes be tricky -- perhaps there is conflict among participants, or it is challenging for everyone to engage fully with a topic. Simply being fully present and willing to pull on different threads of a conversation can be challenging. To assist you in participating in our class and project discussions, the following may be of interest:
* **Combine different discussion techniques** -- consider the use of individual quiet brainstorming, round-robin sharing, and open dialog; during what parts of a discussion might these be useful to your group? When could switching techniques change the energy of the discussion?
* **Focus on collaborative generation** -- one way to invite multiple voices is to create a mechanism that feels collaborative; if the aim of the discussion is to generate multiple perspectives on an idea, then you are inviting everyone participating in the discussion to share or experiment with different ideas and be open to hearing other ideas. This would be the opposite of focusing a discussion on a single perspective or trying to determine the "optimal" way to think about something together. 
* **Ask expansive questions** -- inviting intellectual curiosity in a discussion can assist with navigating conflict (conflict isn't bad, it just needs to be managed!). Asking expansive questions (e.g., what possibilities exist? what's the state space look like?) as opposed to questions that attempt to "narrow in" on a particular perspective/answer/topic can assist the group in becoming more creative and open to ideas.
* **Set discussion norms** -- for long discussions, it can be nice from the start to set norms for a discussion. If this can be done collaboratively, all the better! Having a framework that explicitly talks about the goals of a discussion, appropriate engagement with a discussion, and actions participants can take to address violations to the framework, can be a really useful technique in professional settings for talking about challenging topics productively.
* **Don't be afraid to pivot** -- if a discussion is getting off the rails, or you're reading the room and think that a conversation may turn unproductive, consider switching to a different discussion tactic, tabling a topic for later and moving to another question, or naming the conflict that you are seeing and allowing for meta-conversation about that conflict. 
* **Critique over criticism** -- it will be natural for folks to come with different perspectives on a topic. If conflict were to arise between perspectives, encourage critique of the ideas rather than criticism of those that hold those perspectives. Critique requires asking questions, trying to learn more, and building/improving upon an idea, whereas criticism is meant to highlight negatives and tear a perspective down.
* **Focus on evidence-based claims** -- discussions are most intellectually full when ideas that are shared are coupled with evidence that can be collaboratively inspected. Inviting opinions and feelings into a conversation is welcome, but ask participants to enrich those ideas with grounded personal anecdotes as their form of evidence.

What are other norms or expectations that we should have for one another in our conversations ahead?


## We're All Living in a 1D World! Part 1: Simulation Intuition

Let's see how particle filtering might manifest computationally. To get the code for today you will need to make sure your environment is setup with matplotlib and scipy. If you want to check you can use

{% include codeHeader.html %}
```bash
pip3 show matplotlib scipy
```

If you get any warnings about package(s) not found, you can install them with ``pip3``.  For example, if you didn't have either package, you can use the following command to install the necessary libraries.

{% include codeHeader.html %}
```bash
pip3 install matplotlib scipy
```

Additionally, if you haven't done so yet, clone [the class activities are resources repo](https://github.com/comprobo25/class_activities_and_resources) into your ``ros2_ws/src`` folder.  If you've already cloned it, make sure to do a ``git pull origin main``.

Next, make sure to build your workspace and source your ``install/setup.bash`` file.

```bash
$ cd ~/ros2_ws
$ colcon build --symlink-install
$ source install/setup.bash
```
### Launch a Simulated World
To try things out, let's first startup a 1d simulation of the world. 

{% include codeHeader.html %}
```bash
ros2 run simple_filter simple_filter_world.py --ros-args -p walls:=[0.0,3.0]
```

Take a look at the topics that are being published.  What types of messages are there?  What topics correspond to which messages?  We'll go through this as a class.


### Launch a Particle Filter
Next, we will experiment with our first particle filter:

{% include codeHeader.html %}
```bash
ros2 run simple_filter simple_particle_filter.py --ros-args -p walls:=[0.0,3.0] -p nparticles:=100
```

A visualization should come up.  The visualization shows the position of all the particles, the particle weights, and the true position.  Additionally, a histogram is generated that shows the belief about where the robot is.

### Explore the World -- Where Are You?

You can move your robot around using the following ROS node:

{% include codeHeader.html %}
```bash
ros2 run simple_filter simple_controller.py
```

To use this node make sure the window that pops up has focus, and use the ``a`` key and the ``d`` keys to move around left to right, respectively.

What happens over time to your visualization?

Try different wall configurations to see what happens.  What happens as you change the number of particles?  What happens if the wall configuration of the simulator and the particle filter model don't match up? 

Construct a scenario where there is an inherent ambiguity in determining where the robot is.  How do you do this?  What happens when you run your particle filter?


## The Particle Filter Algorithm
We're going to kick-off this project with a bit more of analytical dive into a particle filter algorithm, then look at some sample code to ground our understanding in implementation. 

### What Does the Robot Know? What Can the Robot Sense?
In our lives, we "localize" by observing our surroundings, maybe checking our GPS location, and referencing a map of our area (either conceptual or actual) to claim "we are here." The robot needs to do the same thing in this project. We can assume the following about our robot:

1. It has a _map_ of the region it is in, but **it does not know where it is within that map**
2. It can observe the world through bumps and laser scans; those sensors are rigidly attached to the body of the robot. **These sensors are noisy**
3. It can explore the world by rolling around; it can **guesstimate how far it has rolled** by keeping track of its velocity and wheel turns.

### Coordinate Systems
There are several coordinate systems that we'll want to consider when localizing:
* ``map`` -- the coordinate system of the map/environment that the robot is in
* ``odom`` -- the coordinate system that _initializes where-ever the robot is_ and in which the robot's motion is tracked
* ``base_footprint`` -- the coordinate system that is attached the robot (where laserscans would be in reference to, for instance)

Which of these are static relationships? Dynamic? How would we think about updating any relationship between these frames?

### The Steps (At a High Level)
We're going to walk through the high-level steps of a particle filter, highlighting along the way the different opportunities for design choices you have as a software engineer. We'll be connecting with the video you watched prior to this class to discuss.

The key steps:
1. **Initialize** Given a pose (represented as $$x, y, \theta$$), compute a set of particles.
2. **Motion Update** Given two subsequent odometry poses of your robot, update your particles.
3. **Observation Update** Given a laser scan, determine the confidence value (weight) assigned to each particle.
4. **Guess** Given a weighted set of particles, determine the robot's pose.
5. **Iterate** Given a weighted set of particles, sample a new set.

Steps 3 and 5 are typically considered the "tricky" ones to implement. Let's take some time to brainstorm possible methods that could be adopted (at a high level) to solve these challenges.

## We're All Living in a 1D World! Part 2: Code Dissection
Group up with the folks around you, and have a look at the code for the ``simple_particle_filter`` demo we ran earlier in class. Diagram out the code and topics...can you map different functions/classes of the code to the high-level steps we've outlined in class? What are you noticing about the implementation? What questions do you have about the techniques used?

## Project Kick-Off
Starting today, the particle filter project is a-go! There is [skeleton code available for this project](https://github.com/comprobo25/robot_localization), which I recommend you have a look at now. The rest of this class will be studio time for team formation and getting started with your first deliverable (a conceptual overview).

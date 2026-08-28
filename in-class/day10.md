---
title: "Applications II // Bayesian Estimation"
toc_sticky: true
toc_data:
  - title: Today
    link: in-class/day10/#today
  - title: For Next Time
    link: in-class/day10/#for-next-time
  - title: Applications II Discussion
    link: in-class/day10/#applications-ii
  - title: Bayesian Estimation Mini-Lecture
    link: in-class/day10/#bayesian-estimation
  - title: Breakout Sessions + Studio
    link: in-class/day10/#breakout-sessions
---

# WORK IN PROGRESS! CHECK BACK FOR UPDATES!


## Today
* Broader Impacts Applications II Discussions
* Mini-Lecture on Bayesian Estimation
* Studio Time and Breakout Sessions -- 
  * Computing Relative Motion
  * Likelihood Models
  * Details of a Bayes Estimation
 
## For Next Time
* Work on the [Robot Localization project](../assignments/robot_localization)
  * Demos due on **Thursday October 16 by Class**
  * Code + Writeups due on **Friday October 17th 7PM**
* Review your Broader Impacts Phase 1 feedback (emailed)
* Consider whether there is [feedback you'd like to share about the class](https://forms.gle/kPjvgWb4ETDKMHRD7)

## Applications II: AI x Robotics - Dealing with Novelty
Last time we talked a bit about different ways of thinking about AI applied to robotic systems, and one challenge with directly implementing modern AI systems (e.g., genAI or large supervised models) on robots: novelty.

Within the realm of AI tools, there are two that have been widely adopted in robotics to attempt to address the novely problem: reinforcement learning and active learning. In this activity, we're going to learn a bit more about one of these techniques and consider their implications of use. 

To begin, in your table group, decide whether you would like to learn more about reinforcement learning or active learning; there will be an info exchange with another group so don't worry too much about missing out! Once you've made your decision, follow-along with the corresponding activity below.

Every individual shoud also be taking notes during the discussion [in this survey](https://forms.gle/s5mZ2TtnycqyPVgE6).

### Reinforcement Learning
Let's start with a definition of reinforcement learning:
> An agent (robot) develops a policy for interacting with the world / performing some task, based on many interactions and recieving a penalty or reward.

In other words, RL for a robot is learning how to do a task through trial and error. For those interested, you can read a lot more [in this IJRR survey paper on the topic](https://www.ri.cmu.edu/pub_files/2013/7/Kober_IJRR_2013.pdf).

**Discussion Question 1**: Using at least one of the robots someone in your group is studying for the Broader Impacts project, determine how that robot would use RL to perform one of the key tasks of that robot. Consider the following:
  * What resources would the robot need? (e.g., access to a particular environment, person, object)
  * What would a trial look like for that robot? What metrics would determine when a trial was "over" and could be scored?
  * How would a robot label a trial as "successful" for that task?


In Robotic RL, there is a set of well known "curses" that make implementation challenging:
  * **The Curse of Dimensionality**: problems often scale exponentially in the number of dimensions to compute optimal policies over
  * **The Curse of Real-World Samples**: robot hardware is expensive (and typically one-off!), suffers from wear and tear, and is in a really noisy, partially observable environment
  * **The Curse of Abstraction and Model Uncertainty**: all models are wrong, some are useful, and its challenging to know what "useful" means
  * **The Curse of Goal Specification**: we reward a robot for doing a "good job" but need to have a formalism for what the job is in order to assess it; but many jobs are complex and hard to define

**Discussion Question 2**: For the robot you've discussed, let's think about some of these curses:
  * Which of these curses do you think is most pressing for your robot, why?
  * How might you think about addressing this curse? Some things to consider: simulation tools, problem simplification, task subdivision and composition, embedding prior knowledge, etc.
  * What might the cost (in time, money, energy, people, task...) be for implementing this work-around for your robot? Do you think it would be worthwhile? Why or why not?

For robots operating in real-world conditions, there is almost always some risk of encountering something novel -- something outside of a training set or only rarely seen in that training set. A lot of [modern research in AI](https://news.mit.edu/2022/machine-learning-biased-data-0221) has focused on how to eliminate bias or leverage diversity in datasets for better performance.There are a lot of design considerations one needs to make as a software engineer and a robot operator to decide what method will be best for a particular system.

**Discussion Question 3**: Finally, let's consider the implications of training your robot with RL systems:
  * How might you shape the training set for your robot system, and why? Some options could include: over-sampling "rare instances" to be more equal with typical instances, starting with a strong prior distribution over known task examples, add noise to all samples, etc.
  * How might you change the model implementation for your robot system to be more robust to novelty, and why? Some options could include: train multiple policies for different classifications of instances/tasks, change the reward function to consider uncertainty over task actions, output a measure of uncertainty for a particular response to a task input, etc.
  * What would the potential consequences be if your robot encountered a novel event from its training data? What would its ideal reaction be?


### Active Learning
Let's start with a definition of active learning:
> An agent (robot) develops a policy for interacting with the world / performing some task, while engaged in that activity, by seeking out informative interactions.

In other words, active learning for a robot allows the robot to make strategic, informative experiments to help it complete its given task. For those interested, you can read a lot more [in this Mechatronics paper on the topic for robotic control](https://tberrueta.github.io/assets/pdfs/TaylorMechatronics2021.pdf).

In active learning, a robot needs to be able to keep track of a model of the world/environment it is in, and how its actions impact that world (and lend itself towards as task). This is known as keeping a *belief* representation over the world. You can think about this as a list of facts that a robot is discovering about itself or the world as it experiments. The process of generating a good belief representation is critical: this is what it will use to eventually plan out the action policies it will use when given a task to perform.

**Discussion Question 1**: Using at least one of the robots someone in your group is studying for the Broader Impacts project, determine how that robot would use active learning to perform one of the key tasks of that robot. Consider the following:
  * What resources would the robot need to build a good belief representation of the world/environment/task? (e.g., access to a particular environment, person, object)
  * How could the robot decide what a "useful" experiment would be to perform to gain new facts about the world? 
    * Make a list of experiments you would deem as "useful" and "not useful" for your robot -- do your lists change depending on the order that the robot executes these experiments?

In active learning for robotics, a typical driver for selecting a useful experiment are information measures -- statistical measures that will tell a robot how much information would be gained by collecting an observation / conducting an experiment. Some information measures are things like: variance, covariance, entropy, and mutual information. The most important part, however, is the ability to represent how uncertain a robot is and help it pick how to best reduce that uncertainty.

**Discussion Question 2**: For the robot you've discussed, let's think about the definition of uncertainty:
  * For the robot you selected, what are things that the robot will definitely know about itself and its environment? What are things that can change about the robot or environment between tasks?
  * For the things that can change, can the robot directly or indirectly observe those things (e.g., for location, does the robot have a GPS or only a Lidar measurement)?
  * For the things that the robot can only indirectly observe, what can the robot do through experimentation to infer more about its environment (e.g., move around, ask a human for assistance, ask another robot for assistance, access an external sensing system)?

For robots operating in the real world, active learning can be super powerful for one-shot deployments when training a robot for a particular task would be literally impossible, but it can come at the cost of overall task efficiency and efficacy. This leads to a common trade-off in active learning:
  * **Greedy** behavior -- also known as exploitative behavior, this is the idea that the robot will tend toward completing a task with only partial knowledge of the environment
  * **Exploratory** behavior -- this is the idea that a robot will tend toward exploring until it has near complete knowledge of an environment before executing a task

**Discussion Question 3**: Finally, let's consider the implications of deploying active learning on your robot:
  * What would the potential consequences be if your robot needed to experiment for a very long time before it completed a task? What would the potentially consequences be if your robot attempted a task and failed?
  * Should your robot be more greedy or exploratory? Why or why not?

### Cross-Topic Jigsaw
We're going to mix up the groups so you can talk to some RL folks and some Active Learning folks. In your cross-topic groups, please:
  * Share the definition of RL/Active Learning and the example robot you discussed
  * Highlight one or two key ideas that your group really got into the weeds of
  * Generate lingering questions you might have about learning based methods in robotics



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


## Breakout Sessions
To learn more about the fundamental theory behind Bayesian Estimation, feel free to stick around in the classroom; if you'd like to continue working through the Motion Model, Likelihood Model, or particle filter project, you can work on self-study next door!

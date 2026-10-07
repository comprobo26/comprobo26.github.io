---
title: "Beyond Particle Filtering"
toc_sticky: true
toc_data:
  - title: Today
    link: in-class/day12/#today
  - title: For Next Time
    link: in-class/day12/#for-next-time
  - title: Localization Project Share-Out
    link: in-class/day12/#localization-share
  - title: Beyond Particle Filtering
    link: in-class/day12/#beyond-particle-filtering
---

# WORK IN PROGRESS! CHECK BACK FOR UPDATES!


## Today
* Bayesian Filtering Mathematical Principles
* Beyond Particle Filtering Mini-Lecture (optional)
* Studio Time

## For Next Time
* Turn in the [Robot Localization project](../assignments/robot_localization)
  * Code + Writeups due on **Tuesday October 21st 7PM**
  * Localization Project Share-Out and Demos, due **Monday October 20th by Class**
* Read over the [Broader Impacts assignment Part 2](../assignments/broader_impacts), due on **November 4th at 7PM** 
  * In class discussions on **Monday November 3rd**
* Read over the [Machine Vision Project Document](../assignments/computer_vision_project).
    * Project Proposal is due on **Wednesday October 22nd at 9PM**. We'll have some in-class time next week to create these proposals.
* Consider whether there is [feedback you'd like to share about the class](https://forms.gle/kPjvgWb4ETDKMHRD7)


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


## Beyond Particle Filtering (Optional Mini-Lecture)
In this optional mini-lecture and activity, we'll discuss a different class of Bayesian filter for state estimation and localization: the Kalman filter. The coding activity for this mini-lecture can be pulled from [this repository](https://github.com/comprobo25/recitation_examples/tree/main/kalman_filters) -- note that this only requires Python to run; this is not a ROS2 based example. For those interested in going even further, you can play with this [CoLab Notebook from 2024](https://colab.research.google.com/drive/1Sbm81zccVfqPNaV6w9rdGH56F1uCTUIF?usp=sharing) which provides Extended Kalman Filter code.

The Kalman filter, like the particle filter, is part of the class of Bayesian filters. Like all Bayesian filters then, it is operationalized into the following steps:
```
1) Initialize with an estimate of the first pose
2) (Predict) Take an action, and predict the new pose based on the motion model
3) (Correct) Correct the pose estimate, given an observation
4) Repeat steps 2 and 3, ad nauseum (or until your robot mission is over)
```

The special assumption of a Kalman filter is that the world is (statistically) normal -- that is, we can use Gaussian distributions to describe our uncertainty about the world. Let's think about this problem for a very simple situation: a runaway Neato moving in a 1D world.

### Defining a State Variable and State Covariance
The _state_ of our world is our Neato's position and velocity. We only get noisy estimates of the Neato position, and have no information about velocity. We can use the notation:

$$\mathbf{x} = [x, \dot{x}]^T$$

to represent the state of our Neato.

Since we're representing everything as a Gaussian, we need to define the variance we associate with our state (basically, how uncertain we are about our state). Since we have a two dimensional satae, our covariance will be a 2x2 matrix:

$$\mathbf{P} = \left[
\begin{matrix}
\sigma_{xx} & \sigma_{x\dot{x}}\\
\sigma_{\dot{x}x} & \sigma_{\dot{x}\dot{x}}
\end{matrix}
\right]$$

where the diagonal elements are the variance in the state variables themselves, and the off-diagonal elements are the covariances between variables.

### The Prediction Step
Also sometimes referred to as the "process model" in literature, this captures the (statistically) expected motion of our Neato. Since we're explicitly keeping track of uncertainty here, we must advance both our state and our uncertainty according to our transition model.

Since we are tracking the Neato moving in 1D, we might use the following model:

$$\hat{x_t} = v\Delta t + x_{t-1}$$

Vectorized per our defintion of state variable:

$$\hat{\mathbf{x}_t} = \mathbf{F}\mathbf{x}_{t-1}$$

$$ \left[\begin{matrix} \hat{x_t} \\ \hat{\dot{x_t}} \end{matrix}\right] = \left[
\begin{matrix}
1 & \Delta t\\
0 & 1 \end{matrix} \right] \left[\begin{matrix} x_{t-1} \\ \dot{x_{t-1}} \end{matrix}\right]$$

For advancing our state covariance, we can use:

$$\hat{\mathbf{P}_t} = \mathbf{F}\mathbf{P}_{t-1}\mathbf{F}^T + \mathbf{Q}$$

where $$\mathbf{Q}$$ is simply some process noise (we typically assume this to be zero-centered white noise).

### The Correction Step
If we only had the prediction step, we'd basically be doing _dead-reckoning_ or open-loop estimation. But we can do better!

First, we need to define a measurement model. In our world, we can get noisy measurements of our position, but not of our velocity. Thus, we can define a residual function (the difference between our observation and our hypothesized observation per our update step) as:

$$ \mathbf{y} = \mathbf{z} - \mathbf{H}\mathbf{x}$$

$$\mathbf{H} = [1, 0]^T$$

where $$\mathbf{H}$$ is our sensor model.

Now, we want to update our pose estimate given our observation; to do this, we're going to compute the _Kalman gain_ -- we can think of this as a weight that uses our uncertainty to place our final pose estimate somewhere between our predicted pose and our residual (measured) location. The Kalman gain has the following structure:

$$K_t = \hat{\mathbf{P}_t}\mathbf{H}^T(\mathbf{H}\hat{\mathbf{P}_t}\mathbf{H}^T + \mathbf{R})^{-1}$$

where $$\mathbf{R}$$ is the observation noise on $$z$$.

Finally then, we can update our pose estimate and covariance as:

$$\mathbf{x}_t = \hat{\mathbf{x}_{t}} + K_t(z_t - \mathbf{H}\hat{\mathbf{x}_{t}})$$

$$\mathbf{P}_t = (\mathbf{I} - K_t\mathbf{H})\hat{\mathbf{P}_{t}}$$

where $$\mathbf{I}$$ is the identity matrix.

### Affordances and Notes
One of the advantages of the Kalman filter is that it allows us to keep track of a closed form of uncertainty, which allows us to do interesting work at every step of the filter (of course, at the expense of assuming the world is Gaussian). 

One of the advantages of this closed form update step, with explicit models for world physics, is that we can directly estimate un-observables -- for instance, take velocity in this example. We never get an observation of velocity directly, however, we can refine our estimate of velocity alongside our estimate of position because we have a direct relationship between these variables and their covariances.

Many modern estimation algorithms in robotics rely on some form of Kalman filter. SLAM (simultaneous localization and mapping) has long used an Extended Kalman Filter (EKF) backbone to jointly estimate both robot pose and map at the same time. If you'd like to learn more, you can check out this [presentation on EKF SLAM](http://ais.informatik.uni-freiburg.de/teaching/ws12/mapping/pdf/slam04-ekf-slam.pdf) and this [5 minute SLAM overview](https://www.youtube.com/watch?v=BuRCJ2fegcc), both by Cyrill Stachniss.

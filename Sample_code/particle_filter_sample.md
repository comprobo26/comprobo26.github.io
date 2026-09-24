---
title: "A Simple Particle Filter"
toc_sticky: true 
source1: "simple_particle_filter/simple_particle_filter.py" 
---

## A Simple Particle Filter

This is an example of a simple particle filter, made for a demonstration in our [class_activities_and_resources](https://github.com/comprobo26/class_activities_and_resources) repository. A robot can move back and forth in a 1D robot, and detect walls that are next to it. Using these detections and a noisy motion model, the particle filter is used to guess the location of the robot in the world.

<a href="{{ page.source1 }}">Source: simple_particle_filter.py</a>

{% highlight python %}
{% include_relative {{ page.source1 }} %}
{% endhighlight %}

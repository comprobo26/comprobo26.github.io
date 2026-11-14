---
title: "Tips and Tricks // Final Project Studio"
toc_sticky: true
toc_data:
  - title: Today
    link: in-class/day22/#today
  - title: For Next Time
    link: in-class/day22/#for-next-time
  - title: Tips and Tricks 
    link: in-class/day22/#tips-and-tricks
  - title: Final Project Studio 
    link: in-class/day22/#final-project-studio
---

## Today
* Tips and Tricks: Namespaces, Launch Files, and Project Development Advice
* Final Project Studio

## For Next Time
* Final Project [Milestone 1](https://canvas.olin.edu/courses/1070/assignments/20104) will be due **Sunday November 22nd at 7PM**
  * [Milestone 2](https://canvas.olin.edu/courses/1070/assignments/20105) will be due **Monday December 7th at 7PM** 
  * The [Project Showcase](https://canvas.olin.edu/courses/1070/assignments/20100) (final event) will be **Tuesday December 15th 8-11AM**
  * The [Final Project](https://canvas.olin.edu/courses/1070/assignments/20111) will be due **Tuesday December 15th at 7PM**
* Work on the [Broader Impacts Phase 3](../assignments/broader_impacts.md), due on **Friday December 11th at 7PM**
* [Last Call!] Sign-up for a [technical interview slot](../assignments/technical_interview.md) if you'd like to participate in the pilot!

## Tips and Tricks: Namespaces, Launch Files, and Project Development Advice
As you work on your projects, it is useful to consider a few tools at your disposal that we haven't had a chance to discuss in detail. This is a quick overview, and additional notes are available [here](https://github.com/comprobo25/robo_tools_ca_lecture).

### Bash Scripting
Bash scripts are a way to write, save, and execute a series of terminal commands. Bash scripts allow you to perform some logic when executing commands, such as automating parameter sweeps for commands with input variables, or catching and skipping failed simulation runs. 

You can learn more about bash scripting from these resources:
* [CodeAcademy Bash and Shell Courses](https://www.codecademy.com/catalog/language/bash?--&utm_id=t_kwd-374328821491:ag_142977825990:cp_10030170703:n_g:d_c&utm_source=google&utm_medium=paid-search&utm_term=how%20to%20learn%20bash%20scripting&utm_campaign=US_Language:_Basic_-_Exact&utm_content=631309442528&g_adtype=search&g_acctid=243-039-7011&gad_source=1&gad_campaignid=10030170703&gclid=CjwKCAiAquDXBhApEiwAoyNqBO2K9i9kx9JZfPg6GeoXxU4FNOcKpTtVJjFYR-2c1mCpk8vjK9zr-xoCO2EQAvD_BwE)
* This [straightforward tutorial](https://www.freecodecamp.org/news/bash-scripting-tutorial-linux-shell-script-and-command-line-for-beginners/) for basic scripting syntax
* Check out some [cheatsheets](https://devhints.io/bash)

As it applies to this class, here is an example of a bash script that sets up launching multiple neatos: [Example Script](https://github.com/comprobo25/robo_tools_ca_lecture/blob/main/fleet_launch.sh)

### Launch Files
When developing in a ROS2 environment, we often find ourselves running multiple nodes all of the time; a launch file helps us put all those nodes in one place and launch them from a single command. We've been using launch files throughout this course, but now you might want to take some time to make one for yourself!

The advantage of a launch file, other than keeping your terminal from getting cluttered, is that you can control the order in which nodes launch and ensure that is consistent every time -- this is helpful for debugging, test repeatability, and is just good practice.

We recommend having a look at the launch files we've been using in this class to start to dissect them and perhaps use them as templates. The [ROS2 documentation](https://docs.ros.org/en/jazzy/Tutorials/Intermediate/Launch/Creating-Launch-Files.html) is another useful source. For good tutorials on writing a launch file, checkout:
* This video series! [Part 1](https://www.youtube.com/watch?v=Da9qeDdMauY&list=PL8MgID9MCju0GMQDTWzYmfiU3wY_Zdjl5&index=10) and [Part 2](https://www.youtube.com/watch?v=A8djMH4Zxd0&list=PL8MgID9MCju0GMQDTWzYmfiU3wY_Zdjl5&index=11)
* This written overview by [Foxglove](https://foxglove.dev/blog/how-to-use-ros2-launch-files)
* This [lecture](https://discourse.openrobotics.org/t/mastering-launch-files-in-ros2-a-comprehensive-tutorial/30911)

As it applies to this class, here is an example of a launch script for multiple neatos: [Example Script](https://github.com/comprobo25/robo_tools_ca_lecture/blob/main/bringup_multi.py)

### Namespaces
Especially if you are working with distributed systems (e.g., multiple robots, multiple computers), you may want to pay attention to _namespaces_. If you've done development in C or C++ before, this might feel like a familiar concept. Essentially, a namespace is a "tag" for a particular computer, which can be applied to topic names, subscriptions, services, etc. This allows multiple computers to have "an address" and avoid conflicts like multiple nodes publishing to `/cmd_vel` or similarly important topic. [These notes](https://github.com/comprobo25/robo_tools_ca_lecture/blob/main/Lecture.md) highlight how namespaces might be handy for this course, and [this ROS2 tutorial](https://docs.ros.org/en/jazzy/Tutorials/Intermediate/Launch/Using-ROS2-Launch-For-Large-Projects.html) contains notes about namespaces and other considerations for working on large projects.   

### Development Advice for Collaborative Projects
* Design your interfaces together, and stick with the architecture; knowing what inputs and outputs you need helps to separate coding tasks
* Pair program when possible
* Use branches to develop code independently, and use pull requests for review before merging into main
* Pull and push often; ideally each pull request is *small* and keeps the code functionally running
* Write specific commit messages; they should contain what was changed and major behavior differences

## Studio Time
Members of the teaching team will visit with each group to check-in prior to the Thanksgiving break holiday.



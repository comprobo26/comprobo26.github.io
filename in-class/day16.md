---
title: "Human-Robot Interaction II // CA Lecture: Light Fields"
toc_sticky: true
toc_data:
  - title: Today
    link: in-class/day16/#today
  - title: For Next Time
    link: in-class/day16/#for-next-time
  - title: Human-Robot Interaction II Discussion
    link: in-class/day16/#human-robot-interaction
  - title: CA Lecture - Light Fields
    link: in-class/day16/#ca-lecture-light-fields
---

## Today
* Human-Robot Interaction II -- Search and Rescue Continued
* CA Lecture: 3D Dynamic Reconstruction for Soft Corals with Light Fields
* Studio Time

## For Next Time
* Work on [Broader Impacts Phase 2](../assignments/broader_impacts)
  * In class discussions on **Monday November 2nd**
  * Materials due **Tuesday November 3rd** (See [Canvas Page](https://canvas.olin.edu/courses/1070/assignments/20095))
* Work on the [Machine Vision Project Document](../assignments/computer_vision_project).
    * Project Shareouts will be **Monday November 9th in class**
    * Project Materials are due on **Tuesday November 10th at 7PM**
* Please provide feedback and weigh-in on an extra credit opportunity! [Poll](https://forms.gle/zVMMPGQrxwBxWfj86)


## Human-Robot Interaction: Search and Rescue Continued
Last time, we read a bit of literature about search and rescue robots, and had a discussion around intended use. Today, we're going to further discuss the human-robot interaction element, and specifically think about how we, as engineers, think about creating _formal standards_ for robot performance. 

For our conversation today, please fill in [this survey](https://forms.gle/nFkuGYhFWjea28bF8).

### Setting Standards for SAR
In the US, the Federal Emergency Management Agency (FEMA), Homeland Security, and the Department of Defense are among the largest customers of SAR robots. In partnership with NIST (the National Institute of Standards and Technology), the guidelines for an effective/useable SAR system for urban environments has been defined ([you can read more here](https://www.nist.gov/system/files/documents/el/isd/ks/Prelim_Requirements_Report.pdf)) and covers the following:

* Human-System Interaction (23 requirements)
* Logistics (10 requirements)
* Operating Environment (5 requirements)
* System (physical robot) (65 requirements; 32 of which are for sensing)

One of the fascinating things about these requirements is that "Human-System Interaction" primarily covers the _robot operator_ but not the interaction with a possible human rescuee. In your small groups, consider the following questions from the perspective of a NIST engineer tasked with setting requirements for a SAR robot (I recommend picking one or two to focus on):

* What would/should official standards for Human-System Interaction cover for the rescuee of a SAR robot? 
  * You may want to consider: interfaces (virtual, sensory, or physical); accessibility; meta-safety; inclusivity...
* How would these standards interact with your robot's sensors? Algorithms?
  * You may want to consider: role of automation/autonomy; consequences of perceptual limitations; edge-cases for perception choices; introduction of bias (implicit or explicit); verifiability; explainability...
* Who should be involved in co-designing this set of standards for this group of stakeholders?
  * The current standards were set based on several workshops with experts in the field (peep the list in the linked report above...notice anything interesting about this group?)
* What tests would need to be designed to assess whether a robot met these standards?


## CA Lecture: 3D Dynamic Reconstruction for Soft Corals with Light Fields
Today we're going to hear from Vivian on current research work she is conducting on using a unique camera configuration to generate high quality 3D reconstructions of dynamic objects, applied to ecological studies of coral reefs. This is an example of how some of the concepts you're exploring in your machine vision projects can be adapted to frontier research questions. You can follow along [with slides here](https://docs.google.com/presentation/d/1UxAYL3YCDhmglfxgEfTMvhmOqyRLfkY2P92FtGlfPwc/edit?slide=id.g38e10bf72ea_0_13#slide=id.g38e10bf72ea_0_13).


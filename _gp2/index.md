---
title: Guided Project 2 WolfScheduler - Activity and Event
tags: [software engineering, software lifecycle, CS2, CSC216, GP2]
description: Guided Project 2 Introduction
pagegroup: gp2
---

# Guided Project 2 Introduction

**Target Audience:** this guided project is geared toward the beginning Java programmer who has some experience with using Eclipse.

A paradigm of good design is to reduce redundancy.  You want to have code in one location (it's easier to maintain) and reuse that code as much as possible.  In [Guided Project 1](../gp1/), you explored the composition relationship.  You could encapsulate code in a single class (e.g., `Course`) providing an abstraction that could be used by other classes (e.g., `WolfScheduler`).  The container class `WolfScheduler` could then delegate to the contained class `Course`.  

Composition is one type of relationship in object-oriented programs.  The other relationship is *inheritance*.  Inheritance is when one class extends or specialized another class.  The common code goes in the parent and the extension goes in the child.  

Guided Project 2 builds on [Guided Project 1](../gp1/) through another iteration of the the phases of the [software lifecycle](../se-overview/).  You will continue to work with [software practices and tools that support those practices](../se-overview/#software-development-practices-and-tools) in Guided Project 2.


  

## WolfScheduler System
You will implement and test PART of the [WolfScheduler](../wolf-scheduler/index) system.  The WolfScheduler system provides a way for a student to determine which course schedule may be best for them in an upcoming semester.  

You will develop the WolfScheduler project over the course of the three guided projects.  The [WolfScheduler requirements](../wolf-scheduler/ws-requirements) describe the fully implemented system.  Guided Project 2 will complete the requirements **except for checking for conflicts between events and courses**.
  
  * [Use Case 1: Load Course Catalog](../wolf-scheduler/ws-requirements#uc1)
  * [Use Case 2: Rename Schedule](../wolf-scheduler/ws-requirements#uc2)
  * [Use Case 3: View Course Information](../wolf-scheduler/ws-requirements#uc3)
  * [Use Case 4: Add Course to Schedule](../wolf-scheduler/ws-requirements#uc4)
  * [Use Case 5: Remove Course from Schedule](../wolf-scheduler/ws-requirements#uc5)
  * [Use Case 6: Add Event to Schedule](../wolf-scheduler/ws-requirements#uc6)
  * [Use Case 7: Remove Event from Schedule](../wolf-scheduler/ws-requirements#uc7)
  * [Use Case 8: Reset Schedule](../wolf-scheduler/ws-requirements#uc8)
  * [Use Case 9: Display Final Schedule](../wolf-scheduler/ws-requirements#uc9)
  * [Use Case 10: Export Schedule](../wolf-scheduler/ws-requirements#uc10)
  
You will complete the functionality for handling schedule conflicts in Guided Project 3.  There are expectations from the Guided Projects that you must follow.  Do NOT attempt to implement any functionality before a Guided Project tells you to do so!

As part of the Guided Project, you are expected to run the provided JUnit tests and acceptance tests to ensure that your implementation meets the requirements and design of the system.


## Tasks
{% include iconHeader.html type="task" %}
{% include tasks.html assignment=page.pagegroup %}

{% capture print %}{% include printable.html %}{% endcapture %}
{{ print }}



## Grading Rubric
{% include iconHeader.html type="rubric" %}

Your Wolf Scheduler Guided Project 2 will be evaluated on the following items:

### Overall Rubric

{% include rubricTable.html project="gp2" grade-category="overall" %} 

### Deductions

{% include deductionsRubricTable.html project="deductions" grade-category="overall" %}

### Javadoc Rubric

{% include javadocRubricTable.html project="javadoc" grade-category="overall" %}

## Jenkins Server
{% include iconHeader.html type="ciTool" %}

We are using the Jenkins Continuous Integration system to automatically evaluate your work and provide feedback on your submission.  Go to the Guided Project and Project Jenkins Server by using [{{site.data.grades.jenkins-server}}]({{site.data.grades.jenkins-server}}).  
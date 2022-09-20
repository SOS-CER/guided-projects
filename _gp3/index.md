---
title: Guided Project 3 WolfScheduler - Conflict
description: Guided Project 3 Introduction
tags: [software engineering, software lifecycle, CS2, CSC216, GP3]
pagegroup: gp3
---

# Guided Project 3 Introduction
**Target Audience:** this guided project is geared toward the beginning Java programmer who has some experience with using Eclipse, inheritance, and running test cases.

An important practice for ensuring that software works correctly is to test it and run other verification and validation tools to minimize programmer mistakes.  Since no one practice can identify all faults, developers work with a suite of practices and tools to help find problems in their code. 

One practice that developers frequently use is *test driven development* (TDD).  In TDD, a developer starts by writing tests, then uses those test to drive forward development of the implementation.  By writing system and unit tests before writing the implementation, a developer can better understand the context of the problem and the area of the solution.     

Guided Project 3 builds on [Guided Project 1](../gp1/) and [Guided Project 2](../gp2/) through another iteration of the the phases of the [software lifecycle](https://pages.github.ncsu.edu/engr-csc-software-development/software-lifecycle), with an emphasis on using TDD to implement the new features.  You will continue to work with [software practices and tools that support those practices](https://pages.github.ncsu.edu/engr-csc-software-development/practices-tools/overview/) in Guided Project 3.

 

## WolfScheduler System
{% include iconHeader.html type="requirements" %}
You will implement and test the remainder of the [WolfScheduler](../wolf-scheduler/) system, with an emphasis on conflict identification and resolution.  The WolfScheduler system enables a student to determine which course schedule may be best for them in an upcoming semester.  

You will develop the WolfScheduler project over the course of the three guided projects.  The [WolfScheduler requirements](../wolf-scheduler/ws-requirements) describe the fully implemented system.  Guided Project 3 will focus the **[Schedule Conflict]** alternative flows of Use Cases 4 & 6 around time (with an assumption of no regression in functionality on the already implemented requirements):
  
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
  
As part of earlier Guided Projects, you were provided with a suite of unit and system tests.  **You will now be adding new tests for the time conflict functionality.**  *You may have to update the provided tests.  Some may fail due to the addition of the new time conflict functionality.*


## Tasks
{% include iconHeader.html type="task" %}
{% include tasks.html assignment=page.pagegroup %}

{% capture print %}{% include printable.html %}{% endcapture %}
{{ print }}

## Grading Rubric
{% include iconHeader.html type="rubric" %}

Your Wolf Scheduler Guided Project 3 will be evaluated on the following items:

### Overall Rubric

{% include rubricTable.html project="gp3" grade-category="overall" %} 

### Deductions

{% include deductionsRubricTable.html project="deductions" grade-category="overall" %}

### Javadoc Rubric

{% include javadocRubricTable.html project="javadoc" grade-category="overall" %}

## Jenkins Server
{% include iconHeader.html type="ciTool" %}

We are using the Jenkins Continuous Integration system to automatically evaluate your work and provide feedback on your submission.  Go to the Guided Project and Project Jenkins Server by using [{{site.data.grades.jenkins-server}}]({{site.data.grades.jenkins-server}}).  
 
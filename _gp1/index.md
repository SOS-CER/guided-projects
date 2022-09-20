---
title: Guided Project 1 - Software Development Practices and Tools
tags: [software engineering, software lifecycle, CS2, CSC216, GP1]
description: Guided Project 1 Introduction
pagegroup: gp1
---

# Guided Project 1 Introduction
**Target Audience:** this guided project is geared toward the beginning Java programmer who has some experience with Java programming from the command line.

Creating a good software system, one that people want to use, requires more than just writing code. Writing software is a process, called [software engineering](https://pages.github.ncsu.edu/engr-csc-software-development/software-lifecycle/index). Software engineering is a sub-area of computer science where practitioners use processes and practices to develop high quality, performant, and usable software that meet a set of customer requirements.  Tools support these processes and practices.

The Guided Projects will walk you through the phases of the [software lifecycle](https://pages.github.ncsu.edu/engr-csc-software-development/software-lifecycle/index): requirements, design, implementation, test, and deployment.  Additionally, the Guided Projects will introduce you to the [software practices and tools that support those practices](https://pages.github.ncsu.edu/engr-csc-software-development/practices-tools/). 


{% capture callout_content %}
Integrated Development Environments (IDEs) facilitate software development by integrating multiple software development tools into a single application. In this module you will use the Eclipse IDE and tooling in Eclipse to develop and test software.
{% endcapture %}
{% include callout.html content=callout_content icon="ideTool" type="bestPractices" title="Best Practice: Integrated Development Environments (IDEs)" %}


## WolfScheduler System
{% include iconHeader.html type="overview" %}
You will implement and test PART of the [WolfScheduler](../wolf-scheduler/index) system.  The WolfScheduler system provides a way for a student to determine which course schedule may be best for them in an upcoming semester.  

You will develop the WolfScheduler project over the course of the three guided projects.  The [WolfScheduler requirements](../wolf-scheduler/ws-requirements) describe the fully implemented system. Guided Project 1 will focus on the following requirements:

  * [Use Case 1: Load Course Catalog](../wolf-scheduler/ws-requirements#uc1)
  * [Use Case 2: Rename Schedule](../wolf-scheduler/ws-requirements#uc2)
  * [Use Case 3: View Course Information](../wolf-scheduler/ws-requirements#uc3)
  * [Use Case 4: Add Course to Schedule](../wolf-scheduler/ws-requirements#uc4)
  * [Use Case 5: Remove Course from schedule](../wolf-scheduler/ws-requirements#uc5)
  * [Use Case 8: Reset Schedule](../wolf-scheduler/ws-requirements#uc8)
  * [Use Case 9: Display Final Schedule](../wolf-scheduler/ws-requirements#uc9) - only courses
  * [Use Case 10: Export Schedule](../wolf-scheduler/ws-requirements#uc10) - only courses
  
You will complete functionality related to events and schedule conflicts in future Guided Projects.  There are expectations from the Guided Projects that you must follow.  Do NOT attempt to implement any functionality before a Guided Project tells you to do so!

As part of the Guided Project, you will be expected to run provided JUnit tests and acceptance tests to ensure that your implementation meets the requirements and design of the system.


## Tasks
{% include iconHeader.html type="task" %}
{% include tasks.html assignment=page.pagegroup %}

{% capture print %}{% include printable.html %}{% endcapture %}
{{ print }}



## Grading Rubric
{% include iconHeader.html type="rubric" %}

Your Wolf Scheduler Guided Project 1 will be evaluated on the following items:

### Overall Rubric

{% include rubricTable.html project="gp1" grade-category="overall" %} 

### Deductions

{% include deductionsRubricTable.html project="deductions" grade-category="overall" %}

### Javadoc Rubric

{% include javadocRubricTable.html project="javadoc" grade-category="overall" %}

## Jenkins Server
{% include iconHeader.html type="ciTool" %}

We are using the Jenkins Continuous Integration system to automatically evaluate your work and provide feedback on your submission.  Go to the Guided Project and Project Jenkins Server by using [{{site.data.grades.jenkins-server}}]({{site.data.grades.jenkins-server}}).  





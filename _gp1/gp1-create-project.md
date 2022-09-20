---
title: Guided Project 1 - Software Development Practices and Tools
tags: [software engineering, software lifecycle, CS2, CSC216, GP1]
description: Independent Task - Create WolfScheduler
navigation: on
pagegroup: gp1
---


# Independent Task: Create WolfScheduler
{% include iconHeader.html type="task" %}
For the remainder of the tutorial, you'll implement the first part of the WolfScheduler project.

{% capture callout_content %}
  * Create an Eclipse project
  * Create a package
  * Create a class
{% endcapture %}
{% include callout.html content=callout_content icon="objective" type="learningOutcomes" title="Learning Outcomes" %}
  
{% capture callout_content %}
Use the Eclipse IDE to create a Java project, package, and class!
{% endcapture %}
{% include callout.html content=callout_content icon="ideTool" type="bestPractices" title="Best Practice: Integrated Development Environments (IDEs)" %}

{% capture reminder-content %} 
References:

  * Eclipse Project Creation - see [Guided Task: Your First Eclipse Project - Create an Eclipse Project](gp1-eclipse-intro#create-an-eclipse-project)
  * Eclipse Package Creation - see [Guided Task: Your First Eclipse Project - Create a Package](gp1-eclipse-intro#create-a-package)
  * Eclipse Class Creation - see [Guided Task: Your First Eclipse Project - Create a Class](gp1-eclipse-intro#create-a-class)
{% endcapture %} {% include mention.html content=reminder-content title="Eclipse Project, Package, and Class Creation"%}


## Tasks
{% include iconHeader.html type="task" %}

Complete the following tasks to set up your `WolfScheduler` project.

  * Create a new project called `WolfScheduler`.  The project MUST have the exact name `WolfScheduler` with a capital `W` and `S` or the automated grading will not work.
  * Create a new package called `edu.ncsu.csc216.wolf_scheduler.course` in the `src` folder of the `WolfScheduler` project.
  * Create a new Java class called `Course` in the `edu.ncsu.csc216.wolf_scheduler.course` package of the `WolfScheduler` project



## Check Your Progress
{% include iconHeader.html type="glance" %}
Verify that your project has the following structure as shown in text and screenshot form, below.  Note that in the screenshot of the **Package Explorer** the only visible part of the package name is `course` due to [IDE Customization](gp1-eclipse-intro#best-practice-ide-customization).

    WolfScheduler
    |-> src/
        |-> edu.ncsu.csc216.wolf_scheduler.course
            |-> Course
    
    
{% include image.html file="images/WolfSchedulerStructure.PNG" caption="Figure: WolfScheduler project structure" %} 


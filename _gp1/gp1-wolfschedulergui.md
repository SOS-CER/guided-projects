---
title: Guided Project 1 - Software Development Practices and Tools
tags: [software engineering, software lifecycle, CS2, CSC216, GP1]
description: Guided Task - `WolfSchedulerGUI`
navigation: on
pagegroup: gp1
---
 
# Guided Task: `WolfSchedulerGUI`
{% include iconHeader.html type="task" %}
Up to this point, you've been working with *model* classes.  Model classes represent the data and business logic of an application and are part of the **Model-View-Controller (MVC)** design pattern.  MVC provides a separation of the major areas of a large application.  

  * **Model**: data and business logic
  * **View**: view that the users interact with 
  * **Controller**: connection between the view and the model
  
In Java, you can create Graphical User Interfaces (GUIs) using the Swing libraries.  The Swing libraries provide both the *view* and the *controller* aspects of MVC.  In Swing, the view is the look and feel of the application and includes form elements and how they are organized.  The controller is the functionality that connects to the underlying model when the user interacts with the GUI by clicking a button or interacts with other form elements.

You are still learning all of the skills needed to write a GUI.  You'll have the opportunity to write your own (small) GUI later this semester.  Until then, the teaching staff will provide you with GUIs for your Guided Projects, projects, and labs.

{% capture callout_content %}
  * Create `WolfSchedulerGUI`
{% endcapture %}
{% include callout.html content=callout_content icon="objective" type="learningOutcomes" title="Learning Outcomes" %}

{% capture reminder-content %} 
Reminders about Eclipse code creation features:

  * [Guided Task: Your First Eclipse Project - Create a Package](gp1-eclipse-intro#create-a-package)
  * [Guided Task: Your First Eclipse Project - Create a Class](gp1-eclipse-intro#create-a-class)
{% endcapture %}
{% include mention.html content=reminder-content type="reminder" title="Reminder: Eclipse Artifact Creation" %}
## Add the GUI Class
You'll need to create a package for the GUI class, which we typically put in a package with `ui` in the package name.  This helps separate the user interface or GUI code from the model portion of the program.  

### Create `edu.ncsu.csc216.wolf_scheduler.ui` Package
Create a new package called `edu.ncsu.csc216.wolf_scheduler.ui` in the `src` folder of the `WolfScheduler` project.

 
### Create `WolfSchedulerGUI` Class
Create a new Java class called `WolfSchedulerGUI` in the `edu.ncsu.csc216.wolf_scheduler.ui` package of the `src` source directory of the `WolfScheduler` project.

[Copy the code from `WolfSchedulerGUI.java](files/WolfSchedulerGUI.java) into your Eclipse file.

Everything should compile.  If not, you may have a misspelled method name in one of the other classes.  Fix your classes; do NOT change the GUI!

 
{% capture reminder-content %} 
GitHub Resources:

  * [Staging Files](https://pages.github.ncsu.edu/engr-csc-software-development/practices-tools/git/git-staging)
  * [Committing Files](https://pages.github.ncsu.edu/engr-csc-software-development/practices-tools/git/git-commit)
  * [Pushing Files](https://pages.github.ncsu.edu/engr-csc-software-development/practices-tools/git/git-push)
{% endcapture %} {% include mention.html content=reminder-content type="reminder" title="Reference: Staging and Pushing to GitHub"%} 
## Check Your Progress
{% include iconHeader.html type="glance" %}
Before moving on to the next portion of the Guided Project, complete the following tasks:

  - [ ] Make sure that all fields, methods, and constructors are commented.
  - [ ] Resolve all static analysis notifications.
  - [ ] Fix test failures.
  - [ ] Commit and push your code changes with a meaningful commit message. Label your commit with "[GUI]" for future you!
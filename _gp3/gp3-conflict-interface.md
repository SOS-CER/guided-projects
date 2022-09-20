---
title: Guided Project 3 WolfScheduler - Conflict
description: Guided Task - Create `Conflict` Interface
tags: [software engineering, software lifecycle, CS2, CSC216, GP3]
navigation: on
pagegroup: gp3
---

# Guided Task: Create `Conflict` Interface
{% include iconHeader.html type="task" %}
Checking for a schedule conflict is a behavior that is useful for `WolfScheduler` and other applications.  We will practice additive change by incorporating the checked conflict behavior as an interface.  For the moment, the `Conflict` interface will be specific to the `Activity` hierarchy (i.e., we will be using classes in the `Activity` hierarchy rather than a generic type).  You can update the `Conflict` interface to handle generic objects later.

{% capture callout_content %}
  * Create an interface
  * Create a custom exception class
{% endcapture %}
{% include callout.html icon="objective" content=callout_content type="learningOutcomes" title="Learning Outcomes" %}


## Create an Interface
Create a new Java interface called `Conflict` in the `edu.ncsu.csc216.wolf_scheduler.course` package of the `WolfScheduler` project.  To create an interface, do the following:

  * Right click on the `edu.ncsu.csc216.wolf_scheduler.course` package and select **New > Interface**.
  * Enter the name `Conflict` and check the option to generate comments.
  * Click **Finish** to create the interface.


{% include image.html file="images/CreateInterface.PNG" caption="Figure: Create an interface" %} 


## Add a Method
Add the method `checkConflict()` to the `Conflict` interface.  The method has a void return type and accepts an `Activity` object as a parameter.  The method must throw a `ConflictException`, which is a custom checked exception that you will define next.   

Since `checkConflict()` is abstract, its header must end in a semicolon rather than an opening curly brace.  However, since the method is part of an interface, it is automatically `public` and `abstract`, so you can leave out those key words.  The method header is:

```java
void checkConflict(Activity possibleConflictingActivity) throws ConflictException;
```
    
There are several design considerations to think about when deciding how best to set up the method for the `Conflict` interface.  The first involves identifying the best location to handle the check for conflict.  There are two choices: 1) handle in the `Activity` hierarchy by comparing the current instance to a parameter instance, and 2) handle in the list of `Activity`s.  By checking for conflict in the `Activity` hierarchy rather than in the list, you are following a design similar to the `equals()` and `hashCode()` methods from `Object` and similar to the [`Comparable` interface](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/java/lang/Comparable.html).  An alternative would be to handle in `WolfScheduler`; however that implementation would likely be clunky since there are two locations where you will need to check for conflict (`addCourse()` and `addEvent()`).  Since `Activity` will implement the `Conflict` interface, the idea of conflict is built into the `Activity` hierarchy and any other program that might use that hierarchy.

A second design consideration is how to report a conflict to the client.  There are two choices: 1) return a `boolean` specifying if there is conflict or not, and 2) throwing an exception.  The first choice would work, but the client could easily ignore the return type and end up with a conflict!  The second choice of throwing an exception is a stronger alternative.  However, it depends on the type of exception that you throw.  If you throw something like an `IllegalArgumentException`,  that can also be ignored or not handled.  `IllegalArgumentException` is an *unchecked exception*, and the compiler doesn't provide feedback about handling it.  It's the developer's responsibility to fully read the documentation to know to check for it to avoid a possible program crash (you did document all the methods that throw `IllegalArgumentExceptions`, right?).  A *checked exception* requires the the developer do something to handle the exception or the code won't even compile.  You'll be using a custom checked exception specifically for conflicts: `ConflictException`.  This means that clients of the `Conflict` interface MUST handle the exceptions in their code!

The design for the full `WolfScheduler` project, including the `Conflict` interface and `ConflictException` is below.

{% include image.html file="../wolf-scheduler/images/ws-GP3-design.png" caption="Figure: Full WolfScheduler Class Diagram" %} 

{% capture reminder-content %}
If you need help creating the `ConflictException` Java Class using Eclipse Quick Fix, see [Guided Task: Eclipse Quick Fix Tool - Quick Fix](../gp1/gp1-quick-fix.html#quick-fix).
{% endcapture %}
{% include mention.html content=reminder-content type="reminder" icon="ideTool" title="Reminder: Quick Fix for Class Creation" %}
## Create `ConflictException`
Use the Quick Fix tool to create a `ConflictException` in the `edu.ncsu.csc216.wolf_scheduler.course` package.  Since `ConflictException` is a checked exception, it should inherit from `Exception`.  You'll finish implementing `ConflictException` on the next page.

{% include image.html file="images/CreateException.PNG" caption="Figure: Create an exception" %} 




## Comment `Conflict`
Interfaces define behaviors that implementing classes must define.  That means the interface must be well commented so that others can use the interface for other classes.  Fully Javadoc the interface at both the interface and method levels.  Remember to use the `@throws` tag to describe when the `ConflictException` is thrown.  


{% capture reminder-content %} 
GitHub Resources:

  * [Staging Files](https://pages.github.ncsu.edu/engr-csc-software-development/practices-tools/git/git-staging)
  * [Committing Files](https://pages.github.ncsu.edu/engr-csc-software-development/practices-tools/git/git-commit)
  * [Pushing Files](https://pages.github.ncsu.edu/engr-csc-software-development/practices-tools/git/git-push)
{% endcapture %} {% include mention.html content=reminder-content type="reminder" title="Reference: Staging and Pushing to GitHub"%} 
## Check Your Progress
{% include iconHeader.html type="glance" %}

Complete the following tasks before pushing your work to GitHub.

  - [ ] Make sure that all fields, methods, and constructors are commented.
  - [ ] Resolve all static analysis notifications.
  - [ ] Fix test failures.
  - [ ] Commit and push your code changes with a meaningful commit message.  Label your commit with "[Implementation]" for future you!

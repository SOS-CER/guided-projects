---
title: Guided Project 2 WolfScheduler - Activity and Event
tags: [software engineering, software lifecycle, CS2, CSC216, GP2]
description: Guided Task -  Design a Hierarchy
navigation: on
pagegroup: gp2
---

# Guided Task: Design a Hierarchy
{% include iconHeader.html type="task" %}

The focus for GP2 is to add `Event`s to the `WolfScheduler` program.  That way users can put items like meals, club meetings, exercise, and other non-course activities on their schedules.  For Guided Project 2, you do not need to worry about checking for conflicting activities.

{% capture callout_content %}
  * Identify design decisions and trade-offs
{% endcapture %}
{% include callout.html content=callout_content type="learningOutcomes" title="Learning Outcomes" %}
  
{% capture callout_content %}
There are two main relationships between classes: composition and inheritance.  Composition is a *has-a* relationship where one object has an instance (or collection) of another object.  Inheritance is an *is-a* relationship where one class is an extension or specialization of another class.  When two objects have a common set of fields with some specializations, those objects are candidates for an inheritance hierarchy.  You can create a parent class that contains the common fields and each child class can then specialize.
{% endcapture %}
{% include callout.html content=callout_content icon="objective" icon="dtTool" type="bestPractices" title="Best Practices: Inheritance" %}


## Identifying Common Elements
[Use Case 6](../wolf-scheduler/ws-requirements#uc6) and [Use Case 7](../wolf-scheduler/ws-requirements#uc7) describes a new type of item that can go on a student's schedule: `Event`s.  Both `Course` and `Event` have a common set of attributes: `title`, `meetingDays`, `startTime`, and `endTime`.  These common elements can be stored in a parent class, `Activity`, and `Course` and `Event` can specialize as appropriate for their classes.

By providing a common parent class, you can maintain the user's schedule as an `ArrayList` of `Activity` objects so the schedule can hold both `Course`s and `Event`s!


{% include image.html file="../wolf-scheduler/images/ws-GP2-activity-hierarchy.png" caption="Figure: Activity Inheritance Hierarchy" %}

**UML diagram notations**
UML uses standard conventions for display of data, methods, and relationships. Many are illustrated in the UML diagram above. Here are some things you should note:

  * `-` OR a red square (empty or solid) in front of a class member means private. 
  * `+` OR a green circle (empty or solid) in front of a class member means public.
  * Static members (data or methods) are underlined.  They also have a small S notation on the left icon.
  * Final members (data or methods) have a small F notation on the left icon and the value is typically provided.
  * Methods embellished with C are constructors.
  * Methods that are declared but not defined (abstract methods or those declared in interfaces) are in italics. 
  * The names of abstract classes are in italics and there is a small A notation on the class icon.
  * Dotted arrows with triangular heads point to interfaces from the classes that implement them.
  * Solid arrows with triangular heads go from concrete classes to their parents.
  * Solid arrows with simple heads indicate **has-a** relationships (composition). The containing class is at the tail of the arrow and the class that is contained is at the head. The arrow is decorated with the name and access of the member in the containing class. The arrow is also decorated with the "multiplicity" of the relationship, where 0..1 means there is 1 instance of the member in the containing class and 0..* means there are many (usually indicating a collection such as an array or `ArrayList`).
  * A circle containing an `X` or cross that sits on the border of a class that contains an inner or nested class, with a line connecting it to the inner class. 


You can read this UML class diagram and see the names and types of all  the classes and class members that you must create. The method signatures in your program **must** match the  above diagram and provided interfaces **exactly** for the teaching staff tests to run.




## Design Changes and Refactoring
In CSC 216, you'll have the opportunity to explore creating designs. But for programming projects you will be provided with a teaching staff design that you're expected to implement.  However, in the Guided Projects, you can model design changes and decisions that are made while implementing the `WolfScheduler` system.  These changes are common in practice because of additional understanding and knowledge about a solution as it is implemented.   

As you consider design changes, you want to make those changes in slow controlled steps and ensure that you don't break any old functionality before adding new functionality to the system.  You can use *refactoring* to support making small structural changes to the program that provides a better design and allows for extension and modification of a program while not changing the functionality.  You can then ensure that your changes do not alter the functionality by running your unit tests!

In the next section you will walk through using one of Eclipse's built in refactoring tools that will support the extraction of a super class, `Activity`, as a first step to the inheritance hierarchy shown in the Figure above.


---
title: WolfScheduler
description: WolfScheduler Design
tags: [software engineering, software lifecycle, CS2, CSC216]
navigation: on
pagegroup: wolf-scheduler
---

# WolfScheduler Design
{% include iconHeader.html type="design" %}

A software [design](../se-overview/design) describes the modules, classes, data, and behaviors of a software system at a high-level. A design must provide a solution that would allow for the implementation to meet the requirements.  

The Wolf Scheduler project follows the Model-View-Controller (MVC) design pattern. The view/controller classes are in the `edu.ncsu.csc216.wolf_scheduler.ui` package. The remaining packages represent the model or underlying business logic of the application. By separating the view/controller from the underlying model, we can isolate the business logic of the application (managing a schedule of events and courses) from the presentation (a GUI or command line interface). We could easily add another user interface to the system without modifying the business logic of the program.

The goal of the design is to isolate the major parts of the system so that each class may specialize in behaviors specific to it's state. Where possible, other classes will delegate to the specializing classes (e.g., the Scheduler class delegates to Schedule for adding/removing an event/course).

As we progress through the three Guided Projects, the design of the `WolfSchedule` program will evolve.  The Guided Projects will walk you through each major design evolution and discuss the decisions that were made at each step.

A detailed listing of the classes and their associated methods (including parameter names) are provided in the [implementation](ws-implementation) section.


## UML Diagram Notation
UML uses standard conventions for display of data, methods, and relationships. Many are illustrated in the UML diagram above. Here are some things you should note:

  * `-` in front of a class member means private. 
  * `+` in front of a class member means public.
  * Static members (data or methods) are underlined.
  * Methods that are declared but not defined (abstract methods or those declared in interfaces) are in italics. 
  * The names of abstract classes are in italics.
  * Dotted arrows with triangular heads point to interfaces from the classes that implement them.
  * Solid arrows with triangular heads go from concrete classes to their parents.
  * Solid arrows with simple heads indicate **has-a** relationships (composition). The containing class is at the tail of the arrow and the class that is contained is at the head. The arrow is decorated with the name and access of the member in the containing class. The arrow is also decorated with the "multiplicity" of the relationship, where 0..1 means there is 1 instance of the member in the containing class and 0..* means there are many (usually indicating a collection such as an array or `ArrayList`).
  * A circle containing an `X` or cross sits on a the border of a class that contains an inner or nested class, with a line connecting it to the inner class. 

Our UML diagram has some additional graphic notation:

  * A  square (empty or solid) in front of a name means private. 
  * A green circle in front of a name means public. 
  * SF in front of a name means static, final. 
  * Methods embellished with C are constructors. 

You can read this UML class diagram and see the names and types of all  the classes and class members that you must create. The method signatures in your program **must** match the  above diagram and provided interfaces **exactly** for the teaching staff tests to run.



## Guided Project 1 Design
For Guided Project 1, we are focusing on the functionality around scheduling courses, which includs the idea of reading in a course catalog, adding/removing courses to/from a schedule, and viewing/exporting the finalized schedule.  The implementation of GP1 covers paths through all of the [use cases](ws-requirements), but leaves out functionality related to events and handling conflicting classes and events.

For GP1, the `WolfScheduler` project is divided into four packages:

  * `edu.ncsu.csc216.wolf_scheduler.course`: Holds the `Course` class.
  * `edu.ncsu.csc216.wolf_scheduler.io`: Holds classes that do file I/O.
  * `edu.ncsu.csc216.wolf_scheduler.scheduler`: Holds the `Scheduler` class that maintains the catalog and selected schedule.
  * `edu.ncsu.csc216.wolf_scheduler.ui`: Holds the user interface.

{% include image.html file="images/ws-GP1-design.png" caption="Figure: Guided Project 1 Class Diagram" %} 

## Guided Project 2 Design
For Guided Project 2, we are focusing on the functionality around events.  The implementation of GP2 covers paths through all of the [use cases](ws-requirements#guided-project-2-requirements), but leaves out functionality related handling conflicting classes and events.

For GP2, the `WolfScheduler` project is divided into four packages:

  * `edu.ncsu.csc216.wolf_scheduler.course`: Holds the `Activity` hierarchy.
  * `edu.ncsu.csc216.wolf_scheduler.io`: Holds classes that do file I/O.
  * `edu.ncsu.csc216.wolf_scheduler.scheduler`: Holds the `Scheduler` class that maintains the catalog and selected schedule.
  * `edu.ncsu.csc216.wolf_scheduler.ui`: Holds the user interface.


{% include image.html file="images/ws-GP2-design.png" caption="Figure: Guided Project 2 Class Diagram" %} 

## Guided Project 3 Design
For Guided Project 3, we are focusing on the functionality around events.  The implementation of GP3 covers paths through all of the [use cases](ws-requirements#guided-project-3-requirements).

For GP3, the `WolfScheduler` project is divided into four packages:

  * `edu.ncsu.csc216.wolf_scheduler.course`: Holds the `Activity` hierarchy.
  * `edu.ncsu.csc216.wolf_scheduler.io`: Holds classes that do file I/O.
  * `edu.ncsu.csc216.wolf_scheduler.scheduler`: Holds the `Scheduler` class that maintains the catalog and selected schedule.
  * `edu.ncsu.csc216.wolf_scheduler.ui`: Holds the user interface.


{% include image.html file="images/ws-GP3-design.png" caption="Figure: Guided Project 3 Class Diagram" %} 

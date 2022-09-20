---
title: Guided Project 1 - Software Development Practices and Tools
tags: [software engineering, software lifecycle, CS2, CSC216, GP1]
description: Guided Task - A Very Brief Introduction to Unit Testing
navigation: on
pagegroup: gp1
---

# Guided Task: A Very Brief Introduction to Unit Testing
{% include iconHeader.html type="task,unitTest" %}

Larger systems with many interacting classes only have one main method. If you can't start a program from a main method, you are unable to run black box tests on the program. 

You could wait until all of the classes are implemented to start testing, but that is very hard debug - and there are always bugs! Instead, you should test as you go along to ensure that your program's smaller units (classes and methods) work the way they are supposed to. For the `WolfScheduler` project, the teaching staff are providing a suite of JUnit tests that you can run to ensure that your implementation meets the specified [`WolfScheduler` requirements and design](../wolf-scheduler/).

{% capture callout_content %}
  * Create a `test/` source folder
  * Create a package in the `test/` folder
  * Create a class for testing
  * Run JUnit tests
{% endcapture %}
{% include callout.html content=callout_content icon="objective" type="learningOutcomes" title="Learning Outcomes" %}

{% capture callout_content %}
During the [test phase](https://pages.github.ncsu.edu/engr-csc-software-development/software-lifecycle) of [development](https://pages.github.ncsu.edu/engr-csc-software-development/software-lifecycle), you execute the program against a variety of inputs to evaluate if the program generates the correct or expected output.  You can determine the *expected output* by reading the requirements as well as the design documentation and APIs that define what the smallest program units (methods) should do.

*Unit testing* focuses on testing the smallest units of a program: methods and classes.  The premise is that by ensuring the smallest portions of the programs work correctly, you  can have increased confidence that the whole program will work correctly.

When you unit test for CSC 216/217, you are actually doing a combination of unit testing and integration testing.  *Integration testing* is when you test things in combination.  You will test methods in combination (e.g., adding something to a list and then removing it) and you will test methods that call other methods (e.g., a constructor calls a setter method).  However, your focus is on the very local functionality of that method or combinations of methods within a class and not the program as a whole.
{% endcapture %}
{% include callout.html content=callout_content icon="unitTest,ttTool" type="bestPractices" title="Best Practice: Unit Testing" %}

{% capture callout_content %}
JUnit is an automated unit testing tool for Java.  JUnit is a set of libraries that include classes, like `TestCase`, and methods, like `assertEquals()`, that help with unit testing Java code.  

For Guided Project 1, all unit tests will be provided so you will be able to assess the quality of your work as you progress through the tasks.  Later, you will be expected to write your own tests and your implementation will be exercised against a hidden suite of teaching staff tests that will assess how well you meet the teaching staff design on the project!
{% endcapture %}
{% include callout.html content=callout_content icon="ttTool" type="tools" title="Tool: JUnit" %}


{% capture reminder-content %} 
References

  * [Guided Task: Your First Eclipse Project - Create a Package](gp1-eclipse-intro#create-a-package)
  * [Guided Task: Your First Eclipse Project - Create a Class](gp1-eclipse-intro#create-a-class)
{% endcapture %} {% include mention.html content=reminder-content type="reminder" title="Reference: Creating Packages and Classes in Eclipse"%}  
## Setup `WolfScheduler` for Testing
You'll start by setting up the `WolfScheduler` project for testing so you can test `Course`.

  1. Create a new source folder, called `test`,  which will contain all JUnit test files. Right click on the project and select **New > Source Folder**.  Enter `test` in the *Folder name* text field.	
  
{% include image.html file="images/TestFolder.PNG" caption="Figure: New Source Folder for Test Files" %} 
  
  {:start="2"}
  2. Create a new package in the test source folder named `edu.ncsu.csc216.wolf_scheduler.course`. Notice that the package is the same as `Course`'s package.
  
  {:start="3"}
  3. Create a new class in the `test` source folder `edu.ncsu.csc216.wolf_scheduler.course` package named `CourseTest`. Notice you use the same class name (`Course`) and append the word `Test` to the end of the class name.
  
{% include image.html file="images/CourseTest.PNG" caption="Figure: Create `CourseTest` Class" %} 

  
  {:start="4"}
  4. [Copy the code from `CourseTest.java`](files/CourseTest.java) into your `CourseTest` class. The class will not compile! That is because you are missing a library.
  
  {:start="5"}
  5. You need to add the JUnit library to your project. Right click on the `WolfScheduler` project and select **Properties**. In the left menu, select **Java Build Path**. In the right portion of the screen, select the **Libraries** tab. Select *Classpath* and then click **Add Library...**. Select **JUnit** and click **Next**. Select **JUnit 5** in the drop down and click **Finish** followed by **Apply and Close**. When you are done, the JUnit 5 library will be added to the project's build path and the compiler errors should be resolved.
  
{% include image.html file="images/JUnitLibrary.PNG" caption="Figure: Add the JUnit 5 Library" %} 
    

 
## Run JUnit Tests
Run the provided JUnit tests by right clicking on the `test` source folder and selecting **Run As > JUnit Test**.  By running the command on the `test` source folder, you will run all the test classes in the folder.  You can also run all the tests in a package or a single test class by right clicking on that artifact.

{% include image.html file="images/RunTests.PNG" caption="Figure: Run JUnit Tests" %} 

After running the tests, several will be passing (`testCourseStringStringStringIntStringString()`, `testEqualsObject()`, `testHashCode()`, `toString()`), but several will be failing!  That's Ok!  You'll fix that soon!

{% include image.html file="images/TestResults1.PNG" caption="Figure: JUnit Results" %} 

{% capture reminder-content %} 
GitHub Resources:

  * [Staging Files](https://pages.github.ncsu.edu/engr-csc-software-development/practices-tools/git/git-staging)
  * [Committing Files](https://pages.github.ncsu.edu/engr-csc-software-development/practices-tools/git/git-commit)
  * [Pushing Files](https://pages.github.ncsu.edu/engr-csc-software-development/practices-tools/git/git-push)
{% endcapture %} {% include mention.html content=reminder-content type="reminder" title="Reference: Staging and Pushing to GitHub"%} 
## Check Your Progress
{% include iconHeader.html type="glance" %}
You've added your `CourseTest` class.  Before moving on to the next portion of the Guided Project, complete the following tasks:

  - [ ] Add `CourseTest` to the index.
  - [ ] Commit and push the `CourseTest` class and any `Course` changes to GitHub.  Remember to use a meaningful commit message describing how you have changed the code.  For example, "[Test] Added CourseTest".
  
---
title: Guided Project 2 WolfScheduler - Activity and Event
tags: [software engineering, software lifecycle, CS2, CSC216, GP2]
description: Guided Task - Run the Debugger
navigation: on
pagegroup: gp2
---

# Guided Task: Run the Debugger
{% include iconHeader.html type="task" %}

You have two failing test cases!  Yay!  This means that we have a concrete example of where our code doesn't work.  And we can use the failing test case to debug our code, find the fault, and then fix it!

<!--The test is considering valid paths of the `setMeetingDaysAndTime()` functionality for an `Event`.  As defined in [[UC6]](../wolf-scheduler/ws-requirements#uc6), an `Event`'s `meetingDays` are valid for Sunday through Saturday.  You'll represent Sunday with a `U` and Saturday with an `S`. The failing test had a `meetingDays` string of "UMTWF", which is -->

We'll start with the failure in `testSetMeetingDaysAndTimesInvalid()`.  The requirements [[UC6]](../wolf-scheduler/ws-requirements#uc6) tell us that the student would enter the days of the week (Sunday through Saturday).  That means the `meetingDays` value of "A" is not valid for `Event`.  The test is failing because you CAN set the `meetingDays` to "A".  It's time to use the debugger to find where you need to fix your code.

The debugger is a tool that steps through your program a statement at a time.  You can follow the flow of control into a called method.  Additionally, the debugger provides a view into the values of variables as the code is executing.  It's a very helpful tool for finding and fixing faults in your code.

{% capture callout_content %}
  * Use the debugger to fix a failing test.
{% endcapture %}
{% include callout.html content=callout_content icon="objective" type="learningOutcomes" title="Learning Outcomes" %}


## Set a Breakpoint
When you debug code, you need to stop the execution so you can then step through the program.  A *breakpoint* pauses the execution of the program.  Then you can view information about the program's state.

When a test fails, you should put a breakpoint at the line of the code under test that you think is causing the failure.  You can determine this by selecting the failing test and investigating the failure trace as shown for the `testSetMeetingDaysAndTimesInvalid()` test failure below.  From this failure, we can see that for the input of "A" we expected an `IllegalArgumentException`, but the exception was not thrown.  By clicking the first line labeled "at", we can go the specific line of code that caused the test failure.

{% include image.html file="images/JUnitFailure.PNG" caption="Figure: Test Failure Trace" %}

From this failure, we can see that for the input of "A" we expected an `IllegalArgumentException`, but the exception was not thrown.  By clicking the first line labeled "at", we can go the specific line of code that caused the test failure.  Our failure is at line 111 (this may be slightly different in your local environment, which is probably ok unless you edited your tests files in a more significant way than adding blank lines...)

{% include image.html file="images/JUnitFailure2.PNG" caption="Figure: Failing Test" %}

From there, we can determine the best place to put a break point.  In this example, we are calling a setter as part of the test case.  Since setters change object state, we should start with the setter closest to the failure; that likely lead to the failure.  Put a breakpoint at the line of the failing test by double clicking in the blue bar to the left of the line numbers.



{% include image.html file="images/Breakpoint.PNG" caption="Figure: Placing a Breakpoint" %}


## Run the Program through the Debugger
With debugging, you select the **Debug** option rather than the **Run** option.  You can run in debug mode by right clicking on the `test/` folder, a package, or a specific class, and selecting **Debug As > JUnit Test**.  There is also a debug button on the top level tool bar.  Select **Debug** to run the last run configuration in debug mode or select the arrow to create a new run configuration to debug. 

However, when debugging, I like to focus on a _single failure at a time_!  This helps narrow my debugging session and removes having to hit a breakpoint multiple times just to get to the failure that I'm interested in debugging.  That means I select the **specific** test failure I want to debug in the JUnit view.  And for parameterized tests, you can select the specific row that you're interested in debugging.  To debug the test failure in `testSetMeetingDaysAndTimesInvalid()`, right click on test 11 under the `testSetMeetingDaysAndTimesInvalid()` label and select **Debug**.

{% include image.html file="images/JUnitFailureStartDebug.PNG" caption="Figure: Test Failure Trace" %}


You may get a message about switching perspectives - this is okay. If you check the "Remember my decision," you will not see this dialog again.

The **Debug Perspective** provides several views to help you with the task of debugging your code.


{% include image.html file="images/DebugPerspective.PNG" caption="Figure: Debug Perspective" %}

  * **Debug** shows the live stack trace of methods. The figure illustrates the stack trace in execution of `EventTest.testSetMeetingDaysAndTimeInvalid()`. If other programs were running at the same time, you would see them here. 
  * **Stepping Buttons** are in the top tool bar.  The provide the ability to restart execution, stop execution, and step through the code.  We'll cover this in more detail shortly.
  * **Variables** shows the values of all the variables that have been declared. If your breakpoint stops before a variable's declaration, that variable will not appear in the list.
  * **Breakpoints** shows the locations of all your breakpoints in the code (you can have many breakpoints).
  * **EventTest.java** shows where you are in the code at the time of the breakpoint.  The arrow and highlighted text let you know where you are in the code.


## Debugger Controls
The main Eclipse toolbar provides buttons for working with the debugger.  There are 7 buttons in the toolbar:

  * **Resume:** resumes the current execution from the given program point
  * **Suspend:** pauses an execution
  * **Stop:** stops the debugging execution.  Always stop your debugging executions or you'll use up a lot of system memory!
  * **Disconnect:** disconnects the debugger
  * **Step Into:** steps into a method call
  * **Step Over:** steps over a method call without going into the details of the method
  * **Step Return:** finishes execution of the current method and returns to the caller
  

{% include image.html file="images/Toolbar.PNG" caption="Figure: Debugger Toolbar" %}

## Step Through a Program
You can use the debugger to determine what is happening in a program and find an underlying bug.  By exploring the program, you are likely to have a better understanding of the flow of control and identify where an implementation doesn't meet the requirements.

The line of code we're investigating is complex.  Let's walk through it first before we start debugging:

```java
Exception exception = assertThrows(IllegalArgumentException.class,
				() -> event.setMeetingDaysAndTime(meetingString, startTime, endTime));
```

This line is asserting that an `IllegalArgumentException` (our expected result) will be thrown when we call `event.setMeetingDaysAndTime(meetingString, startTime, endTime)`, which is the method call that will lead to our actual result.  For this specific failure, the `meetingString` is "A", `startTime` is 0, and `endTime` is 0, which we can see in the **Variables view**.  If the `IllegalArgumentException` is thrown, it will be assigned to the `exception` reference and then we can check that the correct message was provided to describe the reason for throwing the exception.

Typically at this point, we would **step into** the method call at the program statement.  However, lambda expressions will take you through a lot of the Java API.  Since we know what method we want to go to, switch to `Activity.setMeetingDaysAndTime()` and add a breakpoint at the first statement.  Then you can click the **Resume** button to until you reach the first line of `setMeetingDaysAndTime()` bypassing all the Java API calls.

{% include image.html file="images/Breakpoint2.PNG" caption="Figure: Placing a Breakpoint" %}

<!--
We are going to **step into** the call to the `event`'s `setMeetingDaysAndTime()` method with the parameters "A", 0, and 0.

Click the **Step Into** button to start stepping into the code.  You'll need to click it again to finish processing the second line of the program statement.  After that, you may be transferred to a class in the Java API (e.g., `DirectMethodHandle`).  Click **Step Return** until you reac
transfer the flow of control to the first line of `Activity.setMeetingDaysAndTime()`.  
-->

Now, we can explore the method by stepping over the program statement.  Continue stepping through the method with the **Step Over** button.  You reach the end of the method for the assignment to the `meetingDays` field without throwing an exception!

At this point you can either **Resume** or **Stop** the test run.  You know there's a problem in `Activity.setMeetingDaysAndTime()`.


## Debug the Program
The implementation of `setMeetingDaysAndTime()` in `Activity` is the implementation extracted from `Course`.  There isn't an implementation of `setMeetingDaysAndTime()` that supports `Event` specifics!  You need to make a decision about how to best handle the differences between `Course` and `Event` for `setMeetingDaysAndTime()`.  A common implementation in `Activity` will not work.  

The solution is to have `Course` and `Event` override the `setMeetingDaysAndTime()` method.  `Course` and `Event` will handle their own checks on `meetingDays` appropriate for their requirements.  Then they will pass `meetingDays`, `startTime`, and `endTime` to `Activity.setMeetingDaysAndTime()` for the common time checks and assignment of the fields.  

  * Keep the common checks for `meetingString` (e.g., not null or empty) and times (e.g., valid military time) in `Activity`.
  * Override `setMeetingDaysAndTime()` in `Course` and ensure that [[UC1]](../wolf-scheduler/ws-requirements#uc1) is satisfied.  Then let `Activity.setMeetingDaysAndTime()` handle the common checks and final assignment.
  * Override `setMeetingDaysAndTime()` in `Event` and ensure that [[UC6]](../wolf-scheduler/ws-requirements#gp2-uc2-s4) is satisfied.  Note that for the `meetingDays`, string "U" represents Sunday and "S" represents Saturday.  The other days of week characters are the same as `Course`.  Any other character, including "A", is invalid. Then let `Activity.setMeetingDaysAndTime()` handle the common checks and final assignment.
  
  
Overriding `Activity.setMeetingDaysAndTime()` in `Event` should resolve both test failures.  `Course` tests should continue to pass.
  


## Run Tests
Run your tests!  If any are still failing, use the debugger to help you find the problem.

## Comment `Event` and Fix Static Analysis Notifications
Complete the following tasks:

  * Update all your Javadoc for `Course` and `Event`. Overridden methods much also be commented to describe the specifics in the overridden implementation.
  * Resolve all static analysis notifications.


## Additional Resources on the Debugger
This was a very brief overview of using the debugger.  If you would like more information, please see the [Eclipse Debugger Tutorial](https://pages.github.ncsu.edu/engr-csc216-staff/CSC216-SE-Materials/eclipse-debugger/eclipse-debugger.html).


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
  - [ ] Commit and push your code changes with a meaningful commit message.  Label your commit with "[Debug]" for future you!
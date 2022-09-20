---
title: Guided Project 2 WolfScheduler - Activity and Event
tags: [software engineering, software lifecycle, CS2, CSC216, GP2]
description: Guided Task - Create `ActivityRecordIO`
navigation: on
pagegroup: gp2
---

# Guided Task: Create `ActivityRecordIO`
{% include iconHeader.html type="task" %}

`CourseRecordIO` handles reading course records from a file to create a course catalog and writing `Course`s to a file.  Now that you have `Events` that should also be written to an output file (as per [[UC10]](../wolf-scheduler/ws-requirements#uc10), you need to create a new IO class to handle writing `Activity` objects.

{% capture callout_content %}
  * Refactor file I/O functionality
{% endcapture %}
{% include callout.html content=callout_content icon="objective" type="learningOutcomes" title="Learning Outcomes" %}

{% capture reminder_content %}
[Guided Task: Your First Eclipse Project - Create a Class](../gp1/gp1-eclipse-intro#create-a-class).
{% endcapture %}
{% include mention.html content=reminder_content icon="ideTool" type="reminder" title="Reminder: Eclipse Java Class Creation" %}
## Create `ActivityRecordIO` Class
Create a new Java class called `ActivityRecordIO` in the `edu.ncsu.csc216.wolf_scheduler.io` package of the `WolfScheduler` project.  Do not create the constructor or any methods in `ActivityRecordIO`.


## Move `writeCourseRecords()` to `ActivityRecordIO`
Complete the following steps to move `writeCourseRecords()` from `CourseRecordIO` to `ActivityRecordIO`.

  * Open `CourseRecordIO` in the editor.
  * Select the `writeCourseRecords` method name in the editor. You only want to select the method name.
  
   
{% include image.html file="images/MoveMethod.PNG" caption="Figure: Selecting a Method for Moving" %}
    
  * Right click on the `writeCourseRecords` method name and select **Refactor > Move**.
  * **Browse** for `ActivityRecordIO`.  Uncheck the options to keep original member as delegate to moved member.
  
    
{% include image.html file="images/MoveMethodWizard.PNG" caption="Figure: Moving a Method" %}
    
  * The method is now in `ActivityRecordIO`.  `WolfScheduler` and `CourseRecordIOTest` have been udpated with the change.  
  * Refactor the method name in `ActivityRecordIO`.  Select the method name, right click on the method and select **Refactor > Rename**.  Enter `writeActivityRecords` and click **Enter**.
  * Update the generic parameter of the `ArrayList` to be `Activity` instead of `Course`.
  * Update the local variables in the for loop.  You can use the keyboard short cut of **Alt + Shift + R** to do the rename refactoring.
     * Change `c` to `a`
     * Change `courses` to `activities`	 
  * Delete the import for `Course` since it is no longer needed.
  
At this point, there will be a compilation error in `WolfScheduler.exportSchedule()`. That's ok.  We'll fix it later.

The compilation error in `CourseRecordIOTest` we'll fix after you check that `ActivityRecordIO` is complete.
  
After you are done, `ActivityRecordIO` should look like the following:

```java
package edu.ncsu.csc216.wolf_scheduler.io;

import java.io.File;
import java.io.IOException;
import java.io.PrintStream;
import java.util.ArrayList;

import edu.ncsu.csc216.wolf_scheduler.course.Activity;

/**
 * Writes activities to file.
 * @author Sarah Heckman
 */
public class ActivityRecordIO {

    /**
     * Writes the given list of Courses to 
     * @param fileName file to save to
     * @param activities list of course to save
     * @throws IOException if the file cannot be written
     */
    public static void writeActivityRecords(String fileName, ArrayList<Activity> activities) throws IOException {
    	PrintStream fileWriter = new PrintStream(new File(fileName));
    	
    	for (Activity a : activities) {
    		fileWriter.println(a.toString());
    	}
    	
    	fileWriter.close();
    }

}
```


## Update `CourseRecordIOTest`
There is a call to `ActivityRecordIO` in `CourseRecordIOTest` that is not compiling.  This is because we changed the parameter type from an `ArrayList` of `Course`s to an `ArrayList` of `Activity`s.  We'll need to update the `ArrayList` generic type in our test. 

Update the first line of the test method to `ArrayList<Activity> activities = new ArrayList<Activity>();`.  You'll need to import `Activity` for the test to compile.  When changing the variable name, rename with the refactoring tool.

## Run Tests
Run your tests! You'll get a warning because `WolfScheduler` is not compiling, but you can run anyway to make sure that `CourseRecordIOTest` passes. If any are still failing in the `course` or `io` packages, use the debugger to help you find the problem.  For now, the `WolfScheduler` tests may fail due to compilation errors and that's ok.

However, your suite of tests is not sufficient to evaluate if events are correctly written to file.  Create a class `ActivityRecordIOTest` the `edu.ncsu.csc216.wolf_scheduler.io` package of the `test/` folder in the `WolfScheduler` project.  Copy in the [provided `ActivityRecordIOTest` code](files/ActivityRecordIOTest.java) into `ActivityRecordIOTest`.  Create a new text file in the `test-file/` directory called `expected_activity_records.txt` and copy [the provided `expected_activity_records.txt`](files/expected_activity_records.txt). Run the tests.  Ensure they all pass!

## Comment `ActivityRecordIO` and Fix Static Analysis Notifications
Complete the following tasks:

  * Update all your Javadoc for `ActivityRecordIO`. 
  * Resolve all static analysis notifications.


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

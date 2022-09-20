---
title: Guided Project 1 - Software Development Practices and Tools
tags: [software engineering, software lifecycle, CS2, CSC216, GP1]
description: Guided Task - Run System Tests
navigation: on
pagegroup: gp1
---
 
# Guided Task: Run System Tests
{% include iconHeader.html type="systemTest" %}
Now that you're completed the model classes with passing unit tests and added the GUI (view/controller) to the `WolfScheduler` program, you can run your [system level tests.](https://pages.github.ncsu.edu/engr-csc-software-development/software-lifecycle/)  These tests ensure that the entire system is working end to end.  When we run system tests, we consider the system as a whole where the internal details are not know.  The system is like a closed box, where we put input in and get actual results out.  If the actual results of execution are different than what was expected, the test fails and we can start debugging.  The expected results of execution are defined in the requirements!

{% capture callout_content %}
  * Run a Java application in Eclipse
  * Run system tests
  * Record the results of system test execution
{% endcapture %}
{% include callout.html content=callout_content icon="objective" type="learningOutcomes" title="Learning Outcomes" %}

{% capture reminder-content %} 
[Guided Task: Your First Eclipse Project - Running a Java Program](gp1-eclipse-intro#running-a-java-program)
{% endcapture %}
{% include mention.html content=reminder-content type="reminder" title="Reminder: Running Programs in Eclipse" %} 
## Running `WolfScheduler`
The `main()` method for the WolfScheduler project is in the GUI class.  To run the WolfScheduler project, right click on `WolfSchedulerGUI` and select **Run As > Java Application**.  The program will start and a `FileChooser` dialog box titled "Load Course Catalog" will open.  Select `test-files/course-records.txt` and click **Select**.

{% include image.html file="images/LoadCourseCatalogDialog.PNG" caption="Figure: Load Course Catalog" %} 

The main GUI will load.  There are four sections:

  * Course Catalog: The catalog contains 13 classes in the same order as the file. (Note: the file has 14 lines, one line (line 4) is invalid.)  The name, section, and title for each are displayed.
  * Actions: The actions section has a set of buttons and the Schedule Title text field.  
  * My Schedule: Lists the courses that have been added to the schedule.
  * Course Details: Displays the details of any course selected in the Course Catalog table.
  
{% include image.html file="images/WolfSchedulerGUI.PNG" caption="Figure: WolfSchedulerGUI"  %} 

 
## Running System Tests
The teaching staff have created 13 system tests for your to run.  Each test should be independent, but some may have preconditions that rely on earlier tests.  For example, the test to add a course to the schedule relies on the test to load a valid course catalog.  To save a little time, the tests are ordered so that you can go through them all without closing the GUI and starting over for each test, starting with test 2.  However, if you run into issues, you should close the GUI and start over on the next test (which is what the teaching staff will do during grading).

The [System Test Plan is stored on Google Drive](https://docs.google.com/document/d/1IG-HfEuWSVWyuVGaws4ehAgueBWkXwdj3OWOlYrPCVs/edit?usp=sharing).  You must be logged in to Google with your NC State id to access the file!

Download the System Test Plan document as a Word document by select **File > Download > Microsoft Word** in Google Drive.  Create a new folder in your `WolfScheduler` project called `project_docs` by right clicking on `WolfScheduler` and selecting **New > Folder**.   Save your system test plan as a Word document (`*.doc` or `*.docx`) in the `project_docs` folder.  As you run each test, report the results of execution in the system test plan in the actual results column.  DO NOT record, "Passed", "Failed", or copy the expected results.  Instead, describe the results in your own words.  

Make sure all your system tests pass!  However, if you run out of time and are unable to fix all the bugs in your project, report the *actual results* of execution - EVEN IF THEY ARE FAILING! You'll earn some points on the system test portion of the [grading rubric](../wolf-scheduler/ws-rubric) for reporting actual, failing results.

 
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
  - [ ] Commit and push your code changes with a meaningful commit message.  Label your commit with "[Test]" for future you!
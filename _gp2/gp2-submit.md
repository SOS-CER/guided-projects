---
title: Guided Project 2 WolfScheduler - Activity and Event
tags: [software engineering, software lifecycle, CS2, CSC216, GP2]
description: Independent Task - Submit Project
navigation: on
pagegroup: gp2
---

# Independent Task: Submit Project
{% include iconHeader.html type="task" %}

There are a few tasks that you must complete to wrap up Guided Project 2 for grading.

{% capture callout_content %}
  * Run static analysis tools and fix notifications
{% endcapture %}
{% include callout.html content=callout_content icon="objective" type="learningOutcomes" title="Learning Outcomes" %}

<!--
{% capture reminder_content %}
[Guided Task: Run System Tests](../gp1/gp1-bbtp).
{% endcapture %}
{% include mention.html content=reminder_content icon="ideTool" type="reminder" title="Reminder: Running Tests in Eclipse" %}
## Run System Tests
{% include iconHeader.html type="systemTest" %}
Run `WolfSchedulerGUI` and ensure that you pass the extended suite of system tests for the `WolfScheduler` project.

The [Black Box Test Plan is stored on Google Drive](https://docs.google.com/document/d/1bqESm2No4IaTP7mC6i1Hd22fSYWjknjJA_K4_XnFzEI/edit?usp=sharing).  As part of running your tests, you must report the actual results of execution.  Download the document as a Word document by select **File > Download > Microsoft Word** in Google Drive.  Create a new folder in your `WolfScheduler` project called `project_docs` by right clicking on `WolfScheduler` and selecting **New > Folder**.   Save your black box test plan as a Word document (`*.doc` or `*.docx`) in the `project_docs` folder.  As you run each test, report the results of execution in the black box test plan in the actual results column.  DO NOT record, "Passed" or "Failed."  Instead, describe the results, similar to the provided Expected Results.

Make sure all your black box tests pass!  However, if you run out of time, report the actual results of execution - EVEN IF THEY ARE FAILING! You'll earn some points on the system test portion of the [grading rubric](#grading-rubric) for reporting actual, failing results.
-->

{% capture reminder_callout %}
[Guided Task: Run Static Analysis Tools](../gp1/gp1-static-analysis).
{% endcapture %}
{% include mention.html content=reminder_callout icon="saTool" type="reminder" title="Reminder: Running Static Analysis Tools" %}
## Run Static Analysis Tools
{% include iconHeader.html type="saTool" %}

Run SpotBugs, PMD, and CheckStyle on your code (if you haven't already) and remove any notifications.  



{% capture reminder_callout %}
[Guided Task: Generate Javadoc](../gp1/gp1-javadoc).
{% endcapture %}
{% include mention.html content=reminder_callout icon="dtTool" type="reminder" title="Reminder: Generating Javadoc" %}
## Generate Javadoc
{% include iconHeader.html type="dtTool" %}
If you haven't been commenting your code all along, go back and comment your code with Javadoc.  All classes, methods, and fields should be commented.  If you have been commenting as you have implemented the `Activity` hierarchy, go back and double check that the comments are up to date for the implemented functionality.

Make sure you include comments for overridden method that describe why the override was important. 

Generate Javadoc for `WolfScheduler`.  You may want to delete the existing `doc/` folder before generating a new one to ensure that all Javadoc is updated.  Double check that everything was generated!



{% capture reminder_callout %}
[CSC216 Basics of Jenkins Guide](../jenkins/).
{% endcapture %}
{% include mention.html content=reminder_callout icon="ciTool" type="reminder" title="Reminder: Jenkins Feedback" %}
## Continuous Integration and Automated Grading
{% include iconHeader.html type="ciTool" %}
As with Guided Project 1, and all programming assignments for CSC 216/217, we are using Jenkins as an automated grading and feedback system.  Check your [Jenkins results]({{site.data.grades.jenkins-server}}) and use them to [estimate your grade against the Guided Project 2 rubric](#grading-rubric).




## Final Tasks
{% include iconHeader.html type="task" %}

Before you complete your final submission to [GitHub](https://github.ncsu.edu), you should ensure the following:

  * You have met the [requirements and design for the `WolfScheduler` project](../wolf-scheduler/ws-requirements), except for the conflicting activities functionality.
  * You have a green ball on [Jenkins]({{site.data.grades.jenkins-server}}). (No test failures and no static analysis notifications.)
  * All JUnit tests pass with a green bar (0 errors).  There should be no modifications to the teaching staff tests.
  * All [System Tests](https://docs.google.com/document/d/1bqESm2No4IaTP7mC6i1Hd22fSYWjknjJA_K4_XnFzEI/edit?usp=sharing) pass and actual results are reported.
  * There are no SpotBugs notifications.
  * There are no PMD notifications.
  * There are no CheckStyle notifications.
  * All code is commented with meaningful comments.
  * Javadoc webpages are generated with the latest comments.
  * That you [meet all rubric items for the assignment](#grading-rubric).

Make sure that all code is pushed to GitHub by the assignment deadline.  There are deductions for any late work up to 48 hours.

## Grading Rubric
{% include iconHeader.html type="rubric" %}

Your Wolf Scheduler Guided Project 2 will be evaluated on the following items:

### Overall Rubric

{% include rubricTable.html project="gp2" grade-category="overall" %} 

### Deductions

{% include deductionsRubricTable.html project="deductions" grade-category="overall" %}

### Javadoc Rubric

{% include javadocRubricTable.html project="javadoc" grade-category="overall" %}


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
  - [ ] Commit and push your code changes with a meaningful commit message.  Label your commit with [Test], [Static Analysis], [Fix], [GUI], [Documentation] as appropriate for the change and for future you!
  - [ ] Check Jenkins results for a green ball!  Fix any Jenkins issues.

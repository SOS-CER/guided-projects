---
title: Guided Project 2 WolfScheduler - Activity and Event
tags: [software engineering, software lifecycle, CS2, CSC216, GP2]
description: Independent Task - Update `WolfSchedulerGUI`
navigation: on
pagegroup: gp2
---

# Independent Task: Update `WolfSchedulerGUI`
{% include iconHeader.html type="task" %}

`WolfSchedulerGUI` should be updated to interact with the updated `Event` functionality.


{% capture callout_content %}
  * Update `WolfSchedulerGUI`
{% endcapture %}
{% include callout.html content=callout_content icon="objective" type="learningOutcomes" title="Learning Outcomes" %}


## Update `WolfSchedulerGUI`
[Copy the code from `WolfSchedulerGUI.java`](files/WolfSchedulerGUI.java) into your Eclipse file.  Overwrite the entirety of the old file.



## Run Unit Tests
{% include iconHeader.html type="unitTest" %}

Run your tests!  If any are still failing, use the debugger to help you find the problem.

The tests and resources files are listed below if you would like to ensure that you have the correct versions.  Note that we did add a test to the `course-meeting-days-and-times-valid.csv` file to consider an arranged time.

Test Classes (in test/ directory):
  * [CourseTest.java](files/CourseTest.java)
  * [ExtendedCourseTest.java](files/ExtendedCourseTest.java)
  * [EventTest.java](files/EventTest.java)
  * [CourseRecordIOTest.java](files/CourseRecordIOTest.java)
  * [ActivityRecordIOTest.java](files/ActivityRecordIOTest.java)
  * [WolfSchedulerTest.java](files/WolfSchedulerTest.java)
  
Resource Files (in test/resources/ directory):
  * [course-meeting-days-and-times-valid.csv](files/course-meeting-days-and-times-valid.csv)
  * [course-meeting-days-and-times-invalid.csv](files/course-meeting-days-and-times-invalid.csv)
  * [event-meeting-days-and-times-valid.csv](files/event-meeting-days-and-times-valid.csv)
  * [event-meeting-days-and-times-invalid.csv](files/event-meeting-days-and-times-invalid.csv)

Test Files (in test-files/ directory):
  * [course_records.txt](files/course_records.txt)
  * [expected_activity_records.txt](files/expected_activity_records.txt)
  * [expected_course_records.txt](files/expected_course_records.txt)
  * [expected_empty_export.txt](files/expected_empty_export.txt)
  * [expected_schedule_export.txt](files/expected_schedule_export.txt)
  * [invalid_course_records.txt](files/invalid_course_records.txt)
  * [starter_course_records.txt](files/starter_course_records.txt)
  * [README.txt](files/README.txt)


{% capture reminder_content %}
[Guided Task: Run System Tests](../gp1/gp1-bbtp).
{% endcapture %}
{% include mention.html content=reminder_content icon="ideTool" type="reminder" title="Reminder: Running Tests in Eclipse" %}
## Run System Tests
{% include iconHeader.html type="systemTest" %}
Run `WolfSchedulerGUI` and ensure that you pass [the new and updated suite of system tests for the `WolfScheduler` project](https://docs.google.com/document/d/1bqESm2No4IaTP7mC6i1Hd22fSYWjknjJA_K4_XnFzEI/edit?usp=sharing).  As part of running your tests, you must report the actual results of execution.  Download the document as a Word document by select **File > Download > Microsoft Word** in Google Drive.  Create a new folder in your `WolfScheduler` project called `project_docs` by right clicking on `WolfScheduler` and selecting **New > Folder**.   Save your black box test plan as a Word document (`*.doc` or `*.docx`) in the `project_docs` folder.  As you run each test, report the results of execution in the black box test plan in the actual results column.  DO NOT record, "Passed" or "Failed."  Instead, describe the results, similar to the provided Expected Results.

Make sure all your black box tests pass!  However, if you run out of time, report the actual results of execution - EVEN IF THEY ARE FAILING! You'll earn some points on the system test portion of the [grading rubric](#grading-rubric) for reporting actual, failing results.

{% capture callout_content %}
Check that your System Test Plan is actually pushed to the remote GitHub.  If you saved the file to your project via the file system and pushed using Eclipse, Eclipse likely did not know about the new file.  Refresh your project in Eclipse by right-clicking on the project and selecting **Refresh**.  You should then see the *.docx file in your `project_docs` directory and in the **Git Staging** view.

Also, make sure you have the System Test Plan in the correct loction so the PTFs can find it quickly during grading!
{% endcapture %}
{% include callout.html content=callout_content icon="vcTool" type="reminder" title="Check GitHub for System Test Plan" %}


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
  - [ ] Commit and push your code changes with a meaningful commit message.  Label your commit with "[GUI]" and "[Test]" for future you!
  - [ ] Check Jenkins results for a green ball!  Fix any Jenkins issues.

---
title: Guided Project 3 WolfScheduler - Conflict
description: Independent Task - Submit Project
tags: [software engineering, software lifecycle, CS2, CSC216, GP3]
navigation: on
pagegroup: gp3
---
# Independent Task: Submit Project
{% include iconHeader.html type="task" %}
There are a few tasks that you must complete to wrap up Guided Project 3 for grading.

{% capture callout_content %}
  * Run static analysis tools and fix notifications
{% endcapture %}
{% include callout.html icon="objective" content=callout_content type="learningOutcomes" title="Learning Outcomes" %}
  
{% capture reminder_callout %}
[Guided Task: Run Static Analysis Tools](../gp1/gp1-static-analysis).
{% endcapture %}
{% include mention.html content=reminder_callout icon="saTool" type="reminder" title="Reminder: Running Static Analysis Tools" %}
## Run Static Analysis Tools
Run SpotBugs, PMD, and CheckStyle on your code (if you haven't been already) and remove any notifications. 

{% capture reminder_callout %}
[Guided Task: Generate Javadoc](../gp1/gp1-javadoc).
{% endcapture %}
{% include mention.html content=reminder_callout icon="dtTool" type="reminder" title="Reminder: Generating Javadoc" %}
## Generate Javadoc
If you haven't been commenting your code all along, go back and comment your code with Javadoc.  All classes, methods, and fields should be commented.  If you have been commenting as you have implemented the `Activity` hierarchy, go back and double check that the comments are up to date for the implemented functionality.

Make sure you include comments for overridden method that describe why the override was important. 

Generate Javadoc for `WolfScheduler`.  You may want to delete the existing `doc/` folder before generating a new one to ensure that all Javadoc is updated.  Double check that everything was generated!


{% capture reminder_callout %}
[CSC216 Basics of Jenkins Guide](../jenkins/).
{% endcapture %}
{% include mention.html content=reminder_callout icon="ciTool" type="reminder" title="Reminder: Jenkins Feedback" %}
## Continuous Integration and Automated Grading
As with Guided Project 1 & 2, and all programming assignments for CSC 216/217, we are using Jenkins as an automated grading and feedback system.  Check your [Jenkins results]({{site.data.grades.jenkins-server}}) and use them to [estimate your grade against the Guided Project 3 rubric](#grading-rubric).

## Final Tasks
Before you complete your final submission to [GitHub](https://github.ncsu.edu), you should ensure the following:

  * You have met the [requirements and design for the `WolfScheduler` project](#grading-rubric).
  * You have a green ball on [Jenkins]({{site.data.grades.jenkins-server}}). (No test failures and no static analysis notifications.)
  * All JUnit tests pass with a green bar (0 errors). 
  * All System Tests pass and actual results are reported.
  * There are no SpotBugs notifications.
  * There are no PMD notifications.
  * There are no CheckStyle notifications.
  * All code is commented with meaningful comments.
  * Javadoc webpages are generated with the latest comments.
  * That you [meet all rubric items for the assignment](#grading-rubric).

Make sure that all code is **pushed to GitHub** by the assignment deadline (check all the files are on the remote!).  There are deductions for any late work up to 48 hours.


## Grading Rubric
{% include iconHeader.html type="rubric" %}

Your Wolf Scheduler Guided Project 3 will be evaluated on the following items:

### Overall Rubric

{% include rubricTable.html project="gp3" grade-category="overall" %} 

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
  - [ ] Commit and push your code changes with a meaningful commit message.  Label your commit with "[Final Submission]" for future you!
  - [ ] Check Jenkins results for a green ball!  Fix any Jenkins issues.
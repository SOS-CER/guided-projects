---
title: Guided Project 1 - Software Development Practices and Tools
tags: [software engineering, software lifecycle, CS2, CSC216, GP1]
description: Guided Task - Conclusion
navigation: on
pagegroup: gp1
---

# Guided Task: Conclusion
{% include iconHeader.html type="task,ciTool" %}

You should have a green check on Jenkins and your project (including your System Test Plan and generated Javadoc) should be pushed to the remote.  Now's the time to double check all your work!


## Final Tasks
Before you complete your final submission to [GitHub](https://github.ncsu.edu), you should ensure the following:

  - [ ] You have met the [requirements and design for the `WolfScheduler` project](../wolf-scheduler/ws-requirements)
  - [ ] You have a green check on [Jenkins]({{site.data.grades.jenkins-server}}) (No test failures and no static analysis notifications)
  - [ ] All JUnit tests pass with a green bar (0 errors).  There should be no modifications to the teaching staff tests.
  - [ ]  All [Black Box Tests](gp1-stp) pass AND you've pushed the system test plan document to the remote GitHub (check this by going to https://github.ncsu.edu and verifying the document is there)
  - [ ]  There are no SpotBug notifications
  - [ ]  There are no PMD notifications
  - [ ]  There are no CheckStyle notifications
  - [ ]  All code is commented with meaningful comments
  - [ ]  Javadoc webpages are generated with the latest comments
  - [ ]  That you [meet all rubric items for the assignment](#grading-rubric).

Make sure that all code is pushed to GitHub by the assignment deadline.  There are deductions for any late work up to 48 hours.

## Grading Rubric
{% include iconHeader.html type="rubric" %}

All assignments have a rubric that you can use to estimate your grade.  Use the Jenkins feedback and your black box test results to [estimate the grade for Guided Project 1](../wolf-scheduler/ws-rubric).  

Your Wolf Scheduler Guided Project 1 will be evaluated on the following items:

### Overall Rubric

{% include rubricTable.html project="gp1" grade-category="overall" %} 

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
## Submit!
{% include iconHeader.html type="glance" %}
Use the feedback from Jenkins to make changes to your code.  Any time you make a change, push to GitHub and check the Jenkins results.

  - [ ] Make sure that all fields, methods, and constructors are commented.
  - [ ] Resolve all static analysis notifications.
  - [ ] Fix test failures.
  - [ ] Commit and push your code changes with a meaningful commit message.  Label your commit with "[Implementation]" for future you!
  - [ ] Check Jenkins results for a green check!  Fix any Jenkins issues.
  
## Congratulations!
You've finished the first Guided Project and a good portion of the `WolfScheduler` requirements.  Great work on reviewing prerequisite materials and using the new suite of development tools for CSC 216/217!  You're off to a great start.  Take time to celebrate your accomplishment!

Now, onwards to [Guided Project 2](../gp2/).  [Note: Don't start Guided Project 2 until you're assigned a repository by the teaching staff.]

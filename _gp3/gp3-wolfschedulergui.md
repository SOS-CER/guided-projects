---
title: Guided Project 3 WolfScheduler - Conflict
description: Independent Task - Update `WolfSchedulerGUI`
tags: [software engineering, software lifecycle, CS2, CSC216, GP3]
navigation: on
pagegroup: gp3
---
# Independent Task: Update `WolfSchedulerGUI`
{% include iconHeader.html type="task" %}
Black box test the `WolfScheduler` system to ensure that the conflict functionality is working correctly from end-to-end.

{% capture callout_content %}
  * Run (and revise) black box tests
{% endcapture %}
{% include callout.html icon="objective" content=callout_content type="learningOutcomes" title="Learning Outcomes" %}

## `WolfSchedulerGUI`
`WolfSchedulerGUI` did not require any changes from GP2.  But if you need a new copy, [copy the code from `WolfSchedulerGUI.java`](../gp2/files/WolfSchedulerGUI.java) into your Eclipse file.  Overwrite the entirety of the old file.

## Run System Tests
{% include iconHeader.html type="systemTest" %}
Run your system tests!  If any are still failing, use the debugger to help you find the problem.  Report the actual results of your tests.

If you need to revise your tests to more correctly describe the inputs or outputs, you may do so.

Record the actual results of execution for your tests.  If you run low on time, remember it is better to record the actual test failure; you'll get credit for reporting what's actually happening. 

Make sure that you successfully push your System Test Plan to the remote GitHub repository!  Check the website to make sure it's there!

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
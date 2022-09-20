---
title: Guided Project 1 WolfScheduler - Course and Schedule
tags: [software engineering, software lifecycle, CS2, CSC216, GP1]
description: Guided Task - Continuous Integration and Automated Grading
navigation: on
pagegroup: gp1
---

# Guided Task: Continuous Integration and Automated Grading
{% include iconHeader.html type="task,ciTool" %}

A common software engineering practice is [*continuous integration*](https://pages.github.ncsu.edu/engr-csc-software-development/practices-tools/overview/#continuous-integration). That means developers are continuously committing/pushing their code to version control and evaluating the code by running tests and other analysis tools against their code. The evaluation of the code is typically completed by a continuous integration system, which is a software system that will automatically build, test, run analysis tools (like static analysis), and deploy software. Since this is what the teaching staff does when evaluating your work, we can use a continuous integration system to evaluate your work every time you push to GitHub. That means you should be able to estimate your grade on an assignment from the feedback from Jenkins, the continuous integration server we use for CSC216. On future assignments, Jenkins will also run hidden teaching staff tests and provide you feedback on how well you meet the teaching staff's design!

{% capture callout_content %}
  * Utilize results of a continuous integration system to improve program quality
{% endcapture %}
{% include callout.html content=callout_content icon="objective" type="learningOutcomes" title="Learning Outcomes" %}

 
## Check Jenkins Results
You can access the Guided Project and Project Jenkins via [{{site.data.grades.jenkins-server}}]({{site.data.grades.jenkins-server}}). (Labs will have their own Jenkins servers.)  When you log in, your Jenkins job will be listed using the pattern of `GP1-<repo-name>`. If you don't see a project, then email the teaching staff!

Learn more about the [Jenkins continuous integration system and how to use it to for feedback and to estimate your grade by reading the Jenkins tutorial](https://pages.github.ncsu.edu/engr-csc-software-development/practices-tools/jenkins/). Your goal is a green check (no test failures and no static analysis notifications).  

The Jenkins build for Guided Project 1 will copy the provided teaching staff test cases into your project, overwriting the ones that you were provided. This is to make sure that you didn't accidentally modify the teaching staff tests through an Eclipse QuickFix. If you did modify a test, that will likely lead to a red X on Jenkins, which means code didn't compile. 

If your code doesn't compile, you can see the compiler errors in the Console Output for the build.  To get to the Console Output, select your Jenkins job, the latest build in the box to the lower left, then select Console Output from the left menu.  Scroll down to see the compiler errors.  Use those to resolve any issues.

One way to resolve any issues with the provided tests is to recopy them into your local test files.  The provided tests are:

  * [CourseTest.java](files/CourseTest.java)
  * [CourseRecordIOTest.java](files/CourseRecordIOTest.java)
  * [WolfSchedulerTest.java](files/WolfSchedulerTest.java)

 
## Estimate Your Grade Against the Rubric
All assignments have a rubric that you can use to estimate your grade.  Use the Jenkins feedback and your black box test results to [estimate your grade for Guided Project 1](../wolf-scheduler/ws-rubric).  


 
{% capture reminder-content %} 
GitHub Resources:

  * [Staging Files](https://pages.github.ncsu.edu/engr-csc-software-development/practices-tools/git/git-staging)
  * [Committing Files](https://pages.github.ncsu.edu/engr-csc-software-development/practices-tools/git/git-commit)
  * [Pushing Files](https://pages.github.ncsu.edu/engr-csc-software-development/practices-tools/git/git-push)
{% endcapture %} {% include mention.html content=reminder-content type="reminder" title="Reference: Staging and Pushing to GitHub"%} 
## Check Your Progress
{% include iconHeader.html type="glance" %}
Use the feedback from Jenkins to make changes to your code.  Any time you make a change, push to GitHub and check the Jenkins results.

  - [ ] Make sure that all fields, methods, and constructors are commented.
  - [ ] Resolve all static analysis notifications.
  - [ ] Fix test failures.
  - [ ] Commit and push your code changes with a meaningful commit message.  Label your commit with "[Implementation]" for future you!
  - [ ] Check Jenkins results for a green check!  Fix any Jenkins issues.
    

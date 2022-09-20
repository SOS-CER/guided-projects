---
title: Guided Project 3 WolfScheduler - Conflict
description: Independent Task - Update `WolfScheduler`
tags: [software engineering, software lifecycle, CS2, CSC216, GP3]
navigation: on
pagegroup: gp3
---
# Independent Task: Update `WolfScheduler`
{% include iconHeader.html type="task" %}
There are several updates required for `WolfScheduler` to work with the `Activity.checkConflict` functionality.  `WolfScheduler` will catch any `ConflictExceptions` and throw `IllegalArgumentException`s out to the client. 

{% capture callout_content %}
  * Refactor `WolfScheduler` to check for conflict
{% endcapture %}
{% include callout.html icon="objective" content=callout_content type="learningOutcomes" title="Learning Outcomes" %}

## Update `WolfSchedulerTest` and `WolfScheduler`
`WolfScheduler` should check for possible conflicts when `addCourseToSchedule()` and `addEventToSchedule()` are called.  Update `WolfSchedulerTest` to include tests for the conflict functionality.  

Then update `addCourseToSchedule()` and `addEventToSchedule()` to pass the tests.  `WolfScheduler` will catch any `ConflictExceptions` and throw `IllegalArgumentException`s out to the client with appropriate messages for the dialog boxes.  

  * If a `ConflictException` is caught in `addCourseToSchedule()` and `IllegalArgumentException` is thrown with the message `"The course cannot be added due to a conflict."`.  
  * If a `ConflictException` is caught in `addEventToSchedule()` and `IllegalArgumentException` is thrown with the message `"The event cannot be added due to a conflict."`.  

You may need to go back and update some of the tests that were provided with `WolfSchedulerTest`!  The tests were written before the time conflict functionality was added and will need to be modified based on the full implementation.  You cannot delete the provided test methods, but you can revise them to check that the appropriate exceptions are thrown and that the correct schedule information is there afterwards (i.e., without the conflicting activity).

## Jenkins and Teaching Staff Tests
Now that you are writing your own tests, the teaching staff unit tests will be hidden from you.  The teaching staff tests will run if 1) you have no testing-related PMD notifications and 2) you have greater than 80% statement coverage on non-UI classes.  Teaching staff test are listed with a starting `TS_`.  A failing teaching staff test has a hint that is provided so that you can try creating your own version of the test locally for debugging.  If you have a question about a hint, please post it to Piazza for clarification.

When working on your projects, you may end with lots of teaching staff test failures.  That's ok!  They are there to help you improve your code.  However, you need to be strategic in how to go about fixing them.  You can't just start at the top of the list and work your way down.  Because we utilized composition relationships, certain classes have *dependencies* on other classes.  You should focus on fixing the contained classes before fixing the containers.  For `WolfScheduler`, you should focus on fixing bugs in the `Activity` hierarchy *before* fixing bugs in `WolfScheduler`!  


## Run Coverage
Ensure that `WolfScheduler` has 80% or higher statement coverage.  If not, use the coverage feedback to create more high quality tests.

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
  - [ ] Commit and push your code changes with a meaningful commit message.  Label your commit with "[Implementation]" and "[Test]" for future you!
  - [ ] Check Jenkins results for a green ball!  Fix any Jenkins issues.
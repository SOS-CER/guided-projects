---
title: Guided Project 3 WolfScheduler - Conflict
description: Independent Task - Implement `Conflict` in `Activity`
tags: [software engineering, software lifecycle, CS2, CSC216, GP3]
navigation: on
pagegroup: gp3
---

# Independent Task: Implement `Conflict` in `Activity`
{% include iconHeader.html type="task" %}
Use TDD to implement the `checkConflict()` method in `Activity`.

{% capture callout_content %}
  * Use test driven development to implement and test a method.
{% endcapture %}
{% include callout.html icon="objective" content=callout_content type="learningOutcomes" title="Learning Outcomes" %}

{% capture callout_content %}
Test Driven Development (TDD) is the process of using the requirements and object design to write the unit tests for a class first, and then use the tests to drive the implementation of the methods in the class.  The process is typically iterative.  Start with the simplest test first and implement the functionality to pass. Then add additional tests that consider other paths, edge cases, and error cases.  After adding each test, implement the functionality to pass it (if needed).

TDD is a highly effective process for developing code that is well tested.  By testing right away, and letting the tests drive development, you will implement more high quality code more quickly and not run out of time for testing!
{% endcapture %}
{% include callout.html content=callout_content type="bestPractices" icon="ttTool" title="Best Practice: Test Driven Development (TDD)" %}

{% capture reminder-content %}
There are several resources provided for writing tests, including sample test code:

  * [Dr. Heckman's Testing Lecture Notes](https://pages.github.ncsu.edu/engr-csc216/Heckman/slides/02_TestingDebugging.pdf)
  * [Seasons Test Example](https://pages.github.ncsu.edu/engr-csc216/Heckman/resources/Testing_CS2.zip)
  * [Guided Project Tests](../wolf-scheduler/ws-test)
  
Use the provided tests from Guided Projects 1 & 2 to help you write your own tests for Guided Project 3!
{% endcapture %}
{% include mention.html content=reminder-content type="reminder" icon="ttTool" title="Reminder: Resources on Writing Tests" %}
## Test and Implement `Activity.checkConflict()`
Use TDD to implement the `checkConflict()` method in `Activity`.  The teaching staff has provided a list of tests to consider, but this is by no means an exhaustive list or all of the tests that the teaching staff will evaluate you on.  Use your testing skills to develop an extensive set of tests for `Activity.checkConflict()`.



**Tests for consideration:**

  * No conflict test where `a2.checkConflict(a1)` is called.  This switches the `this` and parameter to make sure that the method is commutative.
  * Conflict on a single day.
  * Conflict where the `endTime` for `this` is the same as the `startTime` for `possiblyConflictingActivity`.
  
As you write each test (which can continue in the same method or a separate test method for each test), update `Activity.checkConflict()` as appropriate to test the new tests without failing the old tests (or any other tests in the test suite).

When you are confident that your `Activity.checkConflict()` method is working correctly, you can move on to the next steps.

## Jenkins and Teaching Staff Tests
Now that you are writing your own tests, the teaching staff unit tests will be hidden from you.  The teaching staff tests will run if 1) you have no testing-related PMD notifications and 2) you have greater than 80% statement coverage on non-UI classes.  Teaching staff test are listed with a starting `TS_`.  A failing teaching staff test has a hint that is provided so that you can try creating your own version of the test locally for debugging.  If you have a question about a hint, please post it to Piazza for clarification.

When working on your projects, you may end with lots of teaching staff test failures.  That's ok!  They are there to help you improve your code.  However, you need to be strategic in how to go about fixing them.  You can't just start at the top of the list and work your way down.  Because we utilized composition relationships, certain classes have *dependencies* on other classes.  You should focus on fixing the contained classes before fixing the containers.  For `WolfScheduler`, you should focus on fixing bugs in the `Activity` hierarchy *before* fixing bugs in `WolfScheduler`!  


## Document `Activity.checkConflict()`
As always, you should document the method with details about the implementation that would help a client of `Activity` work with the method correctly in their own code!


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
  - [ ] Check Jenkins results for a yellow ball.  Fix any failing tests in `TS_ActivityTest` and in the `course` package.  Test failures in the `scheduler` package can wait until later in the Guided Project.
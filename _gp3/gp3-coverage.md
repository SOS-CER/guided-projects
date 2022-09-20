---
title: Guided Project 3 WolfScheduler - Conflict
description: Independent Task - Coverage
tags: [software engineering, software lifecycle, CS2, CSC216, GP3]
navigation: on
pagegroup: gp3
---

# Independent Task: Coverage
{% include iconHeader.html type="task" %}
Use EclEmma to evaluate coverage on `checkConflict()` method in `Activity`.

{% capture callout_content %}
  * Use coverage to determine if additional tests are needed to execute other, uncovered, paths
{% endcapture %}
{% include callout.html icon="objective" content=callout_content type="learningOutcomes" title="Learning Outcomes" %}

{% capture callout_content %}
Coverage is a measure of the code executed when running a test case.  The principle behind coverage is that a line of code that has been executed is less likely to contain a bug than a non-executed line of code.  There are four levels of coverage:

  * Method coverage: every method called at least once.
  * Statement/Line coverage: every statement executed at least once.
  * Branch coverage: every conditional statement evaluated on both its true and false paths.
  * Condition coverage: every predicate in a compound conditional evalue on both its true and false paths.
  
For CSC 216, the teaching staff expects that you will achieve at least 80% statement coverage on *each* model class (which are any of the classes not in the `ui` package).  A coverage tool can identify paths that you have not yet executed with your tests.  Using the feedback you can write additional tests to exercise other portions of your code.

There are some limitations to code coverage.  Since you are using your existing code to drive your testing, your tests won't tell you if you're missing functionality.  That is one reason why you should use TDD to drive the implementation and a reason for why we have multiple types of testing - the missing functionality might be caught in system level tests.

Also, don't write poor tests just to make your coverage tool happy.  Take the time to write a meaningful test so that you may have increased confidence that your code works correctly.  PMD will provide notifications on poor test practices!
{% endcapture %}
{% include callout.html content=callout_content type="bestPractices" icon="ccTool" title="Best Practice: Coverage" %}

## Run Tests for Coverage
To run tests for coverage, right click on the `test/` source folder and select **Coverage As > JUnit Test**.

When evaluating coverage locally, focus only on the coverage of classes that are not in the `*.ui` package.  The coverage of the test classes themselves and any user interface classes are not considered when evaluating the coverage of your tests.  Jenkins is set up to exclude test classes and user interface classes, but your local EclEmma is not.  Don't panic if the numbers seem low.

One last thing to check is that EclEmma is reporting the right metrics.  Click the down arrow (View Menu) option in the **Coverage** view.  Select **Line Counters** for seeing statement/line coverage.  If you want to see condition coverage, use the **Branch Counters** option.


{% capture reminder-content %}
There are several resources provided about code coverage:

  * [Dr. Heckman's Coverage and Static Analysis Lecture Notes](https://pages.github.ncsu.edu/engr-csc216/Heckman/slides/03_Coverage_StaticAnalysis.pdf)
  
{% endcapture %}
{% include mention.html content=reminder-content type="reminder" icon="ccTool" title="Reminder: Resources on Coverage" %}
## Use Coverage to Drive Testing
The CSC 216 Teaching Staff expect 80% statement coverage on *every* non-UI and non-test class.  While the unit tests provided by the teaching staff for the rest of the project are extensive, they may not achieve 80% coverage on your implementation.  Add additional tests to reach the 80% coverage threshold for all non-UI and non-test classes: `Activity`, `Course`, `Event`, `ConflictException`, `ActivityRecordIO`, `CourseRecordIO`, and `WolfScheduler`.

## Jenkins and Teaching Staff Tests
Now that you are writing your own tests, the teaching staff unit tests will be hidden from you.  The teaching staff tests will run if 1) you have no testing-related PMD notifications and 2) you have greater than 80% statement coverage on non-UI classes.  Teaching staff test are listed with a starting `TS_`.  A failing teaching staff test has a hint that is provided so that you can try creating your own version of the test locally for debugging.  If you have a question about a hint, please post it to Piazza for clarification.

When working on your projects, you may end with lots of teaching staff test failures.  That's ok!  They are there to help you improve your code.  However, you need to be strategic in how to go about fixing them.  You can't just start at the top of the list and work your way down.  Because we utilized composition relationships, certain classes have *dependencies* on other classes.  You should focus on fixing the contained classes before fixing the containers.  For `WolfScheduler`, you should focus on fixing bugs in the `Activity` hierarchy *before* fixing bugs in `WolfScheduler`!  

When you look at Jenkins feedback at this step, make sure you look at the console output.  That provides a listing of the statement coverage for your non-UI classes and will let you know about PMD notifications.  If the teaching staff test cases are blocked, the statement `SKIPPING TEACHING STAFF TEST CASES` will be displayed.  There are some sample console outputs below.  Note, you can ignore the output lines about the `Nashorn engine`.

**PMD Notification** There is a statement `Project contains X JUnit-related PMD alerts`, which leads to the statement `SKIPPING TEACHING STAFF TEST CASES`.

```
11:26:14      [echo] ---> Checking coverage thresholds for source files
11:26:14    [script] Warning: Nashorn engine is planned to be removed from a future JDK release
11:26:14      [exec] Project contains 1 JUnit-related PMD alerts
11:26:14      [exec] Result: 1
11:26:14    [script] Warning: Nashorn engine is planned to be removed from a future JDK release
11:26:14      [echo] 
11:26:14      [echo] *****SKIPPING TEACHING STAFF TEST CASES*****
```

**Coverage Report - Insufficient Coverage** If the statement/line coverage (last column) for one or more classes is under 80%, a message of `TOTAL of X classes not meeting the 80% line coverage threshold` will be displayed, which leads to the statement of `SKIPPING TEACHING STAFF TEST CASES`.

```
11:55:08      [exec] 	CLASS                                    METHOD COVERAGE      LINE COVERAGE       
11:55:08      [exec] 	Activity                                 100                  83                  
11:55:08      [exec] 	Event                                    90                   93                  
11:55:08      [exec] 	Course                                   82                   72                  
11:55:08      [exec] 	ConflictException                        100                  100                 
11:55:08      [exec] 	CourseRecordIO                           66                   97                  
11:55:08      [exec] 	ActivityRecordIO                         50                   85                  
11:55:08      [exec] 	WolfScheduler                            0                    0                   
11:55:08      [exec] TOTAL of 2 classes not meeting the 80% line coverage threshold
11:55:08      [exec] Result: 1
11:55:08    [script] Warning: Nashorn engine is planned to be removed from a future JDK release
11:55:08      [echo] 
11:55:08      [echo] *****SKIPPING TEACHING STAFF TEST CASES*****
```

**Coverage Report - No Problems** The statement/line coverage (last column) exceeds the 80% threshold per class.  There is a statement that a `TOTAL of 0 classes not meeting the 80% line coverage threshold` and there are lines stating that the teaching staff tests are building and executing.  You can see the full results, including hints, in the test reports.

```
11:40:24      [exec] 	CLASS                                    METHOD COVERAGE      LINE COVERAGE       
11:40:24      [exec] 	Activity                                 100                  91                  
11:40:24      [exec] 	Event                                    100                  100                 
11:40:24      [exec] 	Course                                   100                  93                  
11:40:24      [exec] 	ConflictException                        100                  100                 
11:40:24      [exec] 	CourseRecordIO                           66                   97                  
11:40:24      [exec] 	ActivityRecordIO                         50                   85                  
11:40:24      [exec] 	WolfScheduler                            100                  93                  
11:40:24      [exec] TOTAL of 0 classes not meeting the 80% line coverage threshold
11:40:24    [script] Warning: Nashorn engine is planned to be removed from a future JDK release
11:40:24    [script] Warning: Nashorn engine is planned to be removed from a future JDK release
11:40:24      [echo] 
11:40:24      [echo] ---> Building Teaching Staff Tests
11:40:25      [echo] 
11:40:25      [echo] ---> Executing Teaching Staff unit tests
```


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
  - [ ] Commit and push your code changes with a meaningful commit message.  Label your commit with "[Test]" for future you!
  - [ ] Check Jenkins results for a yellow ball!  Fix any coverage issues in the `course` and `io` packages.  Other test failures and coverage issues from the `scheduler` package can wait for the next step.
---
title: WolfScheduler
tags: [software engineering, software lifecycle, CS2, CSC216]
description: WolfScheduler Unit and System Testing
navigation: on
pagegroup: wolf-scheduler
---

# WolfScheduler Unit and System Testing
{% include iconHeader.html type="unitTest,systemTest" %}

The [testing](../se-overview/test) phase of development exercises the program under a variety of valid and error paths of execution.  You will execute [unit tests](../se-overview/test#unit-test) and [system tests](../se-overview/test#system-test) on `WolfScheduler` for each Guided Project.  Some of the unit tests and all of the black box tests will be provided to you.


## Guided Project 1

### GP1 Unit Testing
The teaching staff have provided the following JUnit test classes (all test class names are links).  All of these test classes should be stored in a source folder named `test/` in the `WolfScheduler` project.  Each test class belongs to a package with the same name as the package the class under test belongs to.  That means `CourseTest` is in the `edu.ncsu.csc216.wolf_scheduler.course` package, just like `Course`.  The difference is that `CourseTest` is in the `test/` folder and `Course` is in the `src/` folder.

  * [CourseTest.java](../gp1/files/CourseTest.java)
  * [CourseRecordIOTest.java](../gp1/files/CourseRecordIOTest.java)
  * [WolfSchedulerTest.java](../gp1/files/WolfSchedulerTest.java)
  
Resources files help run lots of different tests with various inputs and output.  These files should be in your `test/resources/` directory.

  * [course-meeting-days-and-times-valid.csv](../gp1/files/course-meeting-days-and-times-valid.csv)
  * [course-meeting-days-and-times-invalid.csv](../gp1/files/course-meeting-days-and-times-invalid.csv)
  
The tests for `CourseRecordIO` and `WolfScheduler` require input files and expected results files.  These should be stored in a folder name `test-files` in the `WolfSchdeuler` project.

  * [course_records.txt](../gp1/files/course_records.txt)
  * [expected_course_records.txt](../gp1/files/expected_course_records.txt)
  * [expected_empty_export.txt](../gp1/files/expected_empty_export.txt)
  * [expected_schedule_export.txt](../gp1/files/expected_schedule_export.txt)
  * [invalid_course_records.txt](../gp1/files/invalid_course_records.txt)
  * [starter_course_records.txt](../gp1/files/starter_course_records.txt)


### GP1 System Testing
Your WolfScheduler program must pass the teaching staff [Black Box Tests](https://drive.google.com/open?id=1j2JDgzZXgbv8t18s-iN70QjYeyq12EO0ZGS_k8ta9fo). Download the document as a Word document (**File > Download > Microsoft Word**) and copy it into a new folder, `bbtp/`, in the `WolfScheduler` project.

There are 13 tests. Run your test cases and report the actual results of execution. All parts of the test must pass to receive credit for that test case. You will receive partial credit by reporting failing actual results that match what your project actual does for the test.


## Guided Project 2


### GP2 Unit Testing
The teaching staff have provided the following JUnit test classes (all test class names are links).  All of these test classes should be stored in a source folder named `test/` in the `WolfScheduler` project.  Each test class belongs to a package with the same name as the package the class under test belongs to.  That means `CourseTest` is in the `edu.ncsu.csc216.wolf_scheduler.course` package, just like `Course`.  The difference is that `CourseTest` is in the `test/` folder and `Course` is in the `src/` folder.  These tests have been updated to meet the requirements for Guided Project 2.


Test Classes (in test/ directory):
  * [CourseTest.java](../gp2/files/CourseTest.java)
  * [ExtendedCourseTest.java](../gp2/files/ExtendedCourseTest.java)
  * [EventTest.java](../gp2/files/EventTest.java)
  * [CourseRecordIOTest.java](../gp2/files/CourseRecordIOTest.java)
  * [ActivityRecordIOTest.java](../gp2/files/ActivityRecordIOTest.java)
  * [WolfSchedulerTest.java](../gp2/files/WolfSchedulerTest.java)
  
Resource Files (in test/resources/ directory):
  * [course-meeting-days-and-times-valid.csv](../gp2/files/course-meeting-days-and-times-valid.csv)
  * [course-meeting-days-and-times-invalid.csv](../gp2/files/course-meeting-days-and-times-invalid.csv)
  * [event-meeting-days-and-times-valid.csv](../gp2/files/event-meeting-days-and-times-valid.csv)
  * [event-meeting-days-and-times-invalid.csv](../gp2/files/event-meeting-days-and-times-invalid.csv)

Test Files (in test-files/ directory):
  * [course_records.txt](../gp2/files/course_records.txt)
  * [expected_activity_records.txt](../gp2/files/expected_activity_records.txt)
  * [expected_course_records.txt](../gp2/files/expected_course_records.txt)
  * [expected_empty_export.txt](../gp2/files/expected_empty_export.txt)
  * [expected_schedule_export.txt](../gp2/files/expected_schedule_export.txt)
  * [invalid_course_records.txt](../gp2/files/invalid_course_records.txt)
  * [starter_course_records.txt](../gp2/files/starter_course_records.txt)
  * [README.txt](../gp2/files/README.txt)
  
  
### GP2 System Testing
Your WolfScheduler program must pass the teaching staff [Black Box Tests](https://docs.google.com/a/ncsu.edu/document/d/1WFNfjRiCVHksbYfR6ugw1q_9yTvy7Sv87zaFWDY_SUY/edit?usp=sharing). Download the document as a Word document (**File > Download > Microsoft Word**) and copy it into a new folder, `bbtp/`, in the `WolfScheduler` project.

There are 15 tests. Run your test cases and report the actual results of execution. All parts of the test must pass to receive credit for that test case. You will receive partial credit by reporting failing actual results that match what your project actual does for the test.


## Guided Project 3

### GP3 Unit Testing
The teaching staff have provided the following JUnit test classes for GP2 (all test class names are links).  You'll be adding your own tests in GP3.  All of these test classes should be stored in a source folder named `test/` in the `WolfScheduler` project.  Each test class belongs to a package with the same name as the package the class under test belongs to.  That means `CourseTest` is in the `edu.ncsu.csc216.wolf_scheduler.course` package, just like `Course`.  The difference is that `CourseTest` is in the `test/` folder and `Course` is in the `src/` folder.  

You should start with the provided GP2 test suite.  As part of the GP3 instructions you may need to refactor the provided tests.  That is ok as long as you meet the teaching staff design and pass the teaching staff version of the tests on Jenkins.  Please use the GP2 test materials, above, as the starting point.


You will be adding tests to handle evaluate how well your program meets the requirements related to the conflict functionality.  Additionally, you are expected to have at least 80% statement coverage on all of your non-GUI classes.
  
There is now a hidden suite of teaching staff tests that include the provided tests (above) that were modified for the new design and testing of the new functionality.  You are expected to pass all of the hidden teaching staff tests in addition to your own test suite.


### GP3 System Testing
Your WolfScheduler program must pass your [Black Box Tests](https://docs.google.com/document/d/1nlA4r6RaMTmbW94F6__qiNGOnbmRVZSAryprbxCRruY/edit). Download the document as a Word document (**File > Download > Microsoft Word**) and copy it into a new folder, `bbtp/`, in the `WolfScheduler` project.  

There are 15 tests from Guided Project 2.  You must update the tests to fix any that might fail due to the new conflict functionality.  Additionally, you must write 5 additional tests.  The cells should be highlighted to show the changes. Run your test cases and report the actual results of execution. All parts of the test must pass to receive credit for that test case. You will receive partial credit by reporting failing actual results that match what your project actual does for the test.

The teaching staff will also have their own suite of black box tests that they will run on your program after the deadline.
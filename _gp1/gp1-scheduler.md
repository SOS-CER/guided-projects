---
title: Guided Project 1 - Software Development Practices and Tools
tags: [software engineering, software lifecycle, CS2, CSC216, GP1]
description: Independent Task - Implement `WolfScheduler`
navigation: on
pagegroup: gp1
---
 
# Independent Task: Implement `WolfScheduler`
{% include iconHeader.html type="task" %}
The last model class that you need to implement is `WolfScheduler`.  `WolfScheduler` reads in and stores as a list all of the `Course` records stored in a file ([UC 1: Load Course Catalog](../wolf-scheduler/ws-requirements#uc1)).  Additionally, `WolfScheduler` creates a schedule for the current user (a student) and provides functionality for naming the schedule ([[UC 2: Rename Schedule](../wolf-scheduler/ws-requirements#uc3)]), adding a `Course` to the schedule ([[UC 4: Add Course to Schedule](../wolf-scheduler/ws-requirements#uc4)]), removing a `Course` from the schedule ([[UC 5: Remove Course from Schedule](../wolf-scheduler/ws-requirements#uc5)]), resetting the schedule ([[Use Case 8: Reset Schedule](../wolf-scheduler/ws-requirements#uc8)]).  You will start the work needed to pass the appropriate error messages to the graphical user interface (GUI).  However, at this time you will NOT be implementing the conflict functionality.

Note that there are several steps that you will need to complete to fully implement `WolfScheduler`.  The tasks in this section are a review of prerequisite materials or of topics covered earlier in the Guided Project.  Where appropriate, we will provide links to earlier sections that will help as you complete the tasks in this portion of the Guided Project!

{% capture callout_content %}
  * Implement `WolfScheduler`
{% endcapture %}
{% include callout.html content=callout_content icon="objective" type="learningOutcomes" title="Learning Outcomes" %}

{% capture reminder-content %} 
Reminders about Eclipse code creation features:

  * [Guided Task: Your First Eclipse Project - Create a Package](gp1-eclipse-intro#create-a-package)
  * [Guided Task: Your First Eclipse Project - Create a Class](gp1-eclipse-intro#create-a-class)
  * [Guided Task: Eclipse Quick Fix Tool - Quick Fix](gp1-quick-fix#quick-fix)
  * [Guided Task: Eclipse Quick Fix Tool - Create `CourseRecordIO` Methods](gp1-quick-fix#create-courserecordio-methods)
{% endcapture %}
{% include mention.html content=reminder-content type="reminder" title="Reminder: Eclipse Artifact Creation" %}
## Setup `WolfSchedulerTest` and `WolfScheduler`
Use Eclipse's tools to set up the classes for `WolfSchedulerTest` and `WolfScheduler`.  Follow these steps:

  1. Create a new package called `edu.ncsu.csc216.wolf_scheduler.scheduler` in the `test` folder of the `WolfScheduler` project.
  
  2. Create a new Java class called `WolfSchedulerTest` in the `edu.ncsu.csc216.wolf_scheduler.scheduler` package of the `test` source directory of the `WolfScheduler` project.
  
  3. [Copy the code from `WolfSchedulerTest.java](files/WolfSchedulerTest.java) into your Eclipse file.
  
  4. Using the Quick Fix tool, create a new Java class called `WolfScheduler` in the `edu.ncsu.csc216.wolf_scheduler.scheduler` package of the `src` source directory of the `WolfScheduler` project.

  5. Using the Quick Fix tool, create `WolfScheduler`'s public methods from the compiler errors in  `WolfSchedulerTest`.  You can adjust the parameter names as you work on implementing each method in later steps.  You may also need to update the return type if the generated return type is `Object`.  
     * Update the return types of  `getCourseCatalog()`, `getScheduledCourses()`, and `getFullScheduledCourses()` `String[][]`.
	 * Update the return types of `addCourseToSchedule()` and `removeCourseFromSchedule()` to `boolean`.
	 * Update the return type of `getCourseFromCatalog()` to `Course`.
	 * Update the return type of `getScheduleTitle()` to `String`.
	 
  6. The `WolfScheduler` class has three pieces of state.  Write the code to create the three fields for `WolfScheduler` (there's no Quick Fix for this step). You will need to import both `ArrayList` and `Course` using Quick Fix.

     * a course catalog (an `ArrayList` of `Course`s) called `catalog`
     * a schedule (an `ArrayList` of `Course`s) called `schedule`
     * a schedule title (a `String`) called `title`


 
## Implement `WolfScheduler` Constructor and Methods
There are several `WolfScheduler` methods that you must implement so that `WolfScheduler` will pass the tests in `WolfSchedulerTest`.  The sections below provide implementation details for each of the methods.  You'll pass more tests as you implement each of the methods.

{% capture callout_content %}
Writing comments as you write your code can help you understand the problem that you're working on and ensures that future you will understand you code in a few months. Writing the comments first can help you better understand what a method should do. Before implementing each method, write the Javadoc comments for the method.  Then implement.  Finally, revisit the comments so that they match your implementation.  

Don't put off commenting until the end of the project!
{% endcapture %}
{% include callout.html content=callout_content icon="dnTool" type="bestPractices" title="Best Practice: Comment as you Code" %}


{% capture reminder-content %} 
[Guided Project 1: Renaming Identifiers](gp1-quick-fix#renaming-identifiers)
{% endcapture %}
{% include mention.html content=reminder-content type="reminder" title="Reminder: Rename" %}
### Implement `WolfScheduler()`

The `WolfScheduler` constructor has a parameter, which is the filename for the course records that should be read in and stored in the `ArrayList` of `Course`s.  You will likely need to change the name of the parameter from the one created via Quick Fix.  You can use the rename refactoring to rename both the parameter and the Javadoc name.

The constructor should complete the following tasks:

  * construct an empty `ArrayList` to hold the schedule in the `schedule` field
  * set the `title` field to the default "My Schedule" as described in the [requirements](../wolf-scheduler/ws-requirements)
  * try to add the `Course` objects from the input file to the catalog.  An `IllegalArgumentException` should be thrown with the message of "Cannot find file." if `CourseRecordIO.readCourseRecords()` throws an exception.
  
To add the `Course` objects from the input file to the `catalog`, you will need to work with the `CourseRecordIO` class.  Note that all the `CourseRecordIO` methods are static.  You work with them through the class itself (e.g., `CourseRecordIO.readCourseRecords(filename);`).  You can see examples of working with the `CourseRecordIO` class in `CourseRecordIOTest`!

After implementing the constructor, you can run your tests, but they should all fail.  The constructor test depends on other methods in `WolfScheduler` working properly.  You may have to revisit the constructor to debug issues.

{% capture callout_content %}
All `Exception` classes have a constructor with a `String` parameter for a message.  That message is passed with the `Exception` and may be retrieved through a call to `getMessage()`.  By providing error messages as part of an `Exception`, the error functionality is tied to the model.  Then any front end classes will use the same error message!
{% endcapture %}
{% include callout.html content=callout_content icon="plTool" type="bestPractices" title="Best Practice: Exception Messages" %}


### Implement `getCourseCatalog()`
`getCourseCatalog()` returns a 2D `String` array of the `catalog`.  This array is used in the GUI to create the table of course catalog information.  There is a row for each `Course` and three columns for `name`, `section`, and `title`.  If there are no `Courses` in the catalog, an empty 2D `String` array is returned.

The test `testGetCourseCatalog()` should pass after you implement this method.
 
### Implement `getScheduledCourses()`
`getScheduledCourses()` returns a 2D `String` array of the schedule.  This array is used in the GUI to create the table of course catalog information.  There is a row for each `Course` and three columns for `name`, `section`, and `title`.  If there are no `Courses` in the schedule, an empty 2D `String` array is returned.


 
### Implement `getFullScheduledCourses()`
`getFullScheduledCourses()` returns a 2D `String` array of the schedule with all information.  This array is used in the GUI to create the table of course catalog information.  There is a row for each `Course` and six columns for `name`, `section`, `title`, `credits`, `instructorId`, and the meeting days string (e.g., `getMeetingString()`.  If there are no `Courses` in the schedule, an empty 2D `String` array is returned.



{% capture reminder-content %} 
[Guided Project 1: Working with the Java Libraries](gp1-libraries#java-collections-framework)
{% endcapture %}
{% include mention.html content=reminder-content type="reminder" title="Reminder: Using ArrayLists" %}
### Implement `getCourseFromCatalog()`
`getCourseFromCatalog()` has two parameters: a course `name` and `section`.  Since a `Course` in the catalog is distinct by `name` and `section` we can use those two items to find a `Course`.  If the `Course` with the given `name` and `section` does not exist in the catalog, return `null`.

You will iterate through all the elements of the `catalog` `ArrayList` and try to find a `Course` with the given `name` and `section`.  Once you find it, you can return it immediately.  If you reach the end of the loop without finding the `Course`, return `null`.

The following tests should pass after you implement this method:
  * `testGetCourseCatalog()`
  * `testGetCourseFromCatalog()` 
 
### Implement `addCourseToSchedule()`
`addCourseToSchedule()` returns true if the given `Course` (represented by the `name` and `section`) meets the following criteria: 1) the course exists in the catalog and 2) the course is successfully added to the student's schedule.  

If the `Course` is not in the catalog, it cannot be added to the schedule and the method returns false.

A `Course` with the same `name` as another `Course` already in the schedule cannot be added to the schedule. This means a student can't be enrolled in both Section 001 and 002 of CSC216 at the same time.  If a `Course` with the same name is already in the schedule, an `IllegalArgumentException` with the error message of "You are already enrolled in &lt;course name&gt;" is thrown.

The following tests should pass after you implement this method:
  * `testGetCourseCatalog()`
  * `testGetCourseFromCatalog()`
  * `testGetScheduledCourses()`
  * `testGetFullScheduledCourses()`
  * `testAddCourse()`
  

### Implement `removeCourseFromSchedule()`
`removeCourseFromSchedule()` returns true if the given `Course` (represented by the `name` and `section`) can be removed from the student's schedule.  The `Course` should be removed. 

The method returns false if the `Course` isn't in the schedule.

The following tests should pass after you implement this method:
  * `testGetCourseCatalog()`
  * `testGetCourseFromCatalog()`
  * `testGetScheduledCourses()`
  * `testGetFullScheduledCourses()`
  * `testAddCourse()`
  * `testRemoveCourseFromSchedule()`
 
### Implement `resetSchedule()`
`resetSchedule()` creates a empty `ArrayList` for the `schedule`.  

The following tests should pass after you implement this method:
  * `testGetCourseCatalog()`
  * `testGetCourseFromCatalog()`
  * `testGetScheduledCourses()`
  * `testGetFullScheduledCourses()`
  * `testAddCourse()`
  * `testRemoveCourseFromSchedule()`
  * `testResetSchedule()`
 
### Implement `getScheduleTitle()` and `setScheduleTitle()`
`getScheduleTitle()` returns the schedule title.   `setScheduleTitle()` throws an `IllegalArgumentException` if the title is `null` with an error message of "Title cannot be null."

The following tests should pass after you implement this method:
  * `testGetCourseCatalog()`
  * `testGetCourseFromCatalog()`
  * `testGetScheduledCourses()`
  * `testGetFullScheduledCourses()`
  * `testAddCourse()`
  * `testRemoveCourseFromSchedule()`
  * `testResetSchedule()`
  * `testSetScheduleTitle()`
  
 
### Implement `exportSchedule()`
`exportSchedule()` receives a `String` parameter that is the filename where the student's schedule will be saved to.  You will use the `CourseRecordIO.writeCourseRecords()` to export the file.  If `CourseRecordIO.writeCourseRecords()` throws an `IOException`, catch it and throw a new `IllegalArgumentException` with the message of "The file cannot be saved.".

Note that all the `CourseRecordIO` methods are static.  You work with them through the class itself (e.g., `CourseRecordIO.readCourseRecords(filename);`).  You can see examples of working with the `CourseRecordIO` class in `CourseRecordIOTest`!
  
All tests should pass after you implement this method:
  * `testGetCourseCatalog()`
  * `testGetCourseFromCatalog()`
  * `testGetScheduledCourses()`
  * `testGetFullScheduledCourses()`
  * `testAddCourse()`
  * `testRemoveCourseFromSchedule()`
  * `testResetSchedule()`
  * `testSetScheduleTitle()`
  * `testExportSchedule()`
  * `testWolfScheduler()`
 
{% capture reminder-content %} 
GitHub Resources:

  * [Staging Files](https://pages.github.ncsu.edu/engr-csc-software-development/practices-tools/git/git-staging)
  * [Committing Files](https://pages.github.ncsu.edu/engr-csc-software-development/practices-tools/git/git-commit)
  * [Pushing Files](https://pages.github.ncsu.edu/engr-csc-software-development/practices-tools/git/git-push)
{% endcapture %} {% include mention.html content=reminder-content type="reminder" title="Reference: Staging and Pushing to GitHub"%} 
## Check Your Progress
{% include iconHeader.html type="glance" %}
Before moving on to the next portion of the Guided Project, complete the following tasks:

  - [ ] Make sure that all fields, methods, and constructors are commented.
  - [ ] Resolve all static analysis notifications.
  - [ ] Fix test failures.
  - [ ] Commit and push your code changes with a meaningful commit message. Label your commit with "[Implementation]" for future you!
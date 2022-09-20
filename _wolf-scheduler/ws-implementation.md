---
title: WolfScheduler
description: WolfScheduler Implementation
tags: [software engineering, software lifecycle, CS2, CSC216]
navigation: on
pagegroup: wolf-scheduler
---

# WolfScheduler Implementation
{% include iconHeader.html type="implementation" %}

For the [implementation](../se-overview/implementation) phase of development, you will implement the provided design so that all of the pieces of the project work as a coherent whole.

For each Guided Project, you will be provided with a set of files like the GUI (provided in this section) and test files (provided in the [testing](ws-test) section).

## Guided Project 1
[Guided Project 1](../gp1/) will walk you through the creation of the `WolfScheduler` project, but an overview of each class and method are provided here.  Note that all getters and setters for the fields are assumed.  All setters must be implemented so that they do not break any invariants from the requirements (e.g., `Course.setTitle()` should not allow `title` to be set to `null` or empty string).


### `edu.ncsu.csc216.wolf_scheduler.course`
Unless otherwise noted, all constants and fields are `private` and all methods are `public`.  Constants should be `static` and `final`. There are no static methods in the `Course` class.

**`Course` Constants & Fields**

  * `SECTION_LENGTH`: constant containing the length of the `section` `String`, which is a value of 3
  * `MAX_NAME_LENGTH`: constant containing the maximum length of the `name` `String`, which is a value of 6
  * `MIN_NAME_LENGTH`: constant containing the minimum length of the `name` `String`, which is a value of 4
  * `MAX_CREDITS`: constant containing the maximum number of credits for a course, which is a value of 5
  * `MIN_CREDITS`: constant containing the minimum number of credits for a course, which is a value of 1
  * `UPPER_TIME`: constant containing the upper military time, which is a value of 2400
  * `UPPER HOUR`: constant containing the upper value for an hour, which is a value of 60
  * `name`: `String` containing the `Course`'s name
  * `title`: `String` containing the `Course`'s title
  * `section`: `String` containing the `Course`'s section
  * `credits`: `int` containing the `Course`'s credit hours
  * `instructorId`: `String` containing the `Course`'s instructor id
  * `meetingDays`: `String` containing the `Course`'s meeting days
  * `startTime`: `int` containing the `Course`'s start time
  * `endTime`: `int` containing the `Course`'s end time
  
**`Course` Constructors**

  * `Course(String name, String title, String section, int credits, String instructorId, String meetingDays, int startTime, int endTime)`: Sets the fields to the given values or throws an `IllegalArgumentException` if provided an invalid value.
  * `Course(String name, String title, String section, int credits, String instructorId, String meetingDays)`: Sets the fields to the given values or throws an `IllegalArgumentException` if provided an invalid value.  The values of `startTime` and `endTime` are set to 0.
  
**`Course` Methods**

  * Each field has a getter, which returns the field.  There is no special logic to any of the getters, so they are not listed individually.
  * `setName()`: a private method that throws an `IllegalArgumentException` if the parameter is null or less than the `MIN_NAME_LENGTH` or greater than the `MAX_NAME_LENGTH`.
  * `setTitle()`: throws an `IllegalArgumentException` if the parameter is null or an empty `String`.
  * `setSection()`: throws an `IllegalArgumentException` if the parameter is null or has a length not equal to `SECTION_LENGTH`.
  * `setCredits()`: throws an `IllegalArgumentException` if the parameter is less than `MIN_CREDITS` or greater than `MAX_CREDITS`
  * `setInstructorId()`: throws an `IllegalArgumentException` if the parameter is null or an empty `String`.
  * `setMeetingDays()`: throws an `IllegalArgumentException` if the parameter is null or an empty `String`; if the parameter contains a character other than `M`, `T`, `W`, `H`, `F`, or `A`; and if when the parameter contains an `A`, it is not the only character in the `String`
  * `setCourseTime()`: throws an `IllegalArgumentException` if the `startTime` or `endTime` is not between 0 and `UPPER_TIME` or if the last two digits of the time are greater than or equal to `UPPER_HOUR` (e.g., 1478 would be an invalid time).
  * `getMeetingString()`: Returns a `String` representation of the `Course`  meeting time as outlined in [[UC2, S7]](ws-requirements#uc2-s7) and [[UC3, S1]](ws-requirements#uc3-s1).
  * `hashCode()` and `equals()`: Use Eclipse to generate `hashCode()` and `equals()` on all fields.
  * `toString()`: Returns a comma separated list of `Course` fields in the format expected in [[UC1, S1]](ws-requirements#uc1-s1).
  

### `edu.ncsu.csc216.wolf_scheduler.io`
`CourseRecordIO` provides a set of behaviors that should be available without creating an instance of a class.  Additionally, the methods only rely on the provided parameters and not on any state associated with `CourseRecordIO`.  Therefore, all methods in `CourseRecordIO` are static.  That means any class in the project can access a method in a static way: `CourseRecordIO.readCourseRecords()` and `CourseRecordIO.writeCourseRecords()`.  

**`CourseRecordIO` Methods**

  * `readCourseRecords(String fileName)`: Returns an `ArrayList` of valid `Course`s read from the given file name.  The method throws a `FileNotFoundException` if the given file doesn't exist.
  * `readCourse(String line)`: Returns a `Course` object created by parsing the line of text.  This is a `private` helper method of `readCourseRecords()`.  Since the method is `private`, you are not required to have it in your implementation, but it does simplify the program.
  * `writeCourseRecords(String fileName, ArrayList<Course> courses)`: Writes the given list of `Course`s to the given file.  Throws an `IOException` if unable to write to the file.

### `edu.ncsu.csc216.wolf_scheduler.scheduler`

**`WolfScheduler` Constants & Fields**

  * `catalog`: `ArrayList` of `Course`s that make up the course catalog.
  * `schedule`: `ArrayList` of `Course`s that make up a student's schedule.  This `ArrayList` is a subset of the `catalog`.
  * `title`: `String` representing the schedule's title.

**`WolfScheduler` Constructors**

  * `WolfScheduler(String courseRecordsFileName)`: Initializes `schedule` to an empty `ArrayList` and sets `title` to `My Schedule`.  Initializes the `catalog` `ArrayList` and populates the `Course`s in the catalog from the information in the `courseRecordsFileName`.  Throws an `IllegalArgumentException` if the file cannot be found.

**`WolfScheduler` Methods**

  * `getCourseFromCatalog(String name, String section)`: Uses the `name` and `section` to find a `Course` in the `catalog`.  Returns `null` if the `Course` cannot be found.
  * `addCourse(String name, String section)`: Returns `true` if the `Course` represented by the `name` and `section` are in the `catalog` and can be added to the `schedule` and `false` if the `Course` is not in the `catalog`.  If there is a `Course` with the same `name` already in the `schedule` an `IllegalArgumentException` is thrown.
  * `removeCourse(String name, String section)`: Returns `true` if the `Course` is removed from the `schedule` and `false` otherwise.
  * `resetSchedule()`: Resets the `schedule` to an empty `ArrayList`.
  * `getCourseCatalog()`: Returns a `String[][]` (2D array) that contains a `catalog` item on each row.  The first column is the `Course` `name`, the second is the `section`, and the third is the `title`.
  * `getScheduledCourses()`: Returns a `String[][]` (2D array) that contains a `schedule` item on each row.  The first column is the `Course` `name`, the second is the `section`, and the third is the `title`.
  * `getFullScheduledCourses()`: Returns a `String[][]` (2D array) that contains a `schedule` item on each row.  The first column is the `Course` `name`, the second is the `section`, the third is the `title`, the fourth is the `credits`, the fifth is the `instructorId`, and the sixth is the meeting time `String`.
  * `setTitle(String title)`: Throws an `IllegalArgumentException` if the schedule `title` is null.
  * `getTitle()`: Returns the schedule `title`.
  * `exportSchedule(String fileName)`: Writes the `schedule` to the given file.

### `edu.ncsu.csc216.wolf_scheduler.ui`
[`WolfSchedulerGUI` is provided](../gp1/files/WolfSchedulerGUI.java).


## Guided Project 2
[Guided Project 2](../gp2/) will walk you through the addition of `Event`s to the `WolfScheduler` project, but an overview of the changes from Guided Project 1 are listed below.  Note that all getters and setters for the fields are assumed.  All setters must be implemented so that they do not break any invariants from the requirements (e.g., `Course.setTitle()` should not allow `title` to be set to `null` or empty string).


### `edu.ncsu.csc216.wolf_scheduler.course`
Unless otherwise noted, all constants and fields are `private` and all methods are `public`.  Constants should be `static` and `final`. There are no static methods in the `Activity` hierarchy.

**`Activity` Constants & Fields**
  * `UPPER_TIME`: constant containing the upper military time, which is a value of 2400
  * `UPPER HOUR`: constant containing the upper value for an hour, which is a value of 60
  * `title`: `String` containing the `Course`'s title
  * `meetingDays`: `String` containing the `Course`'s meeting days
  * `startTime`: `int` containing the `Course`'s start time
  * `endTime`: `int` containing the `Course`'s end time
  
**`Activity` Constructors**

  * `Activity(String title, String meetingDays, int startTime, int endTime)`: Sets the fields to the given values or throws an `IllegalArgumentException` if provided an invalid value. 
  
**`Activity` Methods**

  * Each field has a getter, which returns the field.  There is no special logic to any of the getters, so they are not listed individually.
  * `setTitle()`: throws an `IllegalArgumentException` if the parameter is null or an empty `String`.
  * `setMeetingDays()`: sets the `meetingDays` field.
  * `setActivityTime()`: throws an `IllegalArgumentException` if the `startTime` or `endTime` is not between 0 and `UPPER_TIME` or if the last two digits of the time are greater than or equal to `UPPER_HOUR` (e.g., 1478 would be an invalid time).
  * `getMeetingString()`: Returns a `String` representation of the meeting time as outlined in [[UC2, S7]](ws-requirements#gp2-uc2-s7) and [[UC3, S1]](ws-requirements#gp2-uc3-s1).
  * `hashCode()` and `equals()`: Use Eclipse to generate `hashCode()` and `equals()` on all fields.
  * `getShortDisplayArray()`: Abstract method that returns an array of `String`s.
  * `getLongDisplayArray()`: Abstract method that returns an array of `String`s.
  * `isDuplicate()`: Abstract method that returns true if the given `Activity` is a duplicate of this object.


**`Course` Constants & Fields**

  * `SECTION_LENGTH`: constant containing the length of the `section` `String`, which is a value of 3
  * `MAX_NAME_LENGTH`: constant containing the maximum length of the `name` `String`, which is a value of 6
  * `MIN_NAME_LENGTH`: constant containing the minimum length of the `name` `String`, which is a value of 4
  * `MAX_CREDITS`: constant containing the maximum number of credits for a course, which is a value of 5
  * `MIN_CREDITS`: constant containing the minimum number of credits for a course, which is a value of 1
  * `name`: `String` containing the `Course`'s name
  * `section`: `String` containing the `Course`'s section
  * `credits`: `int` containing the `Course`'s credit hours
  * `instructorId`: `String` containing the `Course`'s instructor id
  
**`Course` Constructors**

  * `Course(String name, String title, String section, int credits, String instructorId, String meetingDays, int startTime, int endTime)`: Sets the fields to the given values or throws an `IllegalArgumentException` if provided an invalid value.
  * `Course(String name, String title, String section, int credits, String instructorId, String meetingDays)`: Sets the fields to the given values or throws an `IllegalArgumentException` if provided an invalid value.  The values of `startTime` and `endTime` are set to 0.
  
**`Course` Methods**

  * Each field has a getter, which returns the field.  There is no special logic to any of the getters, so they are not listed individually.
  * `setName()`: a private method that throws an `IllegalArgumentException` if the parameter is null or less than the `MIN_NAME_LENGTH` or greater than the `MAX_NAME_LENGTH`.
  * `setSection()`: throws an `IllegalArgumentException` if the parameter is null or has a length not equal to `SECTION_LENGTH`.
  * `setCredits()`: throws an `IllegalArgumentException` if the parameter is less than `MIN_CREDITS` or greater than `MAX_CREDITS`
  * `setInstructorId()`: throws an `IllegalArgumentException` if the parameter is null or an empty `String`.
  * `setMeetingDays()`: overrides `Activity`'s `setMeetingDays()`. Throws an `IllegalArgumentException` if the parameter is null or an empty `String`; if the parameter contains a character other than `M`, `T`, `W`, `H`, `F`, or `A`; and if when the parameter contains an `A`, it is not the only character in the `String`
  * `hashCode()` and `equals()`: Use Eclipse to generate `hashCode()` and `equals()` on all fields.
  * `toString()`: Returns a comma separated list of `Course` fields in the format expected in [[UC1, S1]](ws-requirements#gp2-uc1-s1) and [[UC3, S2]](ws-requirements#gp2-uc3-s2).
  * `getShortDisplayArray()`: Returns an array of `String`s containing `name`, `section`, `title`, and meeting string
  * `getLongDisplayArray()`: Returns an array of `String`s containing `name`, `section`, `title`, `credits`, `instructorId`, meeting string, and empty string.
  * `isDuplicate()`: Returns true if the given `Activity` is a duplicate of the `Course` by `name`.
  
**`Event` Constants & Fields**

  * `weeklyRepeat`: int that describes how many weeks between events
  * `eventDetails`: `String` containing the event details
  
**`Event` Constructor**

  * `Event(String title, String meetingDays, int startTime, int endTime, int weeklyRepeat, String eventDetails)`: Sets the fields to the given values or throws an `IllegalArgumentException` if provided an invalid value.
  
**`Event` Methods**

  * Each field has a getter, which returns the field.  There is no special logic to any of the getters, so they are not listed individually.
  * `setWeeklyRepeat()`: throws an `IllegalArgumentException` if the parameter is less than one or greater than 4.
  * `setEventDetails()`: throws an `IllegalArgumentException` if the parameter is null.
  * `setMeetingDays()`: overrides `Activity`'s `setMeetingDays()`. Throws an `IllegalArgumentException` if the parameter is null or an empty `String`; if the parameter contains a character other than `S`, `M`, `T`, `W`, `H`, `F`, or `S`.
  * `getMeetingString()`: overrides `Activity`'s `getMeetingString()` and appends " (every X weeks)" where X is the `weeklyRepeat`.
  * `toString()`: Returns a comma separated list of `Event` fields in the format expected in expected in [[UC3, S2]](ws-requirements#gp2-uc3-s2).
  * `getShortDisplayArray()`: Returns an array of `String`s containing empty string, empty string, `title`, and meeting string
  * `getLongDisplayArray()`: Returns an array of `String`s containing empty string, empty string, `title`, empty string, empty string, meeting string, and event details.
  * `isDuplicate()`: Returns true if the given `Activity` is a duplicate of the `Event` by `title`.
  

### `edu.ncsu.csc216.wolf_scheduler.io`
`CourseRecordIO` and `ActivityRecordIO` provide a set of behaviors that should be available without creating an instance of a class.  Additionally, the methods only rely on the provided parameters and not on any state associated with the classes.  Therefore, all methods in `CourseRecordIO` and `ActivityRecordIO` are static.  That means any class in the project can access a method in a static way: `CourseRecordIO.readCourseRecords()` and `ActivityRecordIO.writeCourseRecords()`.  

**`CourseRecordIO` Methods**

  * `readCourseRecords(String fileName)`: Returns an `ArrayList` of valid `Course`s read from the given file name.  The method throws a `FileNotFoundException` if the given file doesn't exist.
  * `readCourse(String line)`: Returns a `Course` object created by parsing the line of text.  This is a `private` helper method of `readCourseRecords()`.  Since the method is `private`, you are not required to have it in your implementation, but it does simplify the program.
  
**`ActivityRecordIO` Methods**
  * `writeCourseRecords(String fileName, ArrayList<Activity> courses)`: Writes the given list of `Activity`s to the given file.  Throws an `IOException` if unable to write to the file.


### `edu.ncsu.csc216.wolf_scheduler.scheduler`

**`WolfScheduler` Constants & Fields**

  * `catalog`: `ArrayList` of `Course`s that make up the course catalog.
  * `schedule`: `ArrayList` of `Activity`s that make up a student's schedule.  This `ArrayList` is a subset of the `catalog` and may also contain `Event`s.
  * `title`: `String` representing the schedule's title.

**`WolfScheduler` Constructors**

  * `WolfScheduler(String courseRecordsFileName)`: Initializes `schedule` to an empty `ArrayList` and sets `title` to `My Schedule`.  Initializes the `catalog` `ArrayList` and populates the `Course`s in the catalog from the information in the `courseRecordsFileName`.  Throws an `IllegalArgumentException` if the file cannot be found.

**`WolfScheduler` Methods**

  * `getCourseFromCatalog(String name, String section)`: Uses the `name` and `section` to find a `Course` in the `catalog`.  Returns `null` if the `Course` cannot be found.
  * `addCourse(String name, String section)`: Returns `true` if the `Course` represented by the `name` and `section` are in the `catalog` and can be added to the `schedule` and `false` if the `Course` is not in the `catalog`.  If there is a `Course` with the same `name` already in the `schedule` an `IllegalArgumentException` is thrown.
  * `addEvent(String eventTitle, String eventMeetingDays, int eventStartTime, int eventEndTime, int eventWeeklyRepeat, String eventDetails)`: throws an `IllegalArgumentException` if the `Event` cannot be constructed or if it is a duplicate of an `Event` already in the `schedule`.  Otherwise, the event is added to the end of the `schedule`.
  * `removeActivity(int idx)`: Returns `true` if the `Activity` is removed from the `schedule` and `false` otherwise.  `IndexOutOfBoundsException`s should be handled in the method or prevented through bounds checks.
  * `resetSchedule()`: Resets the `schedule` to an empty `ArrayList`.
  * `getCourseCatalog()`: Returns a `String[][]` (2D array) that contains a `catalog` item on each row.  The first column is the `Course` `name`, the second is the `section`, the third is the `title`, and the forth is the meeting string.
  * `getScheduledCourses()`: Returns a `String[][]` (2D array) that contains a `schedule` item on each row.  The first column is the `Course` `name`, the second is the `section`,  the third is the `title`, and the forth is the meeting string.  Any item that an object is missing should be an empty string.
  * `getFullScheduledCourses()`: Returns a `String[][]` (2D array) that contains a `schedule` item on each row.  The first column is the `Course` `name`, the second is the `section`, the third is the `title`, the fourth is the `credits`, the fifth is the `instructorId`,  the sixth is the meeting time `String`, and the seventh is the `Event` details.  Any item that an object is missing should be an empty string.
  * `setTitle(String title)`: Throws an `IllegalArgumentException` if the schedule `title` is null.
  * `getTitle()`: Returns the schedule `title`.
  * `exportSchedule(String fileName)`: Writes the `schedule` to the given file.


### `edu.ncsu.csc216.wolf_scheduler.ui`
[`WolfSchedulerGUI` is provided](../gp2/files/WolfSchedulerGUI.java).


## Guided Project 3
The implementation details for GP3 are mostly the same as GP2.  This section will only focus on the differences between GP2 and GP3.


### `edu.ncsu.csc216.wolf_scheduler.course`
Unless otherwise noted, all constants and fields are `private` and all methods are `public`.  Constants should be `static` and `final`. There are no static methods in the `Activity` hierarchy.

**`Conflict`** Interface: 
The `Conflict` interface has a single method:

  * `checkConflict(Activity)`: The method throws the checked `ConflictException` if the possibly conflicting activity (parameter) conflicts with the current activity (`this`).

**`ConflictException`**:
The `ConflictException` is a checked exception.  The default message is "Schedule conflict."

  * `ConflictException(String message)`: Creates an exception with the given message.
  * `ConflictException()`: Creates an exception with the default message.
  
**`Activity`** Updates: 
`Activity` implements the `Conflict` interface and provides the definition of the `checkConflict(Activity)` method for the `Activity` hierarchy.

  * `checkConflict(Activity)`: The method throws the checked `ConflictException` if the possibly conflicting activity (parameter) conflicts with the current activity (`this`).
  

### `edu.ncsu.csc216.wolf_scheduler.scheduler`
Unless otherwise noted, all constants and fields are `private` and all methods are `public`.  Constants should be `static` and `final`. 

**`WolfScheduler`** Updates:
The `addCourse()` and `addEvent()` methods are updated to use the conflict checking functionality in `Activity`.

  * `addCourse()`: if there is a conflict, the `ConflictException` is caught and a new `IllegalArgumentException` is thrown with the appropriate message for the GUI.
  * `addEvent()`: if there is a conflict, the `ConflictException` is caught and a new `IllegalArgumentException` is thrown with the appropriate message for the GUI.
  

### `edu.ncsu.csc216.wolf_scheduler.ui`
[`WolfSchedulerGUI` is provided](../gp2/files/WolfSchedulerGUI.java).  The GUI hasn't changed since GP2.

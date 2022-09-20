---
title: WolfScheduler
description: WolfScheduler Requirements
tags: [software engineering, software lifecycle, CS2, CSC216]
navigation: on
pagegroup: wolf-scheduler
---

# WolfScheduler Requirements
{% include iconHeader.html type="requirements" %}

*[Requirements](../se-overview/requirements)* describe what the system should do, typically from a system or user perspective, without design or implementation details.  The requirements for the **Wolf Scheduler** system are described as *[use cases](../se-overview/requirements#use-cases)*, below:

  * [Use Case 1: Load Course Catalog](#uc1)
  * [Use Case 2: Rename Schedule](#uc2)
  * [Use Case 3: View Course Information](#uc3)
  * [Use Case 4: Add Course to Schedule](#uc4)
  * [Use Case 5: Remove Course from Schedule](#uc5)
  * [Use Case 6: Add Event to Schedule](#uc6)
  * [Use Case 7: Remove Event from Schedule](#uc7)
  * [Use Case 8: Reset Schedule](#uc8)
  * [Use Case 9: Display Final Schedule](#uc9)
  * [Use Case 10: Export Schedule](#uc10)



## <a id="uc1"></a>Use Case 1: Load Course Catalog

Load the catalog of courses so students can make personal schedules for planning.

### Main Flow

  1. The user provides a file containing the listing of courses in the catalog for the upcoming semester.
  2. The system processes the course catalog file line by line and stores valid courses in the system **[[Processing Course Information]](#uc1-e1)** **[[Missing File]](#uc1-a1)**.
  3. The name, section, and title of the courses in the catalog are displayed in a list.
  
### Extensions

  * <a id="uc1-e1"></a>**[Processing Course Information]** Information about scheduled courses are stored in a file with one course record per line.  A course record is a comma separated list of the course name, course title, section number, the number of credit hours, instructor's unity id, meeting days, start time, and end time.  The start time and end time may be omitted if the meeting days are listed as 'A'(rranged).  Valid course records are stored in a list of courses **[[Invalid Course Record]](#uc1-a2)**. A course record is invalid if one or more of the following are true, and an invalid course records is skipped:
     * an item is missing
     * the course name is null or an empty string
     * the course name is contains less than 5 characters or more than 8 characters
	 * the course name does not contain one space between letter characters and number characters
	 * the course name does not start with 1 to 4 letter characters
	 * the course name does not end with three digit characters
     * the course title is null or an empty string
     * the section number is NOT exactly three digits
     * the credit hours are not a number
     * the credit hours are less than 1 or greater than 5
     * the instructor's id is null or an empty string
     * meeting days consist of any characters other than 'M', 'T', 'W', 'H', 'F', or 'A'
	 * meeting days have a duplicate character
     * if 'A' is in the meeting days list, it must be the only character
     * the start time is not between 0000 and 2359 an invalid military time
     * the end time is not between 0000 and 2359 or an invalid military time
     * the end time is less than the start time (i.e., no overnight classes)
     * a start time and/or end time is listed when meeting days is 'A'
     * a course with the same name and section

    An example of what a course schedule file might look like is below:

        
        CSC 116,Intro to Programming - Java,001,3,jdyoung2,MW,0910,1100
        CSC 116,Intro to Programming - Java,002,3,spbalik,MW,1120,1310
        CSC 116,Intro to Programming - Java,003,3,tbdimitr,TH,1120,1310
        CSC 216,Programming Concepts - Java,001,4,sesmith5,TH,1330,1445
        CSC 216,Programming Concepts - Java,002,4,jtking,MW,1330,1445
        CSC 216,Programming Concepts - Java,601,4,jep,A
  
### Alternative Flows

  * <a id="uc1-a1"></a>**[Missing File]** If the file does not exist on the system, an error message, "Cannot find file." is displayed and the user is re-prompted for a file.
  * <a id="uc1-a2"></a>**[Invalid Course Record]** An invalid course record is ignored and not added to the list of courses stored by the system.


## <a id="uc2"></a>Use Case 2: Rename Schedule

The student changes the schedule's title from the default name of "My Schedule".  The student can provide a new title for their schedule or leave the title empty.

### Main Flow

  1. The user replaces the current schedule title with a new name
  2. The user saves the new schedule title
  3. The system sets the title of the schedule to the submitted text **[[Invalid Title]](#uc2-a1)**
  
### Alternative Flows

  * <a id="uc2-a1"></a>**[Invalid Title]**: The system displays a message stating "Invalid title.".  The student clicks OK and is returned to the main user interface with no change.

## <a id="uc3"></a>Use Case 3: View Course Information

The student selects a course from the catalog to see all the information about the course.

### Main Flow

  1. The student selects a course in the catalog.
  2. The course details are displayed with the course name, section, title, instructor, credit hours, and meeting information. If the meeting days are “A”, the details view shows “Arranged”. Otherwise, the meeting information shows the meeting days followed by the start time in standard time (e.g., 1:30PM), a dash, and the end time in standard time. Only “AM” and “PM” are used.
  

## <a id="uc4"></a>Use Case 4: Add Course to Schedule

The student adds a course from the course catalog into their schedule.

### Main Flow

  1. The student selects the desired course to add from the course catalog.
  2. The student clicks the add course button.
  3. The system updates the schedule to include the selected course **[[Already Added]](#uc3-a1)** **[[Schedule Conflict]](#uc3-a2)**

  
### Alternative Flows

  * <a id="uc3-a1"></a> **[Already Added]**: If the student has already added a course with the same name to their schedule (the same section or a different section), a pop-up message stating “You are already enrolled in ." is displayed, where is replaced with the name of the course. The student clicks OK and is returned to their schedule with no change.
  * <a id="uc3-a2"></a> **[Schedule Conflict]**: If the course conflicts with another course or event (meaning there is an overlap of at least one day and time, even by the same minute) on the student’s schedule, a pop-up message stating “The course cannot be added due to a conflict.” is displayed. The student clicks OK and is returned to their schedule with no change.



## <a id="uc5"></a>Use Case 5: Remove Course from Schedule

The student removes a course from their current schedule.

### Main Flow

  1. The student selects the desired course to remove from their schedule.
  2. The student clicks the remove course button.
  3. The system updates the schedule to remove the selected course **[[No Selected Course]](#uc4-a1)**

  
### Alternative Flows

  * <a id="uc4-a1"></a> **[No Selected Course]**: If no course is selected in the student’s schedule, a pop-up message stating “No item selected in the schedule.” is displayed. The student clicks OK and is returned to their schedule with no change.
  
  


## <a id="uc6"></a>Use Case 6: Add Event to Schedule

The student can add non-course events to their schedule so they can visualize how their time will be managed with classes and other obligations.

### Main Flow

  1. The student clicks the button to add an event.
  2. The system displays the new event dialog.
  3. The student enters the event title, days of the week (Sunday through Saturday), start time, end time, and optional event details.
  4. The student clicks the add event button.
  5. The system updates the schedule to add a new event with the provided details. **[[Event Exists]](#uc5-a1)** **[[Schedule Conflict]](#uc5-a2)** **[[Missing Name]](#uc5-a3)** **[[Missing Times]](#uc5-a4)** **[[Missing Days]](#uc5-a5)**

  
### Alternative Flows

  * <a id="uc5-a1"></a> **[Event Exists]**: If the student has already added an event with the same title to their schedule, a pop-up message stating “You have already created an event called ." is displayed, where is replaced with the title of the event. The student clicks OK and is returned to the event editing information that is populated with earlier values for editing.
  * <a id="uc5-a2"></a> **[Schedule Conflict]**: If the event conflicts with another course or event (meaning there is an overlap of at least one day and time, even by the same minute) on the student’s schedule, a pop-up message stating “The event cannot be added due to a conflict.” is displayed. The student clicks OK and is returned to the event editing information that is populated with earlier values for editing.
  * <a id="uc5-a3"></a> **[Missing Name]**: If the event name is null or an empty string, a pop-up message stating “Invalid title.” is displayed. The student clicks OK and is returned to the event editing information that is populated with earlier values for editing.
  * <a id="uc5-a4"></a> **[Missing Times]**: If the event start time or end time is empty, an invalid time, or if the end time is earlier than the start time, a pop-up message stating “Invalid meeting days and times.” is displayed. The student clicks OK and is returned to the event editing information that is populated with earlier values for editing.
  * <a id="uc5-a5"></a> **[Missing Days]**: If no day of week is selected, a pop-up message stating “Invalid meeting days and times.” is displayed. The student clicks OK and is returned to the event editing information that is populated with earlier values for editing.



## <a id="uc7"></a>Use Case 7: Remove Event from Schedule

The student removes non-course events to their schedule.

### Main Flow

  1. The student selects an event from their schedule
  2. The student clicks the remove event button.
  3. The system updates the schedule to remove the selected **[[No Selected Event]](#uc6-a1)**

  
### Alternative Flows

  * <a id="uc6-a1"></a> **[No Selected Event]**: If no event is selected in the student’s schedule, a pop-up message stating “No item selected in the schedule.” is displayed. The student clicks OK and is returned to their schedule with no change.


## <a id="uc8"></a>Use Case 8: Reset Schedule

The student clears their schedule and resets it to its defaults.

### Main Flow

  1. The student clicks the reset schedule button.
  2. The system removes all events and courses from the schedule and changes the title of the schedule to the default “My Schedule”



## <a id="uc9"></a>Use Case 9: Display Final Schedule

The student displays their final schedule with all information about the scheduled activities.

### Main Flow

  1. The student clicks the display schedule button.
  2. The student sees the list of scheduled courses and events with columns for name, section, title, instructor, credit hours, meeting information, and description. If the meeting days are "A", the details view shows "Arranged".  Otherwise, the meeting information shows the meeting days followed by the start time in standard time (e.g., 1:30PM), a dash, and the end time in standard time.  Only "AM" and "PM" are used.  If the row is an event, then the name, section, instructor, and credit hours are left blank.  After the table, the total number of credit hours is listed for the given schedule.
  3. The student clicks the revise schedule button to return to the schedule editing functionality.
  
## <a id="uc10"></a>Use Case 10: Export Schedule

The student exports their schedule to a text file for future reference.

### Main Flow

  1. The student clicks the display schedule button.
  2. The student clicks the export schedule button.
  3. The student is prompted with a file dialog where they can provide a location and file name for saving the schedule.
  3. The schedule is stored in a text file with a comma-separated list of courses and events with an ordering of information as follows: **[[Error Saving]](#uc9-a1)**.
     * Course: name,section,title,credits,instructor,meetingDays[,startTime,endTime]
     * Event: title,meetingDays,startTime,endTime,details

  
### Alternative Flows

  * <a id="uc9-a1"></a> **[Error Saving]**: If the file cannot be saved, a pop-up message stating "The file cannot be saved." is displayed.  The student clicks OK and is returned to the file saving dialog.

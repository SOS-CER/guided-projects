---
title: Guided Project 1 - Software Development Practices and Tools
tags: [software engineering, software lifecycle, CS2, CSC216, GP1]
description: Independent Task - Finish `Course`
navigation: on
pagegroup: gp1
---
 
# Independent Task: Finish `Course`
{% include iconHeader.html type="task" %}
Using the `WolfScheduler` [requirements](../wolf-scheduler/ws-requirements) along with the [provided JUnit tests](files/CourseTest.java), you will finish implementing the `Course` class to pass the tests!

There are seven setter methods (you'll see why it is seven shortly) and one getter method that need to be fully implemented to pass all of the provided JUnit tests.  The implementation details below provide additional details about how to implement the WolfScheduler [requirements](../wolf-scheduler/ws-requirements) and will help you pass the test cases.  Note that when a method receive an invalid value in a parameter, you want to throw an `IllegalArgumentException`.  That way the client can catch and handle the error.

You'll walk through an example of implementing `setName()` before leaving the other methods for independent implementation.  The other methods will review prerequisite concepts.

{% capture callout_content %}
  * Write setter methods for `Course` to pass the unit tests and meet the requirements.
{% endcapture %}
{% include callout.html content=callout_content type="learningOutcomes" icon="objective" title="Learning Outcomes" %}
  
{% capture callout_content %}
Test driven development is a software development practice where you write your test cases for a class using the requirements BEFORE you write the code for the class.  The failing tests then drive the development of your class!  You keep fixing your code until your tests pass.

The teaching staff has provided a set of unit tests that you must now pass!

In TDD practice, you may not always write your test cases first. Iterating between code and test (and not putting off testing) is critical for writing high quality code!
{% endcapture %}
{% include callout.html content=callout_content icon="ttTool" type="bestPractices" title="Best Practice: Test Driven Development (TDD)" %}

## Constants
In the [Guided Project 1 design](../wolf-scheduler/ws-design.html#guided-project-1-design) there are several constants listed for the `Course` class.  Constants are used to provide names, and therefore meaning, to values in our programs that do not change.  Add the constant values to `Course` and then use the constant values where appropriate.  Remember that constants are `static` and `final`.  These constants should also be `private` as indicated by the red square in the UML diagram.  See the Conceptual Knowledge block about UML Class Diagrams and Notation for more information.

Comment your constants using Javadoc!

{% capture callout_content %}
We use a Unified Modeling Language (UML) Class Diagram to provide a visual representation of our design.  Class diagram show the classes, their fields, and methods.  Class diagrams also show the connection or relationships between classes.  By interpreting the icons and information in the class diagram we can create a code skeleton of the classes, fields, and methods for our program.  We'll use the information in the `Course` class box to create our constants.

The constants are in the middle portion of the `Course` box, which is labeled as part of the `edu.ncsu.csc216.wolf_scheduler.course` package.  The constants are noted in the left portion of each line by the red outline of a square labeled with an 'S' in the upper left corner and 'F' in the upper right corner.  We interpret the red outline of a square as the keyword `private`.  The 'S' represents `static`.  The 'F' represents `final`.  The name of the constant is next; an example is `SECTION_LENGTH`.  This if followed by the type of `int` and the value it is assigned of `3`.  We would interpret the line in code as `private static final int SECTION_LENGTH = 3;`.  

The other icons in the class diagram tell use different things.  The outlines of circles, squares, and triangles represent fields.  The solid circle, squares, and triangles represent methods.  Green circles are public, red squares are private, and yellow triangles are protected.  'S' is static, 'F' is final, 'C' is a constructor.  

The lines connecting the classes represent fields.  We'll discuss those in further detail when we get to the `WolfScheduler` class.
{% endcapture %}
{% include callout.html content=callout_content icon="dnTool" type="conceptualKnowledge" title="Conceptual Knowledge: UML Class Diagrams and Notation" %}

## Provided Tests
The teaching staff tests have been provided for you.  **The provided tests should NOT change in any way.**  Be careful that you are not using Eclipse Quick Fixes that might change the provided tests.

The automated grading system (this will be explained in much more detail later) will overwrite your copy of the tests with the teaching staff version.  If you changed the provided tests then your code may not compile when you look at the automated grading system feedback.  For now, try to avoid changing the provided tests.  There will be information about resolving any issues when you reach the section of the Guided Project on automated grading.

## Implement `Course` Methods

Now that we have our constants, fields, and constructors set up, we need to implement the `Course` class' methods to meet the requirements defined in [Use Case 1: Load Course Catalog](../wolf-scheduler/ws-requirements#uc1). While Use Case 1 defines the information about how to load a file with course schedule information, the list of what makes a course record in the file invalid helps us determine the implementation of the `Course` object.  We want to define `Course` so that if any of these invalid field characteristics are passed in as parameters, we can let the client (or class that is working with `Course` objects) know that there is a problem.  We will notify the clients' of `Course` about the problem by throwing exceptions!

{% capture callout_content %}
Exceptions are objects that we can throw to let a calling method (or the client of your method) know about a problem.  By throwing an exception to a client when your method can no longer execute, you are letting the client determine how to handle the problem in that class' context.  

When we want to throw an exception, we must first construct it and then use the `throw` keyword to send the exception to the caller (see line 9 in the code snippet below).  When we see the `throw` keyword, the flow of control switches from the current method to the caller (if an exception is throw in `setInfo()`, the flow of control would switch back to line 19 and immediately transfer to the first enclosing `catch` block).  If the caller doesn't catch or handle the exception, then the exception propagates to the the next caller.  If an exception is never caught, then program execution will end.  

```java
/**
 * An example of throwing an exception.
 * @param info additional information for the instance of a class
 * @throws IllegalArgumentException when the parameter info is null or an empty string
 */
public void setInfo(String info) {
   if ( /* something is wrong with info */ ) {
      // error path - info is null or an empty string
      throw new IllegalArgumentException(); // construct the exception and throw
   }
   // continue with happy path
}

/**
 * The calling class - it's calling a method that may thrown an exception
 */
public void processInfo() { // note that this method could be in another class, including a test class!
   try { // wrap around code that may throw an exception
      String s = setInfo();
      // continue with happy path
   } catch (IllegalArgumentException e) {
      // handle exception
   }
}
```

Best practice is to catch and handle exceptions rather than let them escape and stop program execution, but you don't want to wrap all your code in `try/catch` blocks.  There's a balance to working with exceptions.  If your code is trying things that are likely to throw an exception, then wrap in a `try/catch`.  Otherwise, if the exception is unchecked, meaning that you are not required to handle it for compilation, you could chose not to explicitly try to catch the exception.

You should always provide documentation about exceptions that your method might throw to help clients identify if they should catch a possible exception.  Use the `@throws` tag to document.  You can also describe error paths in the main comment body.

{% endcapture %}
{% include callout.html content=callout_content icon="plTool" type="conceptualKnowledge" title="Conceptual Knowledge: Exceptions" %}
 
 

### Implement `setName()` 
From [UC1, Processing Course Information](../wolf-scheduler/ws-requirements#uc1-e1), you need to implement `setName()` to meet the following the description:

{% capture callout_content %} 
A course record is invalid if one of more of the following are true:

   * the course name is null or an empty string
   * the course name is contains less than 5 characters or more than 8 characters
   * the course name does not contain one space between letter characters and number characters
   * the course name does not start with 1 to 4 letter characters
   * the course name does not end with three digit characters
{% endcapture %} 
{% include callout.html content=callout_content icon="requirements" type="reminder" title="Requirements: `Course` Name" %}


{% capture reminder-content %} 
By describing valid and invalid names, we are starting to identify tests to ensure that our method is implemented correctly.  We have a test method that considers valid names (e.g., `testSetNameValid()`) and a test method that considers invalid names (e.g., `testSetNameInvalid()`).
{% endcapture %} {% include mention.html content=reminder-content type="reminder" title="Note: Testing Basics"%} 
The requirements describe the characteristics for a course name.  For example, "CSC 216" would be valid, but "CSC216" would not be because there is no space.  Other valid and invalid examples are provided below.  The provided test cases provide additional examples.

  * Valid names: "E 115", "CSC 116", "MA 141", "HESF 101" 
  * Invalid names (with reasons invalid)
     * `null` - cannot be null
	 * "" - cannot be empty string
	 * "E 11" - length less than 5, incorrect number of digits
	 * "HESFQ 101" - prefix has too many characters
     * "101" - length less than 5, no leading characters, no space
	 * "CSC 21" - less than 3 digits
	 * "CSC\t216" - no space


{% capture reminder-content %} 
When processing the name, you will need to look at individual characters.  You can get a character from a `String` at index `i` using the `String.charAt(i)` method.  

Once you have a character, you can use the methods of the `Character` class to determine if the character is a letter (`Character.isLetter(c)`) or a digit (`Character.isDigit(c)`). 

For the implementation of `setName()` you will need to compare directly with the ` ` (space) character.  Using `Character.isWhitespace(c)` considers more than just a space!  Luckily, we have a test to ensure that you're not using `Character.isWhitespace(c)`.
{% endcapture %} {% include mention.html content=reminder-content type="reminder" title="Reminder: Characters and the `Character` Class"%}
There are several checks that we need to consider to implement `setName()`.  You should consider them one or two at a time rather than in one big if statement.  The one big if statement is harder to debug! Also, by considering one or two checks at a time, we can customize our error messages.  The pseudocode below shows one possible implementation of `setName()`.  

**Implementation Considerations**

*Constants*
  * MIN_NAME_LENGTH
  * MAX_NAME_LENGTH
  * MIN_LETTER_COUNT
  * MAX_LETTER_COUNT
  * DIGIT_COUNT

*Exception Messages*
  * "Invalid course name." 
     - if `name` is `null` 
     - if length is incorrect
     - if name structure is incorrect

*Testing*
  * Run your tests and make sure that `testSetNameValid()` and `testSetNameInvalid()` passes.
  * All previously passing tests should continue to test

```java
/**
 * Sets the Course's name.  If the name is null, has a length less than 5 or more than 8,
 * does not contain a space between letter characters and number characters, has less than 1
 * or more than 4 letter characters, and not exactly three trailing digit characters, an
 * IllegalArgumentException is thrown.
 * @param name the name to set
 * @throws IllegalArgumentException if the name parameter is invalid
 */
private void setName(String name) {
    //Throw exception if the name is null
    if name is null
        throw new IllegalArgumentException("Invalid course name.");

    //Throw exception if the name is an empty string
    //Throw exception if the name contains less than 5 character or greater than 8 characters
    if name's length is less than MIN_LENGTH or name's length is more than MAX_LENGTH
        throw new IllegalArgumentException("Invalid course name.");

    //Check for pattern of L[LLL] NNN
    initialize counter for number of letters
    initialize counter for number of digits
    initialize boolean flag for finding a space to false
    for each character in name
        if a space has not yet been found
            if the character at i is a letter
                increment the letter counter
            else if the character at i is a space
                space flag should be set to true
            otherwise
                throw new IllegalArgumentException("Invalid course name.");
        else if a space is found
            if the character is a digit
                increment the digit counter
            otherwise
                throw new IllegalArgumentException("Invalid course name.");
    
    //Check that the number of letters is correct
    if letter counter is less than one or more than 4
        throw new IllegalArgumentException("Invalid course name.");
    
    //Check that the number of digits is correct
    if digit counter is not 3
        throw new IllegalArgumentException("Invalid course name.");
    
    set this.name (field) to name (parameter)
}
```   
  

    

### Implement `setTitle()` 
From the requirements for [UC1, Processing Course Information](../wolf-scheduler/ws-requirements#uc1-e1), you need to implement `setTitle()` to meet the following:

{% capture callout_content %} 
A course record is invalid if one of more of the following are true:

  * the course title is null or an empty string
{% endcapture %} 
{% include callout.html content=callout_content icon="requirements" type="reminder" title="Requirements: `Course` Title" %}

There are two possible conditionals to check for a problem:

```java
//Conditional 1:
if (title == null || "".equals(title)) { ... }

//Conditional 2:
if (title == null || title.length() == 0) { ... }
```

Both conditionals check if `title` is `null` using `==`, which is appropriate when doing `null` checks.  

Conditional 1 checks for equality of the `title` with the empty string.  Since `String`s are objects, we must use `.equals()` to check for equality.  Additionally, we put the string literal of `""` first because a string literal will never be null and the convention is put string literals first.  If you swap the order, you'll get a CheckStyle notification!

Conditional 2 checks the length of the `title` string.  If the length is zero, the string is empty.

**Implementation Considerations**

*Exception Messages*
  * "Invalid title." - if `title` is `null` or empty string

*Testing*
  * Run your tests and make sure that `testSetTitleValid()` and `testSetTitleInvalid()` passes.
  * All previously passing tests should continue to test

 
### Implement `setSection()` 
From the requirements for [UC1, Processing Course Information](../wolf-scheduler/ws-requirements#uc1-e1), you need to implement `setSection ()` to meet the following

{% capture callout_content %} 
A course record is invalid if one of more of the following are true:

  * the section number is NOT exactly three digits
{% endcapture %} 
{% include callout.html content=callout_content icon="requirements" type="reminder" title="Requirements: `Course` Section" %}

Section numbers can start with a leading zero, so `section` is a `String`.  That means that `section` cannot be `null`.  Remember that you can use the [`Character`](https://docs.oracle.com/javase/8/docs/api/java/lang/Character.html) class methods to help you with determining if a character is a digit.  

**Implementation Considerations**

*Constants*
  * SECTION_LENGTH

*Exception Messages*
  * "Invalid section." 
     - if `section` is `null` or not three characters
     - if any of `section`'s three characters are not digits

*Testing*
  * Run your tests and make sure that `testSetSectionValid()` and `testSetSectionInvalid()` passes.
  * All previously passing tests should continue to test

 
### Implement `setCredits()` 
From the requirements for [UC1, Processing Course Information](../wolf-scheduler/ws-requirements#uc1-e1), you need to implement `setCredits()` to meet the following:

{% capture callout_content %} 
A course record is invalid if one of more of the following are true:

  * the credit hours are not a number
  * the credit hours are less than 1 or greater than 5
{% endcapture %} 
{% include callout.html content=callout_content icon="requirements" type="reminder" title="Requirements: `Course` Credits" %}
 
You actually don't need a specific test here to check if the credit hours are not a number.  The parameter type of `int` guarantees that the value will be a number.  But later on, you will need to handle this case.

**Implementation Considerations**

*Constants*
  * MIN_CREDITS
  * MAX_CREDITS

*Exception Messages*
  * "Invalid credits." - if `credits` is out of bounds

*Testing*
  * Run your tests and make sure that `testSetCreditsValid()` and `testSetCreditsInvalid()` passes.
  * All previously passing tests should continue to test

 
### Implement `setInstructorId()` 
From the requirements for [UC1, Processing Course Information](../wolf-scheduler/ws-requirements#uc1-e1), you need to implement `setInstructorId()` to meet the following:

{% capture callout_content %} 
A course record is invalid if one of more of the following are true:

  * the instructor's id is null or an empty string
{% endcapture %} 
{% include callout.html content=callout_content icon="requirements" type="reminder" title="Requirements: `Course` Instructor" %}

Run your tests and make sure that `testSetInstructorIdValid()` and `testSetInstructorIdInvalid()` passes.

**Implementation Considerations**

*Exception Messages*
  * "Invalid instructor id." - if `instructorId` is `null` or empty string

*Testing*
  * Run your tests and make sure that `testSetInstructorIdValid()` and `testSetInstructorIdInvalid()` passes.
  * All previously passing tests should continue to test
 
### Implement `setMeetingDaysAndTime()` 
From the requirements for [UC1, Processing Course Information](../wolf-scheduler/ws-requirements#uc1-e1), you need to implement a method in the `Course` class to meet the following:

{% capture callout_content %} 
A course record is invalid if one of more of the following are true:

  * meeting days consist of any characters other than 'M', 'T', 'W', 'H', 'F', or 'A'
  * meeting days have a duplicate character
  * if 'A' is in the meeting days list, it must be the only character
  * the start time is not between 0000 and 2359 an invalid military time
  * the end time is not between 0000 and 2359 or an invalid military time
  * the end time is less than the start time (i.e., no overnight classes)
  * a start time and/or end time is listed when meeting days is 'A'
{% endcapture %} 
{% include callout.html content=callout_content icon="requirements" type="reminder" title="Requirements: `Course` Meeting Days and Time" %}

We're going to interpret the requirements in the following way.  If the meeting days for the `Course` is arranged (e.g., `"A"`), then `startTime` and `endTime` should be 0.  If the meeting days for `Course` are not arranged, then there MUST be a valid `startTime` and `endTime`.  We could create separate setters for each, but there are too many dependencies and considerations.  Instead, we will create a single method to ensure the changes are consistent with all three values.

Before you start your method implementation, do the following:

  * Remove `setMeetingDays()`
  * Remove `setStartTime()`
  * Remove `setEndTime()`
  * Create a method `public void setMeetingDaysAndTime(String meetingDays, int startTime, int endTime)`
  * Comment the method to describe the functionality.
  * Update the Course constructor to use the new method
  * Uncomment the method in `CourseTest` called `testSetMeetingDaysAndTimesValid()` 
  * Uncomment the method in `CourseTest` called `testSetMeetingDaysAndTimesInvalid()`
  
This method can have lots of decision points, so pseudocode is provided to get you started on the problem.  There are multiple ways to implement this method; you do not need to implement is as per the pseudocode. 

To make the method easier to understand and to reduce redundancy, you may want to create helper methods to break out some of the work.  If you create helper methods, they must be `private`!  


**Implementation Considerations**

*Hint*
  * When working with military time as an integer, you can get the hours by dividing by 100 and the minutes by mod-ing by 100.

*Constants*
  * UPPER_HOUR
  * UPPER_MINUTE

*Exception Messages*
  * "Invalid meeting days and times." 
      - if meeting days is null, empty, or contains invalid characters
	  - if an arranged class has non-zero start or end times
      - if start time is an incorrect time
      - if end time is an incorrect time
      - if end time is less than start time
  
*Comments*
  * Comment the method, including all parameters.

*Testing*
  * Run your tests and make sure that `testSetMeetingDaysAndTimeValid()` and `testSetMeetingDaysAndTimeInvalid()` passes.
  * All previously passing tests should continue to test

```java
// TODO - Add Javadoc here!
public void setMeetingDaysAndTime(String meetingDays, int startTime, int endTime) {
   if meetingDays is null or empty string
      throw IAE("Invalid meeting days and times.") // IAE = IllegalArgumentException

   if meetingDays is "A" // Arranged
      if startTime is NOT 0 OR endTime is NOT 0
	     throw IAE("Invalid meeting days and times.")
      set meetingDays to the parameter; startTime and endTime to 0
	  
   otherwise //not arranged
      create local variables to hold the counts for each weekday letter
	  for all characters in meetingDays
	     increment weekday letter counter if you find the letter // this will take several lines of code 
		 if any invalid letters
		    throw IAE("Invalid meeting days and times.")
	
	  if any weekday letter counts are more than one // checks for duplicates
	     throw IAE("Invalid meeting days and times.")
		 
	  break apart startTime and endTime into hours and minutes //several lines of code
	  
	  if startHour is invalid // not between 0 and 23, inclusive
	     throw IAE("Invalid meeting days and times.")
	
	  if startMin is invalid // not between 0 and 59, inclusive
	     throw IAE("Invalid meeting days and times.")
	  
	  if endHour is invalid // not between 0 and 23, inclusive
	     throw IAE("Invalid meeting days and times.")
	
	  if endMin is invalid // not between 0 and 59, inclusive
	     throw IAE("Invalid meeting days and times.")
	
	  //everything is valid and works together!
	  set fields for meetingDays, startTime, and endTime
}
```
 
### Implement `getMeetingString()` 
[UC 3: View Course Information](../wolf-scheduler/ws-requirements#uc3) and [UC 9: Display Final Schedule](../wolf-scheduler/ws-requirements#uc9) both discuss providing meeting information as a string in standard time format rather than in military format.  The `getMeetingString()` method provides this functionality.  

To get started, do the following:

  * Create a method `public String getMeetingString()`
  * Uncomment the method in `CourseTest` called `testGetMeetingString()`

To make the method easier to understand and to reduce redundancy, you may want to create helper methods to break out some of the work.  If you create helper methods, they must be `private`!  The teaching staff solution has a helper method, `getTimeString(int time)`, to convert military time to standard time.
  


**Implementation Considerations**

*Hints*
  * When working with military time as an integer, you can get the hours by dividing by 100 and the minutes by mod-ing by 100.
  * If the hour is military time is over twelve, subtract 12 to convert to standard time hours (PM).
  * If the hour in military time is 0, the hour is 12 (AM) in standard time.
  * Minutes less than ten will need a leading '0' character concatenated to the minute value when building the `String` to return.

*Comments*
  * Comment the method, including all parameters.

*Testing*
  * Run your tests and make sure that `testGetMeetingString()` passes.
  * All previously passing tests should continue to test


## Testing and Debugging
At this time, all tests should be passing with a green bar! (You should make sure that you didn't change the teaching staff tests.  You can copy of the test file again to ensure there are no changes.)

{% include image.html file="images/PassingCourseTests.PNG" caption="Figure: JUnit Results" %} 

If you have failing tests, that's ok! The tests are there to help you find problems in your code.  By working incrementally and using test-driven development, that keeps us from implementing too much of our project before finding fundamental problems.  If the `Course` class doesn't work, a list of `Course`s won't work.

There are several ways to debug your code.  You can trace your code via pencil and paper. Start with the failing test and keep track of how the variables change as you move through each statement.  You can also add print statements to your code and execute each test to see how the values change.  If you want to run a single test, you can right click on that test in the JUnit results view and select **Run**.  That will help you narrow down to a single problem. 

{% capture callout_content %}
For additional help, ask a question on Piazza or come to office hours.  When asking a question, please do the following:

  * Push all your source and test code to GitHub, even if it's not working.  The teaching staff can take a look.
  * Provide a link to your GitHub repository in the question.
  * Provide the name of the test method that is failing and provide the specific line number of the failure. 
  * Provide the expected and actual output from the test.
  * Provide a explanation of why you think the test is failing.
{% endcapture %}
{% include callout.html content=callout_content icon="reminder" type="bestPractices" title="Best Practice: Ask for Help on Piazza or in Office Hours" %}



## Requirements and Object Design
You may have noticed that there are two statements in [UC1, Processing Course Information](../wolf-scheduler/ws-requirements#uc1-s1) that you have not yet fully written code for:

A course record is invalid if one or more of the following are true:

  * an item is missing
  * a course with the same name and section
  
You do a basic check for null or empty string items that helps with the "an item is missing" statement, but there is more that will need to be done there when you handle processing the lines of `Course` information from an input file.  

For the requirement that a course record is invalid if "a course with the same name and section" already exists in the catalog isn't something that you can implement at this point.  A `Course` only knows about itself; not about other `Course`s in the system.  You'll implement that statement when you start working with a collection of `Course`s.

{% capture callout_content %}
A requirement describes what the system must do.  Use cases describe the system's behaviors from the context of a user of the system.  When the user interacts with a system, they are not interacting with a specific object, instead, they are interacting with several objects.  When designing systems from requirements, a single object may describe the behavior of part of a single use case or parts of many use cases.  Part of system design is identifying the objects that are necessary in the system and the relationships between those objects.  
{% endcapture %}
{% include callout.html content=callout_content icon="requirements,design" type="conceptualKnowledge" title="Conceptual Knowledge: Requirements & Object Design" %}
  


{% capture reminder-content %} 
GitHub Resources:

  * [Staging Files](https://pages.github.ncsu.edu/engr-csc-software-development/practices-tools/git/git-staging)
  * [Committing Files](https://pages.github.ncsu.edu/engr-csc-software-development/practices-tools/git/git-commit)
  * [Pushing Files](https://pages.github.ncsu.edu/engr-csc-software-development/practices-tools/git/git-push)
  
Static Analysis Resources:

  * [Setting up and running the tools on your project](gp1-static-analysis)
{% endcapture %} {% include mention.html content=reminder-content type="reminder" title="Reference: Staging and Pushing to GitHub"%} 
## Check Your Progress
{% include iconHeader.html type="glance" %}
You've made a lot of changes to your `Course` class by implementing the required functionality to pass the provided test cases.  Before moving on to the next portion of the Guided Project, complete the following tasks:

  - [ ] Make sure that all constants, fields, methods, and constructors are commented.
  - [ ] Resolve all static analysis notifications.
  - [ ] Fix test failures.  DO NOT CHANGE THE PROVIDED TEST CODE!
  - [ ] Commit and push your code changes with a meaningful commit message. For example, "[Implementation][Test] Completed Course functionality".

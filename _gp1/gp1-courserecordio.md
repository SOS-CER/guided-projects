---
title: Guided Project 1 - Software Development Practices and Tools
tags: [software engineering, software lifecycle, CS2, CSC216, GP1]
description: Independent Task - Finish `CourseRecordIO`
navigation: on
pagegroup: gp1
---
 
# Independent Task: Finish `CourseRecordIO`
{% include iconHeader.html type="task" %}
Now that we have the basic outline of `CourseRecordIO` you'll implement the `readCourse()` method to process a single line from the input file and create an instance of the `Course` class. A correct implementation will pass the tests in `CourseRecordIOTest`.  As part of our implementation of `readCourse()`, we'll discuss how to test file I/O.

{% capture callout_content %}
  * Implement `CourseRecordIO.readCourse()`
{% endcapture %}
{% include callout.html content=callout_content icon="objective" type="learningOutcomes" title="Learning Outcomes" %}
 
## Implement `CourseRecordIO.readCourse()`
To finish the `CourseRecordIO` class and pass all of the `CourseRecordIOTest`s, you need to implement `CourseRecordIO.readCourse()`.  The method receives a `String` which is a line from the input file. An example line might be:

```
CSC 116,Intro to Programming - Java,001,3,jdyoung2,MW,0910,1100
```

or 

```
CSC 216,Software Development Fundamentals,601,3,jctetter,A
```


You can use a `Scanner` to process the `String` parameter.   You must break the line up into *tokens* by using the comma character (e.g., `','`) as a delimiter.   A *delimiter* is a string that is used to separate or break apart a larger string.  The default delimiter for `Scanner` is white space.  You can change the delimiter using the `Scanner.useDelimiter()` method.  After updating the delimiter, any call to `Scanner.next()` will return the token before the next delimiter.  So for our example,

```
CSC 216,Software Development Fundamentals,601,3,jctetter,A
```

the first call to `Scanner.next()` would return a string `"CSC 216"`, the second call to `Scanner.next()` would return a string `"Software Development Fundamentals"`, etc.  When reading the values for credits, startTime, or endTime, you can use `Scanner.nextInt()`.

Once you break the line into tokens, you can construct a `Course` object and return it from the method.


There are two places where code that you work with may lead to an exception for invalid values in the input string:

  * `NoSuchElementException` or `InputMismatchException`: if you receive these when processing the input, catch them and throw an `IllegalArgumentException` to the caller (which in this case is `CourseRecordIO.readCourseRecords()`).
  * `IllegalArgumentException`: when constructing a `Course` with invalid values, the `Course` class will throw an `IllegalArgumentException`.  In this case *DO NOT* catch the exception!  Instead, let the exception propagate to the caller (which in this case is `CourseRecordIO.readCourseRecords()`)

Use the fields and constructors of the `Course` class to help you determine what type each token should be.  The tokens will always be in the order of:

```
name,title,section,creditHours,instructor,meetingDay,startTime,endTime
```

or 

```
name,title,section,creditHours,instructor,A
```

If the meeting days string is NOT "A", then you'll need to read in the last two tokens.  If there are any additional tokens after the expected last one, an `IllegalArgumentException` should be thrown.

The high level structure of the method is provided in the pseudocode, below.  You do not have to implement the method this way, but it will be useful for getting started.

```java
//TODO - Add Javadoc here!
private static Course readCourse(String line) {
   construct Scanner to process the line parameter
   set the delimiter to ","
   
   try {
      read in tokens for name, title, section, credits, instructorId, and meetingDays and store in local variables
	  
      if meetingDays is "A"
         if there are more tokens
            throw IAE
         otherwise
         return a newly constructed Course object
      
      otherwise
      read in tokens for startTime and endTime
      if there are more tokens
         throw IAE
      return a newly constructed Course object
   } catch any exceptions and throw a new IllegalArgumentException
   
   //Remember to close the scanner on all possible paths out of the method - that's not in the pseudocode
}
```

Make sure that all your tests are passing before continuing with the Guided Project!

## File I/O Testing Overview
Let's take a quick look at the `CourseRecordIOTest` class to discuss how we are testing `CourseRecordIO`.

There are three test methods and a private helper method.  

Two of the test methods test the `CourseRecordIO.readCourseRecords()` method.  
`CourseRecordIOTest.testReadValidCourseRecords()`  considers an input file with valid lines and one duplicate.  When the file is processed there should be 13 `Course` objects in the `ArrayList` and their `toString()` output should match the constants `validCourse*` at the top of the test class. 
`CourseRecordIOTest.testReadInvalidCourseRecords()` considers an input file with invalid lines.  Each line is invalid in a different way as per the requirements.  The README.txt file describes why each line is invalid and may be useful for finding any bugs in your code. 

The last test method, `CourseRecordIOTest.testWriteCourseRecords()` tests the `CourseRecordIO.writeCourseRecords()` method.  The private helper method `checkFiles()` will check that the actual output file matches the expected output file.  The expected output file was provided.  You can review the tests in more detail as testing is covered in the class.  You will see file I/O again and these tests will be a useful reference for future projects!

## Troubleshooting
There are several places where you may run into trouble when implementing the `CourseRecordIO.readCourse()` method.  The troubleshooting section provides an overview of how to resolve the challenges.  You should also refer to your course text book on the chapters related to File I/O, post questions to Piazza, and attend office hours to help with the implementation of this method!

### Unable to Reset Files
You may run into a `java.lang.AssertionError: Unable to reset files` when executing the `CourseRecordIOTest.setUp()` method.  This method is resetting `course_records.txt` with the starting values needed for the tests.  Other tests in the system may overwrite `course_records.txt`, so the `starter_course_records.txt` file is used to rest the original file.  There are several possibilities that you should investigate if you run into this error:

  * Close all of the files that may be open in Eclipse or in your file system. If the file is being processed by another application, the JVM may not be able to open it.  
  * Close the `Scanner` in all possible paths in `CourseRecordIO`.  If you do not release the `Scanner` on the file, the file may still be considered in use for a time, even if the test stopped execution.  
  * Make sure that all files use the `*.txt` extension.
  * Restart Eclipse.  This will release any file handles that are attached to open files.
 
### Resource Leak
If you receive a CheckStyle notification about a resource leak on your `Scanner`, make sure that you separate any program statement `Scanner s = new Scanner(nextLine).useDelimiter(",");` into two program statements.  Using the two methods chained together leads to CheckStyle misunderstanding the flow of the methods.

 
{% capture reminder-content %} 
GitHub Resources:

  * [Staging Files](https://pages.github.ncsu.edu/engr-csc-software-development/practices-tools/git/git-staging)
  * [Committing Files](https://pages.github.ncsu.edu/engr-csc-software-development/practices-tools/git/git-commit)
  * [Pushing Files](https://pages.github.ncsu.edu/engr-csc-software-development/practices-tools/git/git-push)
{% endcapture %} {% include mention.html content=reminder-content type="reminder" title="Reference: Staging and Pushing to GitHub"%} 
## Check Your Progress
{% include iconHeader.html type="glance" %}
We've finished `CourseRecordIO`.   Before moving on to the next portion of the Guided Project, complete the following tasks:

  - [ ] Make sure that all fields, methods, and constructors are commented.
  - [ ] Resolve all static analysis notifications.
  - [ ] Fix test failures.
  - [ ] Commit and push your code changes with a meaningful commit message. Label your commit with "[Implementation]" for future you!
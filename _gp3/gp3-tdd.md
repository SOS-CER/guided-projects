---
title: Guided Project 3 WolfScheduler - Conflict
description: Guided Task - Test Driven Development
tags: [software engineering, software lifecycle, CS2, CSC216, GP3]
navigation: on
pagegroup: gp3
---

# Guided Task: Test Driven Development 
{% include iconHeader.html type="task" %}
In this section, you will start creating tests for the implementation of the `Conflict` interface in `Activity`.

{% capture callout_content %}
  * Create a test class
  * Implement a test for an exception
{% endcapture %}
{% include callout.html icon="objective" content=callout_content type="learningOutcomes" title="Learning Outcomes" %}

{% capture callout_content %}
Test Driven Development (TDD) is the process of using the requirements and object design to write the unit tests for a class first, and then use the tests to drive the implementation of the methods in the class.  The process is typically iterative.  Start with the simplest test first and implement the functionality to pass. Then add additional tests that consider other paths, edge cases, and error cases.  After adding each test, implement the functionality to pass it (if needed).

TDD is a highly effective process for developing code that is well tested.  By testing right away and letting the tests drive development, you will implement more high quality code more quickly and not run out of time for testing!
{% endcapture %}
{% include callout.html content=callout_content type="bestPractices" icon="ttTool" title="Best Practice: Test Driven Development (TDD)" %}

## Implement the `Conflict` Interface in `Activity`
Since `Activity` contains the fields related to the `meetingDays`, `startTime`, and `endTime`, you can implement the `Conflict.checkConflict()` functionality in the `Activity` class.  If the child classes need custom conflict implementation later, they can override the method.

You can use your tests to drive the creation of new methods in your code as in [using Quick Fixes for Error-Driven Development](../gp1/gp1-quick-fix#best-practice-quick-fix-for-error-driven-development).  However, this may not be appropriate in all cases - Quick Fix will help you create the `checkConflict()` method, but will not know that the method is part of implementing the `Conflict` interface.  Instead, you'll set up the appropriate structure and generate a test class from the structure.

Follow these steps to set up `Activity` for testing the `Conflict` functionality:

  * Open `Activity` in the editor.
  * Update the `Activity` class header to include `implements Conflict`.  When complete, the header should look like `public abstract class Activity implements Conflict {`.
  * Because `Activity` is an abstract class, there are no compiler errors about `Activity` needing an implementation of `Conflict`'s method.  Instead, `Course` and `Event` won't compile.  However, you want `Activity` to contain the `checkConflict()` implementation.  You can use Eclipse's source generation tool to implement the method in `Activity` by right clicking in the editor and selecting **Source > Override/Implement Methods**.  Check the option for `Conflict.checkConflict(Activity)` and click **OK**.
  
{% include image.html file="images/ImplementMethod.PNG" caption="Figure: Implementing `Conflict.checkConflict(Activity)" %} 
  
Now that `Activity` implements the `Conflict.checkConflict()` method, the compiler errors in `Course` and `Event` are resolved.




{% capture reminder-content %}
[Guided Task: Implement and Test `ConflictException` - Creating a Test Class](gp3-conflictexception#creating-a-test-class).
{% endcapture %}
{% include mention.html content=reminder-content type="reminder" icon="ttTool" title="Reminder: Creating a JUnit Test Class from a Class Under Test" %}
## Create `ActivityTest` for Testing Conflict Functionality.
Now, create the JUnit class to test the `Activity.checkConflict()` implementation.  Create a new JUnit test for `Activity` named `ActivityTest` in the `edu.ncsu.csc216.wolf_scheduler.course` package of the `test/` folder in `WolfScheduler`.  Since you've been provided test classes that test the other methods, you should only generate a test method for the `checkConflict()` method.  After generating the test, you can remove the `fail()` statement since you are about to implement the test.


## `checkConflict()` Overview
The `checkConflict()` method is an instance method of `Activity`. That means it compares the current instance (i.e., `this`) with the parameter `possibleConflictingActivity` to see if there is any conflict in their days and times.  If there is a conflict, the checked `ConflictException` is thrown.  If there is no conflict, nothing happens and the statement in the client code following the call to `checkConflict()` is executed.

Two `Activity` objects are in conflict if there is at least one day with an overlapping time.  A time is overlapping if the minute is the same.  For example, an `Activity` on Monday from 1:30PM-2:45PM would conflict with an `Activity` on Monday from 2:45PM-3:30PM because of the overlap on the 2:45 minute.  You'll encode this test shortly.

Start by Javadocing your `checkConflict()` method to describe how the conflict check works in the context of the `Activity` hierarchy.

## Writing Tests
The following sections will detail the tests that you should write to fully test the `checkConflict()` method.

### Setting Up the Test
Start by creating two two `Activity` objects to check for conflict.  Since `Activity` is `abstract`, you cannot directly construct `Activity`. Instead, you must construct a `Course` or `Event` object for the comparison.

An example of two `Activity`s that do not conflict are:

```java
Activity a1 = new Course("CSC 216", "Software Development Fundamentals", "001", 3, "sesmith5", "MW", 1330, 1445);
Activity a2 = new Course("CSC 216", "Software Development Fundamentals", "001", 3, "sesmith5", "TH", 1330, 1445);
```

Next, the `checkConflict()` method is called on one of the objects.  The other is passed as a parameter.

### No Conflict Test
If the two activities should NOT lead to a conflict, then a call to `Activity.checkConflict()` should not throw an exception.  We can test this with the `assertDoesNotThrow()` method from JUnit 5.

The general test structure is:

```java
assertDoesNotThrow(() -> activityReference.checkConflict(otherActivityReference));
```
 
An example no conflict test would be the following.  Note that we're testing that the conflict check works in both directions.

```java
@Test
public void testCheckConflict() {
    Activity a1 = new Course("CSC 216", "Software Development Fundamentals", "001", 3, "sesmith5", "MW", 1330, 1445);
    Activity a2 = new Course("CSC 216", "Software Development Fundamentals", "001", 3, "sesmith5", "TH", 1330, 1445);
    
    assertDoesNotThrow(() -> a1.checkConflict(a2));
    assertDoesNotThrow(() -> a2.checkConflict(a1));
}
```

Run the test.  Since you have not yet implemented `checkConflict()`, the test should pass!!!?  For now, that's ok.  We will shortly be implementing the `checkConflict()` method once we have a failing test to help us with our implementation.  However, our happy path test is an important test to ensure that as you implement the rest of `checkConflict()` that you do not start finding a conflict where there should be no conflict!


### Testing an Exception - Conflict Test
The next test type to consider is a test when there is a conflict.  In this case, the expected results are that the `ConflictException` is thrown. The initial test structure is:

```java
Exception e1 = assertThrows(ConflictException.class, () -> activityReference.checkConflict(otherActivityReference));
assertEquals("Schedule conflict.", e1.getMessage());
```

We can continue writing tests in the same `testCheckConflict()` method or we can create a new test method to consider this specific case.  By continuing with the previous test method, we can work with the existing local variables `a1` and `a2` and modify the days or times to lead to a conflict.  By writing another test method, we can more clearly identify which functionality is passing or failing.  The example below is a separate test method, but you are welcome to continue the implementation in the `testCheckConflict()` test method.



```java
@Test
public void testCheckConflictWithConflict() {
    Activity a1 = new Course("CSC 216", "Software Development Fundamentals", "001", 3, "sesmith5", "MW", 1330, 1445);
    Activity a2 = new Course("CSC 216", "Software Development Fundamentals", "001", 3, "sesmith5", "M", 1330, 1445);
	
    Exception e1 = assertThrows(ConflictException.class, () -> a1.checkConflict(a2));
    assertEquals("Schedule conflict.", e1.getMessage());
	
    Exception e2 = assertThrows(ConflictException.class, () -> a2.checkConflict(a1));
    assertEquals("Schedule conflict.", e2.getMessage());
}
```

Run the test.  It fails!  But that is exactly what you want.  It means you have a test that you can use to start driving the implementation of the `checkConflict()` functionality in `Activity`, which you'll work on in the next step.


## Testing Behaviors to Avoid
There are behaviors that you want to avoid when testing.  PMD will flag some of these behaviors with notifications (and a PMD notification leads to a loss of a point AND PMD testing notifications will block the teaching staff tests from running on your code!)

**Test Class without a Test Method**

Every test class should have at least one test method with the `@Test` annotation.

**Test Method with No `assert*()`**

Every test method should have at least one `assert*()` method call.  The goal of a test method is to assert or check something about the code under test to verify the code is working correctly.  It's very tempting to leave out an `assert*()` method call because your test method will pass (and you may also achieve coverage). But that means you can have no confidence in your code!  Always write a test method to assert something about the code under test!  

**Meaningless `assert*()` Statements**

A meaningless `assert*()` statement is something like `assertTrue(true);`, `assertFalse(false);`, or `assertNull(null);`.  There is  ALWAYS something to check about the code under test.  At a minimum you can check that the state has not changed or that the type is correct.  Avoid meaningless assert statements.  If you need help identifying what you should check, contact the teaching staff.


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
  - [ ] Check Jenkins results for a yellow ball!  At this point, your code should compile against the teaching staff tests.
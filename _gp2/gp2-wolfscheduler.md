---
title: Guided Project 2 WolfScheduler - Activity and Event
tags: [software engineering, software lifecycle, CS2, CSC216, GP2]
description: Independent Task - Update `WolfScheduler`
navigation: on
pagegroup: gp2
---

# Independent Task: Update `WolfScheduler`
{% include iconHeader.html type="task" %}

There are several updates required for `WolfScheduler` to work with the `Activity` hierarchy.  

{% capture callout_content %}
  * Refactor `WolfScheduler` to use `Activity` polymorphically.
{% endcapture %}
{% include callout.html content=callout_content icon="objective" type="learningOutcomes" title="Learning Outcomes" %}


## Update `WolfSchedulerTest`
[Download the updated `WolfSchedulerTest`](files/WolfSchedulerTest.java).  You can use the tests to help you drive your development.  The details of the changes are outlined in the following steps.

## Update `WolfScheduler`
There are several tasks that you will need to complete to update `WolfScheduler` to pass the provided tests.



### Update `schedule` Field
The first change is to update the generic type of the `schedule` `ArrayList`.  A `schedule` can now contain `Events`.  Update the generic type to `Activity` so you can store both `Course`s and `Event`s in the `schedule`.  You'll  need to import `Activity` and  the construction of `schedule` in `WolfScheduler.WolfScheduler()`. 

There will be additional compilation issues that you will resolve in the next steps.


### Update `addCourseToSchedule()`
Since `schedule`'s type is now `Activity` rather than `Course`, the reference returned from a call to `.get()` cannot be assigned to a `Course` reference without a cast.  *Casting should be avoided when it makes the class less cohesive.* In this case, that means `WolfScheduler` should focus on adding `Activity` objects rather than casting to figure out if an object is a duplicate or not.  To avoid casting in `WolfScheduler`, we'll create a new abstract method in `Activity` that will be implemented in `Course` to check for duplicate `Course`s and in `Event` to check for duplicate `Event`s.  

The check that is done at this portion of the code is to see if the `Course` to be added is a duplicate of a `Course` already in the schedule -- see [[UC4]](../wolf-scheduler/ws-requirements#uc4).  [[UC6]](../wolf-scheduler/ws-requirements#uc6) describes a similar situation for `Event`.  The idea of duplicate `Course`s and `Event`s is different from the definition of equality in the `equals()` methods. Keeping a full comparison is beneficial for testing and may be useful in other situations.  So now *add* a new abstract method to `Activity` that both `Course` and `Event` can implement. The method will check if some other `Course` or `Event` is a duplicate.

  * Add the abstract method `public abstract boolean isDuplicate(Activity activity);` to `Activity`.
  * Implement the  in `Course.isDuplicate()`
     * You will need to check if the parameter is an instance of `Course` and **cast** to check `Course`'s fields.  But this is similar to how the `equals()` method works and fits the `Course` abstraction of identifying a duplicate of itself.  
	 * Two `Course`s are considered duplicates if they have the same **name**.
  * Implement the method in `Event.isDuplicate()`
     * You will need to check if the parameter is an instance of `Event` and **cast** to check `Events`'s fields.  But this is similar to how the `equals()` method works and fits the `Event` abstraction of identifying a duplicate of itself.  
	 * Two `Events`s are considered duplicates if they have the same **title**. 
  * Update `WolfScheduler.addCourseToSchedule()` to use the new `isDuplicate()` method.
     * Hint: you'll need to get the `Course` to add from the `catalog` before comparing to the `Activity`s in the `schedule`.
  * Comment all your updates!
  

### Update `removeCourseFromSchedule()`
`removeCourseFromSchedule()` requires a larger refactoring.  The remove functionality is the same for both `Course`s and `Event`s.  However, the current `removeCourseFromSchedule()` method has parameter specific to `Course`.  By updating the method signature, you can update the method to handle any object in the `Activity` hierarchy.

  * Select the `removeCourseFromSchedule` method name.  Right click and select **Refactor > Change Method Signature**.
  * In the resulting dialog, remove the two existing parameters and add a new parameter of type int called `idx`.  The default value (used for replacement of the parameters in the refactoring) should be -1.  Make sure the "Keep original method as delegate to change method" is unchecked. Click **OK**.  
  

{% include image.html file="images/ChangeMethod.PNG" caption="Figure: Change Method Signature" %}
    
  * The dialog will warn of compilation errors due to the change. We'll fix those in a moment.  Click **Continue**.
  * Rename `removeCourseFromSchedule()` to `removeActivityFromSchedule()`.  Use **Alt+Shift+R** for the keyboard shortcut.
  * Fix the compilation errors so that the `removeActivityFromSchedule()` method compiles.  The parameter `idx` is the index of the `Activity` you want to remove from the `schedule`. Note that the fix can be completed by removing the for loop and delegating to the `ArrayList`'s `remove(idx)` method. You'll want to catch any `IndexOutOfBoundsExceptions` and return false.
  
  

### Update `resetSchedule()`
Fix the `resetSchedule()` method so that the method compiles and passes its test case.


### Update `getCourseCatalog()`
Update `getCourseCatalog()` to include a forth column that provides the meeting string information.

You created abstract methods in `Activity` that support returning an array for `Course`s and `Event`s.  Refactor `getCourseCatalog()` to use the `getShortDisplayArray()`.  Note that instead of assigning the cells individually, you can use the `Activity.get*DisplayArray()` method to assign the result at row `i`.  And example is shown below for `getCourseCatalog()`.

```java
	public String[][] getCourseCatalog() {
        String [][] catalogArray = new String[catalog.size()][3];
        for (int i = 0; i < catalog.size(); i++) {
            Course c = catalog.get(i);
            catalogArray[i] = c.getShortDisplayArray();
        }
        return catalogArray;
    }
```

### Update `getScheduledCourses()` and `getFullScheduledCourses()`
Do the following to update these methods:

  * Refactor `getScheduledCourses()` to `getScheduledActivities()`
  * Update `getScheduledCourses()` to use `getShortDisplayArray()` similar to `getCourseCatalog()
  * Refactor `getFullScheduledCourses()` to `getFullScheduledActivities()`
  * Update `getFullScheduledCourses()` to use `getLongDisplayArray()` similar to `getCourseCatalog()

Remember that the short display array has 4 columns and the long display array has 7 columns.


### Implement `addEventToSchedule()`
The functionality for adding a `Course` is separate from adding an `Event`.  Implement the `addEventToSchedule()` method that is called in the `WolfSchedulerTest` class.  The method headers should be:

```java
public void addEventToSchedule(String eventTitle, String eventMeetingDays, int eventStartTime, int eventEndTime, String eventDetails) {
	
}
```

If the new `Event` is a duplicate of an existing `Event` in the schedule, an `IllegalArgumentException` should be thrown with the message "You have already created an event called [event title]".

### Run Tests
Run your tests!  If any are still failing, use the debugger to help you find the problem.

### Comment `WolfScheduler` and Fix Static Analysis Notifications
Complete the following tasks:

  * Update all your Javadoc for `WolfScheduler`. 
  * Resolve all static analysis notifications.


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
  - [ ] Commit and push your code changes with a meaningful commit message.  Label your commit with "[Implementation]" for future you!
  - [ ] Check Jenkins results for a green ball!  Fix any Jenkins issues.
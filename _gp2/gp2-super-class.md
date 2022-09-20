---
title: Guided Project 2 WolfScheduler - Activity and Event
tags: [software engineering, software lifecycle, CS2, CSC216, GP2]
description: Guided Task - Extract a Super Class
navigation: on
pagegroup: gp2
---

# Guided Task: Extract a Super Class
{% include iconHeader.html type="task" %}

With the new hierarchy design, now you need to move toward implementation.  The common elements are already implemented in `Course`.  You can extract those elements into the parent class.  Attempting this extraction manually can be messy and can lead to breaking the code.  Luckily, Eclipse provides a refactoring tool that helps with extracting a super class, because developers frequently need to make these types of changes in their code.

{% capture callout_content %}
  * Use the Eclipse refactoring tool to create a super class
  * Use automated testing to ensure no regression of functionality
{% endcapture %}
{% include callout.html content=callout_content icon="objective" type="learningOutcomes" title="Learning Outcomes" %}


## Extract the Super Class
To extract the `Activity` super class, do the following:

  * Open `Course` in the editor.
  * Right click in the `Course` class in the editor and select **Refactor > Extract Superclass**.  Make sure you are in the curly braces (e.g., `{}`) that define `Course`, otherwise the option to **Extract Superclass** won't be available!
  * Give the superclass the name `Activity`.
  * Select the checkboxes next to the following members of `Course`
     * `UPPER_HOUR`
     * `UPPER_MIN`
     * `title`
     * `meetingDays`
     * `startTime`
     * `endTime`
     * `getTitle()`
     * `setTitle()`
     * `getMeetingDays()`
	 * `getMeetingString()`
     * `getStartTime()`
     * `getEndTime()`
     * `setMeetingDaysAndTime()`
     * Any private helper methods that you wrote to support the implementation of the above methods (the teaching staff solution has a helper method `getTimeString()`)
     
    
{% include image.html file="images/ExtractSuperClass.PNG" caption="Figure: Extracting a Super Class" %}
    
  * Click **Next** and verify that you have all the items you need.
  
    
{% include image.html file="images/ExtractSuperClass2.PNG" caption="Figure: Extracting a Super Class" %}


  * Click **Next**.  Eclipse will provide a warning that the visibility of the method `getTimeString()` will change due to the refactoring.  Since the method is used in `Course`, the method will need to be public so `Course` can access it. Warnings like this should be noted for review after the refactoring.
  
{% include image.html file="images/ExtractSuperClass3.PNG" caption="Figure: Extracting a Super Class" %}  
  
  * Click **Next** again.  You'll see a list of the changes that will be performed as part of the refactoring.  This change will modify most of the classes in the project!  
  
{% include image.html file="images/ExtractSuperClass4.PNG" caption="Figure: Extracting a Super Class" %}
    
  * Click **Finish**.
 
 
### Check Compilation
Your project should continue to compile after the refactoring is complete.  If your code does not compile, you can use Ctrl+Z (Cmd+Z) to undo the refactoring and try again! 


### Run Tests
Run all of your unit tests on the refactored code.  Ensure there are no regressions in functionality.


## Update `Activity` and `Course`
Now that we have extracted the `Activity` class, we have a few changes that we need to make to ensure encapsulation of `Activity` information and provide the additional functionality that `Activity` needs.  Complete the following steps.

### Make `Activity` Abstract
Since `Activity` is a super class of `Course` and will soon be the super class of `Event`, there is no need for `Activity` to be a concrete class.  Instead, `Activity` should be abstract - that means you cannot directly construct `Activity` objects. Additionally, we'll be creating some abstract behavior that we `Course` and `Event` will define for their contexts.

  * Add the `abstract` keyword to the `Activity` class header.
  
```java
public abstract class Activity { 
   ...
}
```


### Make `Activity`'s Fields Private
When creating the super class, Eclipse set the fields of `Activity` to protected level access.  This means that any sub-class can access the fields directly.  However, it also means that another class in the same package can also access the fields directly. To protect your fields, make them `private`.

### Resolve `Course` Compilation Errors
There will be several compilation errors in `Course` after you make the fields in `Activity` private in the `hashCode()`, `equals()`, and `toString()` methods.  Do the following to resolve:  
 
  * Remove `hashCode()` and `equals()`.  Now that there is a super class, you should regenerate `hashCode()` and `equals()` to use the super class. DO NOT do generate a new `equals()` and `hashCode()` yet!
  * In `toString()`, change direct references to `Activity` fields to use the associated getter methods.

{% include image.html file="images/CourseToStringUpdates.PNG" caption="Figure: Updating Course.toString()" %}  

  * Run your tests.  The tests for `Course.hashCode()` and `Course.equals()` will fail.  The `WolfSchedulerTest.testGetCourseFromCatalog()` will also fail because `Course.equals()` is not yet reimplemented.  You'll fix those shortly!


### Create `Activity`'s Constructor
`Activity` was created with a parameterless constructor.  You want to continue to use the *one path of construction* paradigm.  That means you need a way to construct `Activity` and its fields.

  * Replace the default `Activity` constructor with one that requires all of the fields.  The parameters MUST be in the order of `title`, `meetingDays`, `startTime`, and `endTime`.  Additionally, update the body of the constructor to use the appropriate setter methods for the fields since all of the error checking is completed there.
  
```java
    public Activity(String title, String meetingDays, int startTime, int endTime) {
        super();
        setTitle(title);
        setMeetingDaysAndTime(meetingDays, startTime, endTime);
    }
```

### Update `Course` Constructor
After you add a parameterized constructor to `Activity`, `Course` no longer compiles.  Now, `Course` needs to call the parameterized `Activity` constructor.  

  * Update `Course`'s non-compiling constructor to use `Activity`'s new constructor.  Remember, `Activity` is the parent of `Course`.  To interact with the parent class, you need to use the `super` reference.
  
```java
    public Course(String name, String title, String section, int credits, String instructorId, String meetingDays,
            int startTime, int endTime) {
        super(title, meetingDays, startTime, endTime);
        setName(name);
        //setTitle(title);  <-- DELETE THIS, called in super
        setSection(section);
        setCredits(credits);
        setInstructorId(instructorId);
        //setMeetingDaysAndTime(meetingDays, startTime, endTime); <-- DELETE THIS, called in super
    }
```
  
  
  * Run your unit tests to make sure that everything is still passing (except for the failures discussed above).
  

{% capture reminder-content %} 
[Generate `hashCode()` and `equals()`](../gp1/gp1-source-gen#generate-equals-and-hashcode)
{% endcapture %} {% include mention.html content=reminder-content type="reminder" title="Reference: Generating Source Code"%} 
### Generate `hashCode()` and `equals()`
Do the following to add back the `hashCode()` and `equals()` functionality in both `Activity` and `Course`.  Note that you want to generate `Activity`'s methods *first* since `Course`'s method will rely on `Activity`'s.

  * Use Eclipse's source generation tools to generate `hashCode()` and `equals()` in `Activity`.
  * Then use Eclipse's source generation tools to generate `hashCode()` and `equals()` in `Course`.
  * Run your unit tests.  They should all be passing again!
  

### Add Abstract Functionality to `Activity`
Adding events will complicate the display of information in the GUI.  There will be some items that `Course` has that `Event` will not and vice versa.  Creating the array of Strings for display in the GUI should instead be delegated to classes in the `Activity` hierarchy.  You will add two abstract methods that will provide a short and a long version of the array of information to provide to the GUI.

  * Add the statement `public abstract String[] getShortDisplayArray();` to `Activity`.
  * Add the statement `public abstract String[] getLongDisplayArray();` to `Activity`.
  
After adding the methods, make sure you comment them.  This will help any developers that extend `Activity` in the future better understand the intention of the methods.  The short display array is used to populate the rows of the course catalog and student schedule [[UC1, UC3, UC4, UC6](../wolf-scheduler/ws-requirements)].  The full display array is used to display the final schedule [[UC9](../wolf-scheduler/ws-requirements#uc9)].
  

### Implement Abstract Functionality in `Course`
After you add these statements, `Course` will no longer compile.  Select the compiler error on the `Course` class header and use the Quick Fix to add implementations of these two methods to `Course`.

Implement the methods in `Course` as follows:

  * `getShortDisplayArray()` returns an array of length 4 containing the `Course` `name`, `section`, `title`, and meeting string.
  * `getLongDisplayArray()` returns an array of length 7 containing the `Course` `name`, `section`, `title`, `credits`, `instructorId`, meeting string, empty string (for a field that `Event` will have that `Course` does not).
  
### Extended `Course` Unit Testing
Using the `WolfScheduler` [requirements](../wolf-scheduler/ws-requirements) along with the [provided `ExtendedCourseTest` JUnit tests](files/ExtendedCourseTest.java), you will finish implementing the `Course` class to pass the tests!

### Comment `Activity` and `Course` and Fix Static Analysis Notifications
Update all your Javadoc for `Activity` and `Course`.  Make sure you update all references to `Course` in the comments for `Activity`.  

Overridden methods much also be commented to describe the specifics in the overridden implementation.

Now is a great time to make sure that CheckStyle, PMD, and SpotBugs are all active on your project.  Right click on the WolfScheduler project and select **Properties**.  You can select each tool and make sure it is turned on.  Resolve all the notifications.


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
  - [ ] Commit and push your code changes with a meaningful commit message.  Label your commit with "[Refactoring]" for future you!
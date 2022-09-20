---
title: Guided Project 1 - Software Development Practices and Tools
tags: [software engineering, software lifecycle, CS2, CSC216, GP1]
description: Guided Task - Encapsulation and Reducing Redundancy
navigation: on
pagegroup: gp1
---
 
# Guided Task: Encapsulation and Reducing Redundancy
{% include iconHeader.html type="task" %}
Code is redundant where there are multiple locations with the same or almost the same statements.  By reducing redundancy, you can put functionality in one location in our programs and access that functionality through calling methods.  That means if there's a bug, you have one place to look to find and fix the problem!  

{% capture callout_content %}
  * Use private methods to hide setters from a client
  * Call setter methods from a constructor
  * Follow *one path of construction* paradigm
{% endcapture %}
{% include callout.html content=callout_content icon="objective" type="learningOutcomes" title="Learning Outcomes" %}
  
{% capture callout_content %}
You learned in your introductory programming course that methods or procedures were created to provide a name for a related set of program statements that are likely to be used over and over.  While there is a small cost to every method call, the gains in code readability, understandability, and maintenance are critical for teams of software developers working on large programming projects.  When working on code, you should remove redundant code as often as you can!
{% endcapture %}
{% include callout.html content=callout_content type="bestPractices" title="Best Practice: Reducing Redundancy" %}
  
 
## Further Encapsulate the `Course.name` Field
A `Course` shouldn't ever change its `name` (CSC 216 will always be CSC 216).  You want to have a method that will set the `name` field and do all the appropriate checks that the value is correct when constructing the object, but you don't want to allow clients of your code to change the field after construction.  You need to make the `setName()` method `private` to prevent clients from modifying the field.  There will be a warning about not using the `setName()` method, but you can ignore it for now.  You'll use the method shortly.

{% capture callout_content %}
The **Outline View** provides a list of the fields and methods in the class that is currently in focus in the Editor.  You can sort the members listed in the outline view in several different ways. By clicking a member in the outline view, the editor will be updated to display that element.  It's a lot faster to click a method in the outline view than to scroll through your code.  Give it a try to select `setName()`.

{% include image.html file="images/OutlineView.PNG" caption="Figure: Outline View" %} 
{% endcapture %}
{% include callout.html content=callout_content type="bestPractices" title="Best Practice: Use the Outline" %}

Change the `setName()` method to use the `private` access identifier as shown below.  Notice the outline view changes the icon next to the method from a green circle (indicating `public`) to a red square (indicating `private`).



```java
/**
 * Set's the Course's name.
 * @param name the name to set
 */
private void setName(String name) {
    this.name = name;
}
```

{% capture callout_content %}
Setter methods are convenient for wrapping up all the (potentially complex) functionality for checking that a value is valid for storage in a class's field.  However, you may not want to expose that functionality to a client.  `private` methods provide a mechanism for wrapping up functionality in a method that can be used internally within the class as a helper method for setting the values for a given field.
{% endcapture %}
{% include callout.html content=callout_content icon="plTool" type="conceptualKnowledge" title="Conceptual Knowledge: Encapsulation - `private` Setters" %}

 
## Reducing Redundancy in the `Course` Constructors
The Eclipse constructor generation code assigns the parameters to the fields directly.  However, there is error checking that you must complete on the constructor's parameters before assigning them to fields (you'll actually write the error checking code in the next step).  The parameters of all setter methods for `Course` should also be checked.  For example, a `Course` should not be created if the `name` is `null` or an empty string. 

To reduce duplicate code, you can place the code to check for invalid parameters in each of the setter methods and call the setter methods from the constructor.

{% capture callout_content %}
Another consideration when designing classes is that if you do have code that checks if a field receives a correct value, you should have that code in only one place.  A setter method for a field may be appropriate.  Other methods that change the field can call the setter with the appropriate value and handle an incorrect value as needed for the calling method's goals.
{% endcapture %}
{% include callout.html content=callout_content icon="plTool" type="conceptualKnowledge" title="Conceptual Knowledge: Reducing Redundancy" %}

The constructor calls each of the setters for the fields, as shown below.

```java
/**
 * Constructs a Course object with values for all fields.
 * @param name name of Course
 * @param title title of Course
 * @param section section of Course
 * @param credits credit hours for Course
 * @param instructorId instructor's unity id
 * @param meetingDays meeting days for Course as series of chars
 * @param startTime start time for Course
 * @param endTime end time for Course
 */
public Course(String name, String title, String section, int credits, String instructorId, String meetingDays,
        int startTime, int endTime) {
    setName(name);
    setTitle(title);
    setSection(section);
    setCredits(credits);
    setInstructorId(instructorId);
    setMeetingDays(meetingDays);
    setStartTime(startTime);
    setEndTime(endTime);
}

/**
 * Creates a Course with the given name, title, section, credits, instructorId, and meetingDays for 
 * courses that are arranged.
 * @param name name of Course
 * @param title title of Course
 * @param section section of Course
 * @param credits credit hours for Course
 * @param instructorId instructor's unity id
 * @param meetingDays meeting days for Course as series of chars
 */
public Course(String name, String title, String section, int credits, String instructorId, String meetingDays) {
    setName(name);
    setTitle(title);
    setSection(section);
    setCredits(credits);
    setInstructorId(instructorId);
    setMeetingDays(meetingDays);
}
```
    
However, you still have some redundant code in your constructors - the calls to `setName()`, `setTitle()`, `setSection()`, `setCredits()`, `setInstructorId()`, and `setMeetingDays()`.  You want to follow the paradigm of *one path of construction* to further reduce redundant code.

{% capture callout_content %}
When writing a class, you want to minimize redundancy.  That is one reason why you want to create setters for checking that the values stored in a field are appropriate for the class.  Another way to minimize redundancy is to create one path of construction for a class.  In Java, a class can have multiple constructors with different sets of parameters to initialize a class.  One constructor should call another constructor (with appropriate default values for any missing fields) so that there is the main construction code in only one location.  And that code can call (or delegate to) the appropriate setters for setting field values so that the code for checking for a valid field value is in only one location.

You call another constructor in a Java class using the keyword `this()`.

By having one location for functionality, it's much easier to maintain your code.  If there's a bug, you only have one place that you need to look to find and fix it!
{% endcapture %}
{% include callout.html content=callout_content icon="plTool" type="conceptualKnowledge" title="Conceptual Knowledge: One Path of Construction" %} 

You will update your `Course` constructor with six parameters so that it calls the `Course` constructor with all eight parameters.  You'll pass in default parameters for the course times.  We'll use 0 to represent the idea of a course with no meeting time.

```java
/**
 * Creates a Course with the given name, title, section, credits, instructorId, and meetingDays for 
 * courses that are arranged.
 * @param name name of Course
 * @param title title of Course
 * @param section section of Course
 * @param credits credit hours for Course
 * @param instructorId instructor's unity id
 * @param meetingDays meeting days for Course as series of chars
 */
public Course(String name, String title, String section, int credits, String instructorId, String meetingDays) {
    this(name, title, section, credits, instructorId, meetingDays, 0, 0);
}
```

{% capture reminder-content %} 
GitHub Resources:

  * [Staging Files](https://pages.github.ncsu.edu/engr-csc-software-development/practices-tools/git/git-staging)
  * [Committing Files](https://pages.github.ncsu.edu/engr-csc-software-development/practices-tools/git/git-commit)
  * [Pushing Files](https://pages.github.ncsu.edu/engr-csc-software-development/practices-tools/git/git-push)
{% endcapture %} {% include mention.html content=reminder-content type="reminder" title="Reference: Staging and Pushing to GitHub"%} 
## Check Your Progress
{% include iconHeader.html type="glance" %}
You've made a lot of changes to your `Course` class by reducing redundancy.  Before moving on to the next portion of the Guided Project, complete the following tasks:

  - [ ] Update the comments on the `Course` class.
  - [ ] Make sure that all fields, methods, and constructors are commented.
  - [ ] Commit and push the `Course` class to GitHub.  Remember to use a meaningful commit message describing how you have changed the code.  For example, "[Refactoring] Reduced redundancy in Course".



<!--
!#step-row
##Protecting `Object` Fields
Encapsulation of classes protects the class' data.  However, we have to remember that when a method of a class returns and `Object` type, it is really returning a reference to the type and not a copy of the object.  If we want the client to be able to modify the `Object`, then everything is fine.  But if that `Object` shouldn't be modified by a client, we should copy the `Object`'s state to a new object and return the copy so that we protect our class' data.
    
!#row
!#callout-conceptualKnowledge
!#class="plToolIcon-white" role="img" aria-label="Programming Language Tool Icon"
#Conceptual Knowledge: Protective Copying of `Object` fields {.callout-h1}   
Getters can also provide a problem with encapsulation.  All objects in Java are *passed by reference*.  That means a reference that points to the object in memory is passed to a method as a parameter and returned from a method with an object return type.  Any class with a reference can change the object through the reference and the change is seen through all references!  If you have a field that is an object that you DO NOT want changed, make a new instance of the object and copy the state.  Return the copy.  Then any changes made by the client will affect the copy and not the original protected by your class.
!#callout-end

There is only one `Object` field that we need to be concerned about with `Course`: `meetingDays` (remember and array is a pseudo-object).  While `String`s are `Objects`, they are *immutable*, which means that after a `String` is created it cannot be changed.  The `String` class is already implemented with protective copying of the field before returning the `String` from any of `String`'s methods.  We'll now do the same with `meetingDays`.

Update `getMeetingDays()` with the following code that copies the array and returns the copy.

	/**
	 * Returns a copy of the array of meeting days.
	 * @return the meetingDays
	 */
	public boolean[] getMeetingDays() {
		return Arrays.copyOf(meetingDays, meetingDays.length);
	}
-->

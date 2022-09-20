---
title: Guided Project 1 - Software Development Practices and Tools
tags: [software engineering, software lifecycle, CS2, CSC216, GP1]
description: Guided Task - Working with the Java Libraries
navigation: on
pagegroup: gp1
---
 
# Guided Task: Working with the Java Libraries
{% include iconHeader.html type="task" %}
Your skeleton of `CourseRecordIO` uses classes and interfaces from the [`java.io` package](https://docs.oracle.com/javase/8/docs/api/java/io/package-summary.html) and the [Java Collections Framework](https://docs.oracle.com/javase/8/docs/technotes/guides/collections/overview.html).   

{% capture callout_content %}
  * Implement code using [`List`](https://docs.oracle.com/javase/8/docs/api/java/util/List.html) and [`ArrayList`](https://docs.oracle.com/javase/8/docs/api/java/util/ArrayList.html).
  * Review file I/O implementation.
{% endcapture %}
{% include callout.html content=callout_content icon="objective" type="learningOutcomes" title="Learning Outcomes" %}
  
{% capture callout_content %}
When programming complex systems, most software engineers don't start from scratch.  Instead, they take advantage of existing libraries of common functionalities when writing their programs.  You work with libraries that are part of the Java Development Kit (JDK) all the time when writing programs.  For example, any time you print to the console using `System.out.println()`, you are working with the `System` class'  `PrintStream` object named `out`, which has a method `println()` that provides the functionality for writing to standard output stream (or the console).  

You will be working with two portions of the JDK when implementing `CourseRecordIO`: the [`java.io` package](https://docs.oracle.com/javase/8/docs/api/java/io/package-summary.html) and the [Java Collections Framework](https://docs.oracle.com/javase/8/docs/technotes/guides/collections/overview.html).
{% endcapture %}
{% include callout.html content=callout_content icon="plTool" type="bestPractices" title="Best Practice: Working with Libraries" %}

 
## File Input
When reading from files, you use the [`Scanner`](https://docs.oracle.com/javase/8/docs/api/java/util/Scanner.html) class (which is actually in the `java.util` package because `Scanner` can scan other things than files).  The `CourseRecordIO.readCourseRecords()` method will use the `Scanner` class to read the file.  `readCourseRecords()` receives a parameter specifying the name of the file that will be read. 

`Scanner` has several constructors that accept parameters specifying different resources that `Scanner` can parse.  When working with `File`s, `Scanner` requires a parameter of type `File` or `FileInputStream`.  For `CourseRecordIO` we will use `FileInputStream` so that the files are processed as bytes rather than characters.  You will use the `Scanner` as you normally would.  Passing in a `String` type will lead to a logic error because `Scanner`s can also be used to parse `String`s!

The `Scanner(File)` constructor may throw a *checked* `FileNotFoundException` if there is a problem reading the file.  One way to handle is that to surround the code with a `try/catch` block.  However, that would hide the error within the `CourseRecordIO` class.  Instead, the `CourseRecordIO.readCourseRecords()` throws a `FileNotFoundException` out to the client.  That means you do not need to check for the `FileNotFoundException` in `CourseRecordIO`.

Copy the code below into your `CourseRecordIO.readCourseRecords()` method.  This code should replace the entire method body.  Delete the `TODO` comment.  It's no longer needed because you are implementing the method.

You will have compiler errors under the `Scanner` and `FileInputStream` classes.  Use Eclipse's quick fix tool to import those classes (**Ctrl+1** or **Cmd+1**).

```java
Scanner fileReader = new Scanner(new FileInputStream(fileName));

fileReader.close();
return null;
```

{% capture callout_content %}
When passed a `File` as a parameter, a `Scanner` is a wrapper for an operating system resource called a *file handle*.  Every time you create a `File` `Scanner`, you use one of the OS's file handles.  File handles are a limited resource, so when you use a file handle, you should make sure it's released when you're done.  This is done through the `Scanner.close()` method.
{% endcapture %}
{% include callout.html content=callout_content icon="plTool" type="conceptualKnowledge" title="Conceptual Knowledge: File Resources" %}



{% capture reminder-content %} 
If you need help using Eclipse's Quick Fix to create a method, see [Guided Task: Eclipse Quick Fix - Create `CourseRecordIO` Methods](gp1-quick-fix#create-courserecordio-methods).
{% endcapture %} {% include mention.html content=reminder-content type="reminder" title="Reminder: Eclipse Quick Fix"%} 
## File Processing
`Scanner` has a set of `hasNext*()` methods that let you check to see if the next value is of the type that you want.  Once you know that the next token is the value you want, you can use a `next*()` method to get the value of the given type.  From the requirements for [UC 1: Load Course Catalog](../wolf-scheduler/ws-requirements#uc1), you know that the `Course` records are stored in a text file with one `Course` record per line.  You will want to get each line from the file and then create a `Course` or skip that line if the record is not a valid `Course`.

The following code sets up the loop for processing each line.  You will use a `private` helper method, `readCourse()`, to process each `Course`.  You can use Eclipse's Quick Fix to create the `readCourse()` helper method.

```java
Scanner fileReader = new Scanner(new FileInputStream(fileName));
while (fileReader.hasNextLine()) {
    Course course = readCourse(fileReader.nextLine());
}
fileReader.close();
return null;
```

{% capture callout_content %}
When writing object-oriented code, you may find that public methods (those that a client may want to use) can quickly grow complex.  When that happens, it is useful to put some of the functionality in a `private` method.  By creating smaller methods, the code is easier to maintain.  The cost of calling another method is very small compared to readable code in large systems.
{% endcapture %}
{% include callout.html content=callout_content icon="plTool" type="conceptualKnowledge" title="Conceptual Knowledge: `private` Helper Methods" %}

 
## File Output
You can use the `PrintStream` class (the same type as `System.out`) to write to a `File` by providing a `File` object as an actual parameter.  `CourseRecordIO.writeCourseRecords()` writes information about each `Course` to the file using a `PrintStream` as shown below.

Like `Scanner`, `PrintStream`s should also be closed when they are done.  Note that you are also using the `Course.toString()` method to create the comma-separated output in the same format as the input!

Copy the following code into your `CourseRecordsIO.writeCourseRecords()` method.  

```java
PrintStream fileWriter = new PrintStream(new File(fileName));

for (int i = 0; i < courses.size(); i++) {
    fileWriter.println(courses.get(i).toString());
}

fileWriter.close();
```
    


 
## Java Collections Framework
The Java Collections Framework (JCF) provides functionality for working with collections of objects.  In CSC216, you will focus on the [`List`](https://docs.oracle.com/javase/8/docs/api/java/util/List.html) collection type. 

{% capture callout_content %}
`ArrayList` provides `List` functionality using the underlying storage of an array.  That means `ArrayList` is a class that wraps additional functionality around an array so that it is easier for clients (like us) to work with it.  

Like an array, `ArrayList` provides functionality for adding elements, removing elements, getting elements, finding the size, and several other useful methods.  The table below shows the relationship between arrays and `ArrayList`.

| Function | Array | `ArrayList` |
|-------------|-----------------------------------|-----------------------------------|
| Constructing | `String [] array = new String[size]` | `ArrayList<String> array = new ArrayList<String>()` |
| Adding an element | `array[0] = "apple";` | `array.add(0, "apple");` |
| Removing an element | `array[0] = null;` | `array.remove("apple");` |
| Getting an element | `return array[0];` | `return array.get(0);` |
| Size | `array.length` | `array.size()` |
{% endcapture %}
{% include callout.html content=callout_content icon="plTool" type="conceptualKnowledge" title="Conceptual Knowledge: `ArrayList` and `Arrays`" %}

`CourseRecordIO.readCourseRecords()` returns an `ArrayList` of `Course`s.  That means the method should construct an empty `ArrayList` and add each `Course` to the `ArrayList`.  You can also plan for the error handling that needs to occur when there's an invalid `Course` record.  If there's a problem when constructing a `Course` object, an `IllegalArgumentException` is thrown.  You can catch the exception and skip adding that line to the `courses` `ArrayList`.  Additionally, you need to handle the requirement in [[UC1, Processing Course Information]](../wolf-scheduler/ws-requirements#uc1-e1) where a course record is invalid if the name and section is the same as another course in the list.  That means only the first course in an input file with a given name, title, and section is added to the list.  Others are ignored.  

Copy this code into your `CourseRecordsIO.readCourseRecords()` method.  You should overwrite the code we copied in earlier.  The comment provide additional details about what is happening in the class.

```java
public static ArrayList<Course> readCourseRecords(String fileName) throws FileNotFoundException {
    Scanner fileReader = new Scanner(new FileInputStream(fileName));  //Create a file scanner to read the file
    ArrayList<Course> courses = new ArrayList<Course>(); //Create an empty array of Course objects
    while (fileReader.hasNextLine()) { //While we have more lines in the file
        try { //Attempt to do the following
            //Read the line, process it in readCourse, and get the object
            //If trying to construct a Course in readCourse() results in an exception, flow of control will transfer to the catch block, below
            Course course = readCourse(fileReader.nextLine()); 

            //Create a flag to see if the newly created Course is a duplicate of something already in the list  
            boolean duplicate = false;
            //Look at all the courses in our list
            for (int i = 0; i < courses.size(); i++) {
                //Get the course at index i
                Course current = courses.get(i);
                //Check if the name and section are the same
                if (course.getName().equals(current.getName()) &&
                        course.getSection().equals(current.getSection())) {
                    //It's a duplicate!
                    duplicate = true;
                    break; //We can break out of the loop, no need to continue searching
                }
            }
            //If the course is NOT a duplicate
            if (!duplicate) {
                courses.add(course); //Add to the ArrayList!
            } //Otherwise ignore
        } catch (IllegalArgumentException e) {
            //The line is invalid b/c we couldn't create a course, skip it!
        }
    }
    //Close the Scanner b/c we're responsible with our file handles
    fileReader.close();
    //Return the ArrayList with all the courses we read!
    return courses;
}
```

Note that in the `CourseRecordIO.writeCourseRecords()` code in the last section, you already used an `ArrayList`.  `for` loops are an excellent tool for working with the elements of an `ArrayList`.  Instead of using the array's length, you get the `ArrayList`'s `size()`.  You can use the `get()` method to get the element at index `i`.

 
{% capture reminder-content %} 
GitHub Resources:

  * [Staging Files](https://pages.github.ncsu.edu/engr-csc-software-development/practices-tools/git/git-staging)
  * [Committing Files](https://pages.github.ncsu.edu/engr-csc-software-development/practices-tools/git/git-commit)
  * [Pushing Files](https://pages.github.ncsu.edu/engr-csc-software-development/practices-tools/git/git-push)
{% endcapture %} {% include mention.html content=reminder-content type="reminder" title="Reference: Staging and Pushing to GitHub"%} 
## Check Your Progress
{% include iconHeader.html type="glance" %}
You've added functionality to `CourseRecordIO`, but it's not yet complete. Before moving on to the next portion of the Guided Project, complete the following tasks:

  - [ ] Make sure that all fields, methods, and constructors are commented.
  - [ ] Resolve all static analysis notifications.
  - [ ] Commit and push your code changes with a meaningful commit message.  Try writing your own commit message this push.  We suggest that you label the commit with the "[Implementation]" tag to describe the type of commit.  This will help future you (and the teaching staff or any future teammates) understand what you did in this commit.
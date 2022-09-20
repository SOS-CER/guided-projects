---
title: Guided Project 3 WolfScheduler - Conflict
description: Independent Task - Write and Update System Test Plan
tags: [software engineering, software lifecycle, CS2, CSC216, GP3]
navigation: on
pagegroup: gp3
---

# Independent Task: Write and Update System Test Plan
{% include iconHeader.html type="task" %}
Test Driven Development (TDD) means that tests are written before code is written.  For system level tests, that means they are written as soon as the requirements are finalized. You will use the [WolfScheduler Requirements](../wolf-scheduler/ws-requirements) to write additional test cases for the conflict functionality.  Additionally, you will update any test cases that are no longer appropriate once the conflict functionality is added. 

{% capture callout_content %}
  * Write and update system tests
{% endcapture %}
{% include callout.html icon="objective" content=callout_content type="learningOutcomes" title="Learning Outcomes" %}


## Create GP3 System Test Plan Document
If you don't already have a `project_docs` folder in your `WolfScheduler` project, create it by right clicking on `WolfScheduler` and selecting **New > Folder**. 

You'll start with a copy of the Guided Project 2 System Test Plan that [has been updated with instructions for Guided Project 3](https://docs.google.com/document/d/1tMpkfJVXFHG4XOVE-9Vtj-qNVbM9cgrQfgpf626_600/edit?usp=sharing).  

  1. Download the document as a Word document by selecting **File > Download > Microsoft Word** in Google Drive.
  2. Save your system test plan as a Word document (`*.doc` or `*.docx`) 
  3. Put the system test plan in the `WolfScheduler` `project_docs` folder. 
  4. Add the system test plan to the index of the repo and commit/push.  


## Add and Modify Tests
Read the [`WolfScheduler` requirements](../wolf-scheduler/ws-requirements).  Guided Project 3 will focus the **[Schedule Conflict]** alternative flows of Use Cases 4 & 6 around time.  The remaining requirements were implemented in Guided Projects 1 and 2.
  
  * [Use Case 1: Load Course Catalog](../wolf-scheduler/ws-requirements#uc1)
  * [Use Case 2: Rename Schedule](../wolf-scheduler/ws-requirements#uc2)
  * [Use Case 3: View Course Information](../wolf-scheduler/ws-requirements#uc3)
  * [Use Case 4: Add Course to Schedule](../wolf-scheduler/ws-requirements#uc4)
  * [Use Case 5: Remove Course from Schedule](../wolf-scheduler/ws-requirements#uc5)
  * [Use Case 6: Add Event to Schedule](../wolf-scheduler/ws-requirements#uc6)
  * [Use Case 7: Remove Event from Schedule](../wolf-scheduler/ws-requirements#uc7)
  * [Use Case 8: Reset Schedule](../wolf-scheduler/ws-requirements#uc8)
  * [Use Case 9: Display Final Schedule](../wolf-scheduler/ws-requirements#uc9)
  * [Use Case 10: Export Schedule](../wolf-scheduler/ws-requirements#uc10)

With the new time conflict functionality, there are tests in the system test plan that were fine for Guided Project 2, but that no longer meet the requirements.  These tests must be revised to meet the full `WolfScheduler` requirements.

Do the following tasks to update your system test plan:

  * Identify any tests that will fail with the conflict requirement fully implemented. Revise or rewrite the test(s).  You MAY NOT remove them!  Mark them as "(Modified)" in the Test ID column and highlight the rows in a light gray.
  * Write 5 additional tests that consider different conflict scenarios.  Mark them as "(New)" in the Test ID column and highlight the rows in a darker gray.
  
**Additional instructions about the expectations for updating the system test plan for the `WolfScheduler` project are IN the System Test Plan document.  Please follow those instructions (especially highlighting new or modified tests) to help with grading and earning full credit for your work.**
  

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
  - [ ] Double check that your GP3 System Test Plan was pushed to the repo!  This is a common mistake.
  - [ ] Commit and push your code changes with a meaningful commit message.  Label your commit with "[Test]" or "[System Test]" for future you!

---
title: WolfScheduler
tags: [software engineering, software lifecycle, CS2, CSC216]
description: WolfScheduler Commenting and Style
navigation: on
pagegroup: wolf-scheduler
---
# WolfScheduler Commenting and Style
{% include iconHeader.html type="implementation" %}


## Commenting
{% include iconHeader.html type="dtTool" %}

Every class, method, and field must be Javadoced and follow the [CSC Department's Style Guidelines](https://pages.github.ncsu.edu/engr-csc116-staff/CSC116-Materials/course-resources/style-guidelines/). Your Javadoc comments must be meaningful and relevant to the class, method, and field.


## Generating Javadoc
{% include iconHeader.html type="dtTool" %}

You will generate the HTML API pages by using the Javadoc tool as described in [Javadoc section of Guided Project 1](../gp1/gp1-javadoc). The generated Javadoc should be stored in a `doc/` directory of your project.


## Static Analysis Tools
{% include iconHeader.html type="saTool" %}

We will use three different static analysis tools to find potential problems in our code. The reason we're using three static analysis tools is that each tool has an area of specialization. The three tools we're using are:

  * **FindBugs**: FindBugs finds potential security vulnerabilities and dangerous code patterns that may lead to runtime exceptions.
  * **PMD**: PMD can find some code problems and style issues. We'll focus on using PMD for finding style problems and incorrect JUnit tests.
  * **CheckStyle**: CheckStyle finds problems with style issues: naming, indentation, commenting, etc.
  
You will use static analysis tools to help remember good style and prevent careless mistakes while developing software.  These tools will need to be configured for each project and they may be set up to run automatically with every save.  

Any un-addressed static analysis notifications, unless otherwise allowed by the teaching staff, will result in a deduction from your [style grade](ws-rubric).  Make sure that you are using the CheckStyle and PMD configuration files for this class (details are in [CSC216 Environment Setup - PMD and CheckStyle Settings](../install/install-overview#pmd-and-checkstyle-settings)). If you are not using the provided style files, PMD and CheckStyle will generate an *abundance* of additional notifications on items that we are not requiring you to fix.


### FindBugs
FindBugs will need to be configured for each project and then run using the following steps. You should remove all notifications that are labeled **Scariest** and **Scary** before submitting your code. This will prevent potential silly mistakes.


#### Configure FindBugs
Do the following to configure FindBugs for your project:

  * Right click on the project and select **Properties > FindBugs**.
  * Select the check boxes labeled **Enable project specific settings**, **Run automatically**, and **(also on full build)**.
  * In the **Reporter Configuration** tab, move the slider all the way to the right so that the text **9 (Scary)** is listed below the slider.
  * Leave the default selection of **Reported (visible) bug categories** (Bad practice, Correctness, Performance, Dodgy code, and Multithreaded correctness)
  * Select the drop down boxes next to **Scariest** and **Scary** to contain **Error**.
  * Click **OK**.
  * Click **OK** on the pop-up box about **Full FindBugs build required**.


#### Run FindBugs
Do the following to run FindBugs on your project:

  * Right click on the project and select **FindBugs > FindBugs**.

The counts of the number of FindBugs notifications will be in parentheses next to each project, package, and class. Details about the notifications will be listed in the **Problems** view of the Java perspective.

Selecting a notification in the **Problems** view will take you to the associated line of code in the editor. Selecting the notification icon in the left gutter of the editor will open a **Bug Info** view that will provide additional details about the notification.


### PMD
Do the following to run PMD on your project:

  * Right click on the project and select **PMD > Check Code**. This will run PMD on your code.

After PMD runs, you will automatically switch to the **PMD perspective**. You can browse the PMD results there. (Switch back to the **Java perspective** by selecting the **Java perspective** icon in the upper right of the workbench.) You can also look at the PMD results in the **Problems** view of the **Java perspective**.

If you want PMD to run every time your program compiles, right click on your project and select **Properties > PMD > Enable PMD**.


### CheckStyle
Do the following to run CheckStyle on your project:

  * Right click on the project and select **CheckStyle > Check Code with CheckStyle**. This will run CheckStyle on your code.

CheckStyle alerts are listed in the **Problems** view of the **Java perspective**.

If you want CheckStyle to run every time your program compiles, right click on your project and select **Properties > CheckStyle > CheckStyle active for this project**.


### Static Analysis Tool Meta Data
Each static analysis tool will create their own set of meta data or configuration files in your project folder.  **These files MAY be pushed to GitHub**.  

If you would prefer to leave them off, you can add the files to the `.gitignore`.  If you're using the Eclipse **Git Staging** view, right click on the file and select **Ignore**.  This will add the file to `.gitignore` and add the `.gitignore` file to the list of unstaged changes.

Also note that your `.project` file also changed.  The `.project` file contains information about the configuration of your project and has been updated to reflect your use of static analysis tools.  **DO NOT IGNORE THE `.project` FILE!!** If the `.project` file is not pushed to GitHub, the teaching staff will not be able to import your project into Eclipse for manual grading of the black box tests!  You will receive a deduction for any manual configuration of your project required to grade your work.  The same applies to the `.classpath` file even though it was not modified by using static analysis tools.

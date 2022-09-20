---
title: Guided Project 1 - Software Development Practices and Tools
tags: [software engineering, software lifecycle, CS2, CSC216, GP1]
description: Guided Task - Code Editing Tools
navigation: on
pagegroup: gp1
---

# Guided Task: Code Editing Tools
{% include iconHeader.html type="task,ideTool" %}
Now that you have seen the power of source code generation and quick fix, you can explore some other Eclipse code editing tools that may be useful as you develop code.

  * [Auto-Complete](#auto-complete)
  * [Code Templates](#code-templates)
  * [Code Formatter](#code-formatter)
  * [Customizing Templates and the Formatter](#customizing-templates-and-the-formatter)
  
{% capture callout_content %} 
  * Explore Eclipse auto-complete
  * Explore Eclipse code templates
  * Explore Eclipse code formatter
{% endcapture %}
{% include callout.html content=callout_content type="learningOutcomes" title="Learning Outcomes" %}

{% capture callout_content %}
Many IDEs have tools that help with common tasks and some of those tools can help you generate code.  You learned how to write these code statements manually in your introductory programming class so that you would fully understand their purpose.  Now, you can use Eclipse's code generation tools to help in writing common statements.  A benefit of using code generation tool, besides saving time, is that the code is more likely to be correct.  However, you should always test the generated code so make sure that it meets the requirements of the larger program.
{% endcapture %}
{% include callout.html content=callout_content icon="ideTool" type="bestPractices" title="Best Practice: IDE Code Generation" %}

{% capture callout_content %}
Formatting of code is also important.  Well formatted code is easier to read and maintain.  Additionally, it easier for others to read - especially if you need help.  Most companies have a set of style guidelines that they expect software engineers to follow when working on a code base to ensure that everyone can read and understand code quickly.  That is why we have a set of style guidelines for code in CSC216 and enforce those guidelines through the static analysis tool, CheckStyle.
{% endcapture %}
{% include callout.html content=callout_content icon="plTool" type="bestPractices" title="Best Practice: Code Formatting and Style" %}
  
 
## Auto-Complete
Eclipse can fix your simple errors. It can also guess what you want to type via the auto-complete tool. The auto-complete tool is especially handy for remembering class, method, and variable names especially when your code has long or complicated variable or method names.

To use auto-complete, start typing a variable or method name and press **Ctrl + Space** or **Cmd + Space**. The auto-complete context menu provides several options for code generation. Select the best option and press **Enter** to generate the code.

Hint: Any time you want to finish something that you think Eclipse can guess, it's worth pressing **Ctrl + Space** or **Cmd + Space** to see if it does. Eclipse will find things like method names, variables in the current scope, class names, or even make suggestions for a variable you're declaring! The idea is that you don't have to remember everything about the program you're writing. You can select the options with the mouse, but it's probably faster to use the arrow keys and the **Enter** key.

 
## Code Templates
Eclipse provides several code templates for commonly used methods and statements. 

To use a code template, start typing in the code template keyword and then press Ctrl+Space.

Some keywords for code templates are:

  * Typing `main` will create a `main` method
  * Typing `sysout` will create a `System.out.println()` statement.
  * There are several `for` code templates that will create `for`-loops.
  * The `foreach` template will search upward from your current location and find the nearest `Iterable` type and create an enhanced `for`-loop over it.
  * Typing `/**` before a method will generate Javadoc, inferring the parameters to your method.  You still have to write the comments that describes what the method does and provide information about the parameters to the method.  Don't write junk!  We do read your comments to ensure they describe your code.

 
## Code Formatter
Additionally, Eclipse can help you keep your code well formatted (which is nice for avoiding loss of style points on your programming assignments).

Once you know that your program works, take a look at your code. Methods should be indented within classes, and statements should be indented within methods. If your code does not follow proper indentation let Eclipse help. Press **Ctrl + Shift + F** (or go to the **Source > Format** in the menu; Mac users try **Cmd + Shift + F**).

 
## Customizing Code Templates and the Formatter
If you want to add/edit code templates for the way your code gets formatted, select **Window > Preferences** (Mac Users select **Eclipse > Preferences**).

For code templates, select **Java > Editor > Templates**. Alternatively, start typing "Code templates" in the top text search box to find the menu.

For the formatter, select **Java > Code Style > Formatter**. Alternatively, start typing "Formatter" in the top text search box to find the menu.

Eclipse defaults to using tabs for indentation.  If you want to switch the tab key to enter spaces rather than a tab, do so by editing the style defined in the **Formatter** properties menu.

{% capture warning %}
 * If your workshop code does not build (your workshop code has a red ball) on Jenkins, you will automatically receive 0 points for the Coding Activity portion of your workshop grade.
 * If teaching staff test cases do not run on Jenkins, you will automatically receive 0 points for the Coding Activity portion of your workshop grade.
 * The output from Jenkins helps you **estimate** your grade. Your grade may be manually adjusted through manual inspection. For example, your grade may be lowered if your submitted artifacts do not satisfy the workshop's learning objectives, if you have poor quality test cases, etc.
 * Please review the course policies on [academic integrity](https://pages.github.ncsu.edu/engr-csc316-staff/DE/syllabus#academic-integrity){:target="_blank"}. Remember that it is better to turn-in *nothing* and receive a 0 rather than committing academic misconduct, receiving a -100%, and being placed on academic probation. If you have any questions about academic integrity or what behaviors are allowed, you must check with the instructor first *before* submitting the assignment.
{% endcapture %}
{% include callout.html type="danger" content=warning title="Important Notes about workshop Grading"%}

Phase | Category | Points Possible | Description                        
---------|-------------|----------------------------------------------
{% include icon.html type="unitTest" %} | **Student Unit Tests** | 20 | [Jenkins](http://go.ncsu.edu/jenkins-csc316){:target="_blank"} will run your unit tests and report the percentage passing.
{% include icon.html type="unitTest" %} | **Student Test Coverage** | 25 | [Jenkins](http://go.ncsu.edu/jenkins-csc316){:target="_blank"} will evaluate the statement coverage of your test cases. You are expected to have 80% statement coverage of each non-UI class. To calculate this score, the coverage percentage of any class with less than 80% coverage will be divided by 80. This will be added to the scores for other classes. If a class has 80% or higher coverage, a value of 1 will be used. The sum of scores will then be divided by the number of model classes and multiplied by 25 for this portion of your score. For example, if the project has three model classes and Class1 has 90% statement coverage, Class2 has 85% coverage and Class3 has 76% coverage, the score would be calculated as: 1 + 1 + (76 / 80) = 1 + 1 + .95 = 2.95 / 3 = .98 * 25 = 24.5
{% include icon.html type="implementation" %} | **Static Analysis & Style** | 5 | [Jenkins](http://go.ncsu.edu/jenkins-csc316){:target="_blank"} will run SpotBugs, PMD, and CheckStyle on your submission. Each "Scary" or "Scariest" SpotBugs notification or infraction of the [Departmental Style Guidelines](https://pages.github.ncsu.edu/engr-csc116-staff/CSC116-Materials/course-resources/style-guidelines/){:target="_blank"} as recorded by PMD and CheckStyle will result in the deduction of 1 point until all points in this category are exhausted.
**Coding Activity TOTAL** | | 50 | The total will be determined by the following formula: (**Student Unit Tests** + **Student Test Coverage** + **Static Analysis & Style**) X (**Passing Teaching Staff JUnit Tests/Total Teaching Staff JUnit Tests**) |

<br>


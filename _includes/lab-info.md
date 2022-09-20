Lab Section | Meeting Times | Meeting Location | Lab Deadline | Jenkins Link              
------------|---------------|------------------|--------------|-------------
{% for section in site.data.courseInfo.labSections %}
      {{ section.name }} | {{section.time}} | {{section.location}} | {{section.deadline}} | [ | {{section.jenkins-url}}]({{section.jenkins-url}})
{% endfor %}
# {{ site.data.courseInfo.shortName }} - {{ site.data.courseInfo.name }} ({{ site.data.courseInfo.semester }})

**Course description:** {{ site.data.courseInfo.description }}
*Prerequisites:* {% for item in site.data.courseInfo.prerequisites %}*{{item}}* {% endfor %}.
*Corequisites:* {% for item in site.data.courseInfo.corequisites %}*{{item}}* {% endfor %}.

## Navigation
<div class="expand dashboard">
<details><summary>CSC 217 Course Materials & Logistics - {{ site.data.courseInfo.semester }}</summary>
{% include cardRow.html data=site.data.courseInfo.logistics type="" %}
</details>
</div>

<div class="expand dashboard">
<details><summary>Lab Section Information</summary>

{% include lab-info.html %}

</details>
</div>

<div class="expand dashboard">	
<details><summary>Support - Tools & Teaching Staff</summary>
{% include cardRow.html data=site.data.courseInfo.support type="" %}

<p style="font-size:1.5em">Instructors</p>
{% include cardRow.html data=site.data.courseInfo.instructor type="staff" %}

<p style="font-size:1.5em">Peer Teaching Fellows</p>
{% include cardRow.html data=site.data.courseInfo.staff type="staff" %}

<p style="font-size:1.5em">Upcoming Office Hours</p>
{% include googleCalendar.html url=site.data.courseInfo.officeHourCalendar.url %}
{% include calendar.html %}
</details>
</div>	


<div class="expand dashboard"> 
 <details><summary>Archive</summary>
  {% include cardRow.html data=site.data.courseInfo.archive type="" %}
 </details>
</div>
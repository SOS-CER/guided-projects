<table>
<thead>
<tr>
	<td><strong>Learning Objective</strong></td>
	<td><strong>W1</strong></td>
	<td><strong>W2</strong></td>
	<td><strong>W3</strong></td>
	<td><strong>W4</strong></td>
	<td><strong>W5</strong></td>
	<td><strong>W6</strong></td>
	<td><strong>W7</strong></td>
	<td><strong>W8</strong></td>
	<td><strong>W9</strong></td>
	<td><strong>W10</strong></td>
	<td><strong>W11</strong></td>
	<td><strong>W12</strong></td>
	<td><strong>Project</strong></td>
</tr>
</thead>
<tbody>
{% for obj in site.data.objectives %}
<tr>
<td>{{obj.id}}: {{obj.text}}</td>
<td>{%if obj.assignments contains "W01" %}<span class="glyphicon glyphicon-check" data-alt="checkmark"></span>{% endif %}</td>
<td>{%if obj.assignments contains "W02" %}<span class="glyphicon glyphicon-check" data-alt="checkmark"></span>{% endif %}</td>
<td>{%if obj.assignments contains "W03" %}<span class="glyphicon glyphicon-check" data-alt="checkmark"></span>{% endif %}</td>
<td>{%if obj.assignments contains "W04" %}<span class="glyphicon glyphicon-check" data-alt="checkmark"></span>{% endif %}</td>
<td>{%if obj.assignments contains "W05" %}<span class="glyphicon glyphicon-check" data-alt="checkmark"></span>{% endif %}</td>
<td>{%if obj.assignments contains "W06" %}<span class="glyphicon glyphicon-check" data-alt="checkmark"></span>{% endif %}</td>
<td>{%if obj.assignments contains "W07" %}<span class="glyphicon glyphicon-check" data-alt="checkmark"></span>{% endif %}</td>
<td>{%if obj.assignments contains "W08" %}<span class="glyphicon glyphicon-check" data-alt="checkmark"></span>{% endif %}</td>
<td>{%if obj.assignments contains "W09" %}<span class="glyphicon glyphicon-check" data-alt="checkmark"></span>{% endif %}</td>
<td>{%if obj.assignments contains "W10" %}<span class="glyphicon glyphicon-check" data-alt="checkmark"></span>{% endif %}</td>
<td>{%if obj.assignments contains "W11" %}<span class="glyphicon glyphicon-check" data-alt="checkmark"></span>{% endif %}</td>
<td>{%if obj.assignments contains "W12" %}<span class="glyphicon glyphicon-check" data-alt="checkmark"></span>{% endif %}</td>
<td>{%if obj.assignments contains "P" %}<span class="glyphicon glyphicon-check" data-alt="checkmark"></span>{% endif %}</td>
</tr>
{% endfor %}
</tbody>
</table>
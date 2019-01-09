---
title: Send Document - User stories
keywords: 
tags: [messaging]
sidebar: senddocument_sidebar
permalink: senddocument_userstories2.html
summary: "Mock-up for user stories"
toc: false
---

## Purpose ##

The purpose of this page is to document the user stories that apply across all of GP Connect Send Document capability. To avoid duplication links to the requirements within the specification have be provided where applicable.



<div>
{% assign stories = site.data.senddoc_user_stories | sort:'id' %}
{% for item in stories %}

<h2> {{item.title}} </h2>

<table class='resource-attributes'>
  <tr>
	<td><strong>ID: </strong><code>{{item.id}}</code></td>
	<td><strong>Source: </strong>{{item.source}}</td>
  </tr>
</table>

<div>
	<div>	
		<p><strong>Description</strong></p>
		<p style="margin-left: 30px"><em>As <strong>{{item.as}}</strong>...</em></p>
		<p style="margin-left: 30px"><em>I want <strong>{{item.iwant}}</strong>...</em></p>
		<p style="margin-left: 30px"><em>so that <strong>{{item.sothat}}</strong></em></p>
		<br/>
	</div>

	<div>	
		<p><strong>Acceptance criteria - provider</strong></p>
		{{item.provider}}
		<br/>
	</div>

	<div>	
		<p><strong>Acceptance criteria - consumer</strong></p>
		{{item.consumer}}
	</div>
	<hr style="width:100%">
</div>


{% endfor %}



<div>
<table>
  {% for item in site.data.senddoc_requirements.requirements %}
  <tr class="newlines">
    <td id="{{item.id}}">{{item.id}}</td>
    <td><a href="senddocument_payload.html#{{item.id}}" data-toggle="tooltip" data-original-title="{{item.tooltip}}">{{item.id}}</a></td>
  </tr>
  {% endfor %}
</table>


</div>


<table>
  {% for item in site.data.glossary.glossary %}
  {% if item.title == 'Spine' %}
  <tr>
    <td title="{{item.title}}">{{item.title}}</td>
    <td>{{item.value}}</td>
  </tr>
  {% endif %}
  {% endfor %}
</table>


{% for item in site.data.glossary.glossary %}
	{% if item.title == 'Spine' %}
		<a href="overview_glossary.html#spine" data-toggle="tooltip" data-original-title="{{item.value}}">{{item.title}}</a>
	{% endif %}
{% endfor %}
  

 <hr> 
  
include text {% include tooltip.html type="Spine" %}on each side
<br/>
{% include tooltip.html type="FHIR&reg;" %} 
<br/>
{% include tooltip.html type="Clinical safety" %} 
<br/>
{% include tooltip.html type="First of Type (FoT)" %} 

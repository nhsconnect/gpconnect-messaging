---
title: User stories
keywords: use-case, send-document, messaging
tags: [use-case, send-document, messaging]
sidebar: senddocument_sidebar
permalink: senddocument_userstories.html
summary: "User stories for Send Federated Consultation Report"
toc: true
---


## Purpose ##

The purpose of this page is to document the user stories that apply across all of GP Connect Send Document capability. To avoid duplication links to the requirements within the specification have be provided where applicable.

## User stories ##

<div>
{% assign stories = site.data.senddoc_user_stories | sort:'id' %}
{% for item in stories %}

<h3> {{item.title}} </h3>

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
		<p><strong>Acceptance criteria - sender</strong></p>
		{{item.sender}}
		<br/>
	</div>

	<div>	
		<p><strong>Acceptance criteria - receiver</strong></p>
		{{item.receiver}}
	</div>
	
	<div class="bs-callout bs-callout-success">
		<strong>Linked requirements: </strong>{% include requirement.html type=item.requirement1 %} {% include requirement.html type=item.requirement2 %} {% include requirement.html type=item.requirement3 %} {% include requirement.html type=item.requirement4 %} {% include requirement.html type=item.requirement5 %} {% include requirement.html type=item.requirement6 %}
	</div>

	<hr style="width:100%">
	
</div>

{% endfor %}
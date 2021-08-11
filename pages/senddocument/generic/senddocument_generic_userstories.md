---
title: User stories
keywords: use-case, send-document, messaging
tags: [use-case, send-document, messaging]
sidebar: senddocument_sidebar
permalink: senddocument_generic_userstories.html
summary: "User stories for Generic payload"
toc: true
---


## Purpose ##

The purpose of this page is to document the user stories that apply to the Generic use case.

## User stories ##

<div>
{% assign stories = site.data.oc_user_stories | sort:'id' %}
{% for item in stories %}

<h3> {{item.title}} </h3>

<table class='resource-attributes'>
  <tr>
	<td><strong>ID: </strong><code>{{item.id}}</code></td>
	<td><strong>Source: </strong>{{item.source}}</td>
  </tr>
</table>


	<div>	
		<p><strong>Description</strong></p>
		<p style="margin-left: 20px"><em>As <strong>{{item.as}}</strong>...</em></p>
		<p style="margin-left: 20px"><em>I want <strong>{{item.iwant}}</strong>...</em></p>
		<p style="margin-left: 20px"><em>so that <strong>{{item.sothat}}</strong></em></p>
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
	<div>	
		{{item.notes}}
	</div>	
	<div class="bs-callout bs-callout-primary">
		<p><strong>Requirements references:</strong></p>
		<p style="font-size:14px">{{item.technical}}</p>
	</div>
	
	<hr style="width:100%">
		


{% endfor %}

---
title: Requirements list
keywords: use-case
tags: [use-case, send-document]
sidebar: senddocument_sidebar
permalink: senddocument_generic_reqs.html
summary: "All requirements associated with Generic payload"
toc: false
---

## List of all requirements ##

The following table contains all the requirements associated with the Send Document capability. Each row contains a link to requirement within the specification and the requirement description for a quick reference:


<table class="requirement-box">
<tr>
	<th>Link</th>
	<th>Requirement description</th>
</tr>	
  {% for item in site.data.oc_requirements.requirements %}
  <tr>
    <td><a href="{{item.page}}#{{item.id}}">{{item.id}}</a></td>
    <td>{{item.description}}</td>
  </tr>
  {% endfor %}
</table>


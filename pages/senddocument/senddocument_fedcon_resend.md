---
title: Document Replacement
keywords: document, mesh
tags: [messaging, mesh, send-document]
sidebar: senddocument_sidebar
permalink: senddocument_fedcon_resend.html
summary: "Document replacement semantics for Send Document"
---

The Send Document capability allows for the replacement of a previously sent document. This replacement is at a whole document level, in that the original document is replaced by a new one and the old document is only kept for audit purposes. A sender may choose to send a new replacement document for a number of reasons, for example:

- the original document contained an error - identified after the document sent
- the sender has more up-to-date or complete information - the original is correct but further information is now available to make the document more complete or detailed

<table class="requirement-box">
  {% for item in site.data.senddoc_requirements.requirements %}
  {% if item.area == 'resend' %}
  <tr>
    <td id="{{item.id}}">{{item.id}}</td>
    <td>{{item.description}}</td>
  </tr>
  {% endif %}
  {% endfor %}
</table>


When the new document cannot be processed then:

<table class="requirement-box">
  {% for item in site.data.senddoc_requirements.requirements %}
  {% if item.area == 'resend2' %}
  <tr>
    <td id="{{item.id}}">{{item.id}}</td>
    <td>{{item.description}}</td>
  </tr>
  {% endif %}
  {% endfor %}
</table>

Replacement guidance:

<table class="requirement-box">
  {% for item in site.data.senddoc_requirements.requirements %}
  {% if item.area == 'resend3' %}
  <tr>
    <td id="{{item.id}}">{{item.id}}</td>
    <td>{{item.description}}</td>
  </tr>
  {% endif %}
  {% endfor %}
</table>

FHIR&reg; elements used for replacement:

<table class="requirement-box">
  {% for item in site.data.senddoc_requirements.requirements %}
  {% if item.area == 'resend4' %}
  <tr>
    <td id="{{item.id}}">{{item.id}}</td>
    <td>{{item.description}}</td>
  </tr>
  {% endif %}
  {% endfor %}
</table>





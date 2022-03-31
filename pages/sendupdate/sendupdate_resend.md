---
title: Update Replacement
keywords: update, mesh
tags: [messaging, mesh, send-update]
sidebar: sendupdate_sidebar
permalink: sendupdate_resend.html
summary: "Replacement semantics for Send Update"
---

The Send Update capability allows for the replacement of a previously sent message. This replacement is at a whole message level, in that the original message is replaced by a new one and the old message is only kept for audit purposes. A sender may choose to send a new replacement message for a number of reasons, for example:

- the original message contained an error - identified after the message sent
- the sender has more up-to-date or complete information - the original is correct but further information is now available to make the message more complete or detailed

<table class="requirement-box">
  {% for item in site.data.sendupdate_requirements.requirements %}
  {% if item.area == 'resend' %}
  <tr>
    <td id="{{item.id}}">{{item.id}}</td>
    <td>{{item.description}}</td>
  </tr>
  {% endif %}
  {% endfor %}
</table>


When the new message cannot be processed then:

<table class="requirement-box">
  {% for item in site.data.sendupdate_requirements.requirements %}
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
  {% for item in site.data.sendupdate_requirements.requirements %}
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
  {% for item in site.data.sendupdate_requirements.requirements %}
  {% if item.area == 'resend4' %}
  <tr>
    <td id="{{item.id}}">{{item.id}}</td>
    <td>{{item.description}}</td>
  </tr>
  {% endif %}
  {% endfor %}
</table>





---
title: Triggering message creation
keywords: send-document
tags: [send-document]
sidebar: senddocument_sidebar
permalink: senddocument_fedcon_trigger.html
summary: "Options for triggering the creation of a consultation report message"
---


This page provides guidance on how systems which send a consultation report should initiate the message creation action.

## Guiding principles ##

The following two principles should guide the implementation choice:

<table class="requirement-box">
  {% for item in site.data.senddoc_requirements.requirements %}
  {% if item.area == 'trigger' %}
  <tr>
    <td id="{{item.id}}">{{item.id}}</td>
    <td>{{item.description}}</td>
  </tr>
  {% endif %}
  {% endfor %}
</table>

## Recommended solution ##

The following solution is presented as the preferred option:

### Automated message creation ###

The message creation process is hidden from the clinician – in a similar way that synchronisation with Summary Care Record (SCR) takes place without the involvement of a clinician, the GP principal clinical system is responsible for the background task of ensuring that the registered practice record is updated.

Where the encounter details at a practice are updated later (for example, at the end of a clinic), an additional message would result to ensure that the latest complete picture of the encounter was made available to the registered practice. Note that each additional encounter summary message would contain a complete encounter summary, and not simply the delta to the previous instance.

The trigger for the background process would be at or near the time when a practice encounter is saved.

Any additional consultation report could be clearly marked as such. As the GUID of the encounter is present in the ITK3 SenderReference field, all messages associated with that encounter can be identified.

As the process to generate and send a consultation report is automated, message priority cannot be set, as this would require a review by the clinician. As a result, the message priority of all messages for this use case will be set to `routine` indicating that the practice is simply requesting that information about the practice encounter be attached to the registered practice record.

Where specific actions are required at the registered practice as a result of the encounter, the practice clinician will follow existing business processes.
 
## Defining whether message should be sent ##

Irrespective of the means of triggering message creation, the first step the sending system must perform is to ascertain whether a message must be sent to the registered practice.

The message sender performs the following steps to ascertain whether a message should be sent to the registered practice:

<table class="requirement-box">
  {% for item in site.data.senddoc_requirements.requirements %}
  {% if item.area == 'trigger2' %}
  <tr>
    <td id="{{item.id}}">{{item.id}}</td>
    <td>{{item.description}}</td>
  </tr>
  {% endif %}
  {% endfor %}
</table>

In a scenario where both the sending and receiving practice are operating the same GP principal clinical system, updating the registered practice may be performed directly within that system infrastructure.

## Defining when message should be sent ##

The message sender <strong>MUST</strong> fulfil these time period requirements:

<table class="requirement-box">
  {% for item in site.data.senddoc_requirements.requirements %}
  {% if item.area == 'trigger3' %}
  <tr>
    <td id="{{item.id}}">{{item.id}}</td>
    <td>{{item.description}}</td>
  </tr>
  {% endif %}
  {% endfor %}
</table>

## Dealing with deleted consultations ##

Deletions are rare but do happen. For example, where a consultation was recorded against the wrong patient. In the event of a deletion the following sender requirement <strong>MUST</strong> be fulfilled:

<table class="requirement-box">
  {% for item in site.data.senddoc_requirements.requirements %}
  {% if item.area == 'trigger4' %}
  <tr>
    <td id="{{item.id}}">{{item.id}}</td>
    <td>{{item.description}}</td>
  </tr>
  {% endif %}
  {% endfor %}
</table>

{% include note.html content="It is the responsibility of the GP practice that recorded the consultation to inform the registered GP practice. There is no requirement for the sending system to send an automated message to inform the registered GP practice about the deletion. The sender system should assist the GP practice in managing and tracking the process of informing other organisations." %} 

## PDF Format and business process ##

Please refer to [Send Consultation Report - Business Requirements](senddocument_userstories.html) for business requirement context for the creation of the message together with details of the PDF format to be used.


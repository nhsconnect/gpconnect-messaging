---
title: Payload requirements
keywords: use-case
tags: [use-case, send-document]
sidebar: senddocument_sidebar
permalink: senddocument_fedcon_payload.html
summary: "Details of the FHIR resources which make up the payload for the Send Federated Consultation Report use case."
---


Please refer to [Send Document - Payload structure](senddocument_payload) for a definition of the payload structure to be used to fulfil the [Send Federated Consultation Report](/senddocument_fedcon_overview.html#federated-appointments-use-case) use case.

The following sections describe the resources which form the payload. i.e. the resources which will be present as entries of the [ITK-Payload-Bundle](https://fhir.nhs.uk/STU3/StructureDefinition/ITK-Payload-Bundle-1) resource which acts as a container for the payload. 

A [message example](senddocument_payload) is provided which illustrates these requirements to aid understanding.

## Task resource ##

<table class="requirement-box">
  {% for item in site.data.senddoc_requirements.requirements %}
  {% if item.area == 'payload' %}
  <tr>
    <td id="{{item.id}}">{{item.id}}</td>
    <td>{{item.description}}</td>
  </tr>
  {% endif %}
  {% endfor %}
</table>

The following requirements describe how the Task resource is populated:

<table class="requirement-box">
  {% for item in site.data.senddoc_requirements.requirements %}
  {% if item.area == 'payload1' %}
  <tr>
    <td id="{{item.id}}">{{item.id}}</td>
    <td>{{item.description}}</td>
  </tr>
  {% endif %}
  {% endfor %}
</table>

### Including binary documents in the payload ###

[Send Document - Including documents in the payload](/senddocument_fedcon_payload.html#including-binary-documents-in-the-payload) defines how binary documents are included in the Send Document payload.

For this use case, the following specific requirements apply:

**Federated Consultation Report** <br/>

Message senders will include the federated consultation report as an instance of the task.input element as described in [Send Document - payload structure](senddocument_payload.html#including-documents-in-the-payload).

<table class="requirement-box">
  {% for item in site.data.senddoc_requirements.requirements %}
  {% if item.area == 'payload2' %}
  <tr>
    <td id="{{item.id}}">{{item.id}}</td>
    <td>{{item.description}}</td>
  </tr>
  {% endif %}
  {% endfor %}
</table>
	
<br/>
**Additional input elements**

Message senders **MAY** include additional binary documents in the payload as each expressed as an additional instance of the task.input as described in [Send Document - payload structure](senddocument_payload.html#including-documents-in-the-payload).

<table class="requirement-box">
  {% for item in site.data.senddoc_requirements.requirements %}
  {% if item.area == 'payload3' %}
  <tr>
    <td id="{{item.id}}">{{item.id}}</td>
    <td>{{item.description}}</td>
  </tr>
  {% endif %}
  {% endfor %}
</table>

## Organization resources ##

<table class="requirement-box">
  {% for item in site.data.senddoc_requirements.requirements %}
  {% if item.area == 'payload4' %}
  <tr>
    <td id="{{item.id}}">{{item.id}}</td>
    <td>{{item.description}}</td>
  </tr>
  {% endif %}
  {% endfor %}
</table>

The table below outlines how these resources are populated:

<table class="requirement-box">
  {% for item in site.data.senddoc_requirements.requirements %}
  {% if item.area == 'payload5' %}
  <tr>
    <td id="{{item.id}}">{{item.id}}</td>
    <td>{{item.description}}</td>
  </tr>
  {% endif %}
  {% endfor %}
</table>

## Practitioner resource ##

The [CareConnect-Practitioner-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Practitioner-1) resource present in the payload is populated as follows:

<table class="requirement-box">
  {% for item in site.data.senddoc_requirements.requirements %}
  {% if item.area == 'payload6' %}
  <tr>
    <td id="{{item.id}}">{{item.id}}</td>
    <td>{{item.description}}</td>
  </tr>
  {% endif %}
  {% endfor %}
</table>

## Patient resource ##

The [CareConnect-Patient-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Patient-1) in the payload is populated as follows:

<table class="requirement-box">
  {% for item in site.data.senddoc_requirements.requirements %}
  {% if item.area == 'payload7' %}
  <tr>
    <td id="{{item.id}}">{{item.id}}</td>
    <td>{{item.description}}</td>
  </tr>
  {% endif %}
  {% endfor %}
</table>

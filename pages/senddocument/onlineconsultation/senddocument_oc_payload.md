---
title: Payload requirements
keywords: use-case
tags: [use-case, send-document]
sidebar: senddocument_sidebar
permalink: senddocument_oc_payload.html
summary: "Details of the FHIR&reg; resources which make up the payload for the Online Consultation Report use case."
---

Please refer to [Send Document - Payload structure](senddocument_payload) for a definition of the payload structure to be used to fulfil the Online Consultation use case.

The following sections describe the resources which form the payload. These are the resources that will be present as entries of the [ITK-Payload-Bundle](https://fhir.nhs.uk/STU3/StructureDefinition/ITK-Payload-Bundle-1) resource, which acts as a container for the payload. 

A [message example](senddocument_oc_example) is provided which illustrates these requirements to aid understanding.

## Composition resource ##

<table class="requirement-box">
  {% for item in site.data.oc_requirements.requirements %}
  {% if item.area == 'payload' %}
  <tr>
    <td id="{{item.id}}">{{item.id}}</td>
    <td>{{item.description}}</td>
  </tr>
  {% endif %}
  {% endfor %}
</table>

The following requirements describe how the Composition resource is populated:

<table class="requirement-box">
  {% for item in site.data.oc_requirements.requirements %}
  {% if item.area == 'payload1' %}
  <tr>
    <td id="{{item.id}}">{{item.id}}</td>
    <td>{{item.description}}</td>
  </tr>
  {% endif %}
  {% endfor %}
</table>
	

<br/>

**Additional input elements**

Message senders **MAY** include additional binary documents in the payload as each expressed as an additional instance of the composition.section as described in [Send Document - payload structure](senddocument_payload.html#including-documents-in-the-payload).

<table class="requirement-box">
  {% for item in site.data.oc_requirements.requirements %}
  {% if item.area == 'payload3' %}
  <tr>
    <td id="{{item.id}}">{{item.id}}</td>
    <td>{{item.description}}</td>
  </tr>
  {% endif %}
  {% endfor %}
</table>

## Patient resource ##

<table class="requirement-box">
  {% for item in site.data.oc_requirements.requirements %}
  {% if item.area == 'payload8a' %}
  <tr>
    <td id="{{item.id}}">{{item.id}}</td>
    <td>{{item.description}}</td>
  </tr>
  {% endif %}
  {% endfor %}
</table>

The [CareConnect-Patient-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Patient-1) in the payload is populated as follows:

<table class="requirement-box">
  {% for item in site.data.oc_requirements.requirements %}
  {% if item.area == 'payload8' %}
  <tr>
    <td id="{{item.id}}">{{item.id}}</td>
    <td>{{item.description}}</td>
  </tr>
  {% endif %}
  {% endfor %}
</table>

## Organization resource ##

<table class="requirement-box">
  {% for item in site.data.oc_requirements.requirements %}
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
  {% for item in site.data.oc_requirements.requirements %}
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
  {% for item in site.data.oc_requirements.requirements %}
  {% if item.area == 'payload6' %}
  <tr>
    <td id="{{item.id}}">{{item.id}}</td>
    <td>{{item.description}}</td>
  </tr>
  {% endif %}
  {% endfor %}
</table>

## Device resource ##

The [GPConnect-Device-1](https://fhir.nhs.uk/STU3/StructureDefinition/GPConnect-Device-1) resource present in the payload is populated as follows:

<table class="requirement-box">
  {% for item in site.data.oc_requirements.requirements %}
  {% if item.area == 'payload7' %}
  <tr>
    <td id="{{item.id}}">{{item.id}}</td>
    <td>{{item.description}}</td>
  </tr>
  {% endif %}
  {% endfor %}
</table>


## Observation resource ##

The [CareConnect-GPC-List-1](https://fhir.nhs.uk/STU3/StructureDefinition/CareConnect-GPC-List-1) in the payload is populated as follows:

<table class="requirement-box">
  {% for item in site.data.oc_requirements.requirements %}
  {% if item.area == 'payload9a' %}
  <tr>
    <td id="{{item.id}}">{{item.id}}</td>
    <td>{{item.description}}</td>
  </tr>
  {% endif %}
  {% endfor %}
</table>

Each [CareConnect-GPC-Observation-1](https://fhir.nhs.uk/STU3/StructureDefinition/CareConnect-GPC-Observation-1) in the payload is populated as follows:

<table class="requirement-box">
  {% for item in site.data.oc_requirements.requirements %}
  {% if item.area == 'payload9' %}
  <tr>
    <td id="{{item.id}}">{{item.id}}</td>
    <td>{{item.description}}</td>
  </tr>
  {% endif %}
  {% endfor %}
</table>


## QuestionnaireResponse resource ##

The [CareConnect-GPC-QuestionnaireResponse-1](https://fhir.nhs.uk/STU3/StructureDefinition/CareConnect-GPC-QuestionnaireResponse-1) in the payload is populated as follows:

<table class="requirement-box">
  {% for item in site.data.oc_requirements.requirements %}
  {% if item.area == 'payload10' %}
  <tr>
    <td id="{{item.id}}">{{item.id}}</td>
    <td>{{item.description}}</td>
  </tr>
  {% endif %}
  {% endfor %}
</table>

## Location resource ##

The [CareConnect-GPC-Location-1](https://fhir.nhs.uk/STU3/StructureDefinition/CareConnect-GPC-Location-1) in the payload is populated as follows:

<table class="requirement-box">
  {% for item in site.data.oc_requirements.requirements %}
  {% if item.area == 'payload11' %}
  <tr>
    <td id="{{item.id}}">{{item.id}}</td>
    <td>{{item.description}}</td>
  </tr>
  {% endif %}
  {% endfor %}
</table>

## Consent resource ##

The [CONSENT??]() in the payload is populated as follows:

<table class="requirement-box">
  {% for item in site.data.oc_requirements.requirements %}
  {% if item.area == 'payload12' %}
  <tr>
    <td id="{{item.id}}">{{item.id}}</td>
    <td>{{item.description}}</td>
  </tr>
  {% endif %}
  {% endfor %}
</table>

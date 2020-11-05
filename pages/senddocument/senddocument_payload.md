---
title: Send Document - payload structure
keywords: document, payload
tags: [send-document]
sidebar: senddocument_sidebar
permalink: senddocument_payload.html
summary: "Send Document capability - the structure of the payload to be used for all use cases of the Send Document capability"
---

## Payload message requirements ##

The following requirements describe the structure of the Send Document payload:

<table class="requirement-box">
  {% for item in site.data.senddoc_requirements.requirements %}
  {% if item.area == 'senddocpayload' %}
  <tr>
    <td id="{{item.id}}">{{item.id}}</td>
    <td>{{item.description}}</td>
  </tr>
  {% endif %}
  {% endfor %}
</table>


### Including documents in the payload ###

The following requirements describe how binary documents are included in the payload:

<table class="requirement-box">
  {% for item in site.data.senddoc_requirements.requirements %}
  {% if item.area == 'senddocpayload2' %}
  <tr>
    <td id="{{item.id}}">{{item.id}}</td>
    <td>{{item.description}}</td>
  </tr>
  {% endif %}
  {% endfor %}
</table>

Each instance of a binary document will be included as follows:

<table class="requirement-box">
  {% for item in site.data.senddoc_requirements.requirements %}
  {% if item.area == 'senddocpayload3' %}
  <tr>
    <td id="{{item.id}}">{{item.id}}</td>
    <td>{{item.description}}</td>
  </tr>
  {% endif %}
  {% endfor %}
</table>


### Including structured Observations in the payload ###

{% include warning.html content="The requirements below have been introduced to support the **COVID-19 pandemic**. All COVID-19 related codes **MUST** be sent as an Observation within the payload." %} 

The following requirements describe how structured Observations are included in the payload:

<table class="requirement-box">
  {% for item in site.data.senddoc_requirements.requirements %}
  {% if item.area == 'urgent' %}
  <tr>
    <td id="{{item.id}}">{{item.id}}</td>
    <td>{{item.description}}</td>
  </tr>
  {% endif %}
  {% endfor %}
</table>

Each instance of an Observation will be included as follows:

<table class="requirement-box">
  {% for item in site.data.senddoc_requirements.requirements %}
  {% if item.area == 'urgent1' %}
  <tr>
    <td id="{{item.id}}">{{item.id}}</td>
    <td>{{item.description}}</td>
  </tr>
  {% endif %}
  {% endfor %}
</table>


<br>

{% include note.html content="Please refer to the particular use case in question for detailed requirements on the population of these payload resources. Example FHIR&reg; Messages illustrating how payloads look on-the-wire are available for each use case." %} 


### Identifying the use case ###

The ITK3 message handling key `LocalExtension` is used to define the health or social care use case associated with the Send Document message. Please refer to the ITK3 header requirements for your particular use case.   


## Payload message illustration ##

The payload of a GP Connect message which uses the Send Document capability **MUST** have the structure illustrated in the diagram below:

<object type="image/svg+xml" data="images/senddocument/payload.svg" style="max-width:100%;max-height:100%;" alt="Payload message illustration"></object>
<br/>


## Payload message definition ##

The FHIR MessageDefinition resource provides a formal, machine-readable definition of a message shared between systems. Please refer to [ITK3 Message Definitions](https://developer.nhs.uk/apis/itk3messagedistribution-2-5-0/explore_defs_overview.html) for an overview of how MessageDefinition resources are used in ITK3 messages.

The GP Connect Send Document capability has defined a MessageDefinition resource instance which describes the *payload* of the FHIR Message, as defined at [ITK3 Message Definition Patterns](https://developer.nhs.uk/apis/itk3messagedistribution-2-5-0/explore_defs_overview.html#message-definition-patterns).

The Message Definition for the GP Connect Send Document message payload is provided below. This definition can be used by FHIR tools such as [FHIR Check](http://clarotech.co.uk/products/tool-fhir-check/) to verify that particular instance of a Send Document message is conformant. 

{% include senddocument/definition.xml %}

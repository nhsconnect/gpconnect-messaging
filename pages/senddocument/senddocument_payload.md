---
title: Send Document - payload structure
keywords: document, payload
tags: [send-document]
sidebar: senddocument_sidebar
permalink: senddocument_payload.html
summary: "Send Document capability - The structure of the payload to be used for all use cases of the Send Document capability."
---

## Payload message requirements ##

{% include callout.html content="The Send Document payload recognises that for most scenarios messages which are intended to update target organisations' records will result in a task being created in the target system workflow. As a result, the Task resource is used to describe the intent of the message - to request that a task be created in the target organisation to review and perform an update." type="info" %}

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

Each instance of an binary document will be included as follows:

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

The GPConnect-DocumentReference-1 resource will be specified as follows:

<table class="requirement-box">
  {% for item in site.data.senddoc_requirements.requirements %}
  {% if item.area == 'senddocpayload4' %}
  <tr>
    <td id="{{item.id}}">{{item.id}}</td>
    <td>{{item.description}}</td>
  </tr>
  {% endif %}
  {% endfor %}
</table>

<br>

{% include note.html content="Please refer to the particular use case in question for detailed requirements on the population of these payload resources. Example FHIR Messages illustrating how payloads look on-the-wire are available for each use case." %} 

### Identifying the use case ###

The ITK3 message handling key `LocalExtension` is used to define the health or social care use case associated with the Send Document message. Please refer to the ITK3 header requirements for your particular use case.   


## Payload message illustration ##

The payload of a GP Connect message which uses the Send Document capability **MUST** have the structure illustrated in the diagram below. (Context for the Send Federated Consultation Report use case is given in parentheses.).

![Send Document - Payload](images/senddocument/senddocument_payload.PNG "Send Document - Payload message illustration") 

## Payload message definition ##

The FHIR MessageDefinition resource provides a formal, machine-readable definition of a message shared between systems. Please refer to [ITK3 Message Definitions](https://developer.nhs.uk/apis/itk3messagedistribution-2-5-0/explore_defs_overview.html) for an overview of how MessageDefinition resources are used in ITK3 messages.

The GP Connect Send Document capability has defined a MessageDefinition resource instance which describes the *payload* of the FHIR Message, as defined on at [ITK3 Message Definition Patterns](https://developer.nhs.uk/apis/itk3messagedistribution-2-5-0/explore_defs_overview.html#message-definition-patterns)

The Message Definition for the GP Connect Send Document message payload is provided below. This definition can be used by FHIR tools such as [FHIR Check](http://clarotech.co.uk/products/tool-fhir-check/) to verify that particular instance of a Send Document message is conformant. 

{% include senddocument/Message_definition.xml %}
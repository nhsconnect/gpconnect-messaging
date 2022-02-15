---
title: Send Update - payload structure
keywords: update, payload
tags: [send-update]
sidebar: sendupdate_sidebar
permalink: sendupdate_payload_structure.html
summary: "Send Update capability - the structure of the payload to be used for all use cases of the Send Update capability"
---

## Payload message requirements ##

The following requirements describe the structure of the Send Update payload. These requirements are applicable to each use case covered in the specification:

<table class="requirement-box">
  {% for item in site.data.sendupdate_requirements.requirements %}
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
  {% for item in site.data.sendupdate_requirements.requirements %}
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
  {% for item in site.data.sendupdate_requirements.requirements %}
  {% if item.area == 'senddocpayload3' %}
  <tr>
    <td id="{{item.id}}">{{item.id}}</td>
    <td>{{item.description}}</td>
  </tr>
  {% endif %}
  {% endfor %}
</table>


{% include note.html content="Please refer to the particular use case in question for detailed requirements on the population of these payload resources. Example FHIR&reg; Messages illustrating how payloads look on-the-wire are available for each use case." %} 


### Identifying the use case ###

The ITK3 message handling key `LocalExtension` is used to define the health or social care use case associated with the Send Document message. Please refer to the ITK3 header requirements for your particular use case.   


## Payload message illustration ##

The payload of a GP Connect message which uses the Send Document capability **MUST** have the structure illustrated in the diagram below, as described in the sections above:

<br/>
<object type="image/svg+xml" data="images/senddocument/payload.svg">
    <!-- Your fall back here -->
    <img src="images/senddocument/payload.png" usemap="#image-map"/>
	
<map name="image-map">
    <area target="_self" alt="CareConnect-Patient-1" title="CareConnect-Patient-1" href="https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Patient-1" coords="230,343,11,281" shape="rect">
</map>
	
</object>
<br/>



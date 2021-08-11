---
title: MESH message configuration
keywords: document, mesh
tags: [messaging, mesh, send-document]
sidebar: senddocument_sidebar
permalink: senddocument_fedcon_mesh.html
summary: "MESH configuration"
---

Please refer to [Integration to MESH](integration_mesh.html) for an introduction to the use of MESH for GP Connect Messaging use cases.

## MESH message routing ##

<table class="requirement-box">
  {% for item in site.data.senddoc_requirements.requirements %}
  {% if item.area == 'mesh' %}
  <tr>
    <td id="{{item.id}}">{{item.id}}</td>
    <td>{{item.description}}</td>
  </tr>
  {% endif %}
  {% endfor %}
</table>

Please refer to [Message routing to registered practice](integration_mesh.html#message-routing-to-registered-practice) for details of how to use this facility.

## Workflow groups and Workflow ID ##

<table class="requirement-box">
  {% for item in site.data.senddoc_requirements.requirements %}
  {% if item.area == 'mesh1' %}
  <tr>
    <td id="{{item.id}}">{{item.id}}</td>
    <td>{{item.description}}</td>
  </tr>
  {% endif %}
  {% endfor %}
</table>

### MESH client configuration 

When using the MESH client to send a message to the MESH server, the `.CTL` file will contain the following metadata about the message:

<table class="requirement-box">
  {% for item in site.data.senddoc_requirements.requirements %}
  {% if item.area == 'mesh2' %}
  <tr>
    <td id="{{item.id}}">{{item.id}}</td>
    <td>{{item.description}}</td>
  </tr>
  {% endif %}
  {% endfor %}
</table>


An example `.CTL` file is given below for a Consultation Report message regarding a consultation which took place for a fictional patient: Mr Richard Smith, NHS Number 1234567890, Date of birth 9th January 1955.

```xml
<DTSControl>
<Version>1.0</Version>
<AddressType>DTS</AddressType>
<MessageType>Data</MessageType>
<From_DTS>GP0001</From_DTS>
<To_DTS>GPPROVIDER_1234567890_09011955_Smith</To_DTS>
<Subject>GP consultation report for patient Mr Richard Smith , NHS Number 1234567890, with details of encounter which at practice GP0001</Subject>
<LocalId></LocalId>
<DTSId></DTSId>
<PartnerId></PartnerId>
<Compress>Y</Compress>
<Encrypted>N</Encrypted>
<WorkflowId>GPFED_CONSULT_REPORT</WorkflowId>
<ProcessId></ProcessId>
<DataChecksum></DataChecksum>
<IsCompressed>Y</IsCompressed>
</DTSControl>
```

### MESH API configuration ###

When using the [MESH API](https://meshapi.docs.apiary.io/) the [Send Message API call](https://meshapi.docs.apiary.io/#reference/0/mesh-messages/send-a-message) will be used by a practice API client to send a message to the MESH server. MESH metadata items are defined in HTTP header fields as described below:

<table class="requirement-box">
  {% for item in site.data.senddoc_requirements.requirements %}
  {% if item.area == 'mesh3' %}
  <tr>
    <td id="{{item.id}}">{{item.id}}</td>
    <td>{{item.description}}</td>
  </tr>
  {% endif %}
  {% endfor %}
</table>

---
title: MESH message configuration
keywords: document, mesh
tags: [messaging, mesh, send-document]
sidebar: senddocument_sidebar
permalink: senddocument_generic_mesh.html
summary: "Generic payload - MESH configuration"
---

Please refer to [Integration to MESH](integration_mesh.html) for an introduction to the use of MESH for GP Connect Messaging use cases.

{% include important.html content="The preferred method for sending the Generic payload is the <strong>MESH API</strong>, this is because the MESH API is more easily integrated into sending systems.<br/><br/>The <strong>MESH client</strong> can be used to send the message, but the <strong>MESH API Address Lookup</strong> is still required if sending to a an alternative care provider.<br/><br/>The [Message routing to registered practice](integration_mesh.html#message-routing-to-registered-practice) can be used if only ever sending to the patient's registered GP practice. " %}


## MESH API Address Lookup ##

<table class="requirement-box">
  {% for item in site.data.ge_requirements.requirements %}
  {% if item.area == 'mesh' %}
  <tr>
    <td id="{{item.id}}">{{item.id}}</td>
    <td>{{item.description}}</td>
  </tr>
  {% endif %}
  {% endfor %}
</table>

## Workflow groups and Workflow ID ##

<table class="requirement-box">
  {% for item in site.data.ge_requirements.requirements %}
  {% if item.area == 'mesh1' %}
  <tr>
    <td id="{{item.id}}">{{item.id}}</td>
    <td>{{item.description}}</td>
  </tr>
  {% endif %}
  {% endfor %}
</table>

## MESH API configuration ##

When using the [MESH API](https://digital.nhs.uk/developer/api-catalogue/message-exchange-for-social-care-and-health-api) the [Send Message API call](https://digital.nhs.uk/developer/api-catalogue/message-exchange-for-social-care-and-health-api#api-Endpoints-sendMessage-0) will be used by a sending organisation API client to send a message to the MESH server. MESH metadata items are defined in HTTP header fields as described below:

<table class="requirement-box">
  {% for item in site.data.ge_requirements.requirements %}
  {% if item.area == 'mesh3' %}
  <tr>
    <td id="{{item.id}}">{{item.id}}</td>
    <td>{{item.description}}</td>
  </tr>
  {% endif %}
  {% endfor %}
</table>

## MESH client configuration  ##

When using the MESH client to send a message to the MESH server, the `.CTL` file will contain the following metadata about the message:

<table class="requirement-box">
  {% for item in site.data.oc_requirements.requirements %}
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
<Subject>Online consultation report for patient Mr Richard Smith , NHS Number 1234567890, GP0001</Subject>
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



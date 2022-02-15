---
title: Error handling
keywords: use-case, itk3, mesh
tags: [use-case, itk3, mesh, send-document]
sidebar: sendupdate_sidebar
permalink: sendupdate_errors.html
summary: "Error handling details for Send Update"
---

The following section describes error scenarios and associated error codes for this messaging use case.

## ITK3 errors ##

<table class="requirement-box">
  {% for item in site.data.sendupdate_requirements.requirements %}
  {% if item.area == 'error' %}
  <tr>
    <td id="{{item.id}}">{{item.id}}</td>
    <td>{{item.description}}</td>
  </tr>
  {% endif %}
  {% endfor %}
</table>

## Diagnostic information ##

<table class="requirement-box">
  {% for item in site.data.sendupdate_requirements.requirements %}
  {% if item.area == 'error3' %}
  <tr>
    <td id="{{item.id}}">{{item.id}}</td>
    <td>{{item.description}}</td>
  </tr>
  {% endif %}
  {% endfor %}
</table>

## Errors from MESH Endpoint Lookup ##

The following table describes error codes returned from the MESH server as a result of issues encountered using the facility to [route a message automatically to the registered practice](integration_mesh.html#message-routing-to-registered-practice). 

<table class="requirement-box">
  {% for item in site.data.sendupdate_requirements.requirements %}
  {% if item.area == 'error4' %}
  <tr>
    <td id="{{item.id}}">{{item.id}}</td>
    <td>{{item.description}}</td>
  </tr>
  {% endif %}
  {% endfor %}
</table>

| Status Code | MESH Error Code | Description |
| ----------- | --------------- | ----------- |
| EPL-150 | ERROR_TOO_MANY_MAILBOX_MATCHES | Multiple mailboxes matches |
| EPL-151 | ERROR_NO_MAILBOX_MATCHES | No mailbox matched |
| EPL-152 | ERROR_INVALID_NHSNUMBER | Invalid NHS Number |
| EPL-153 | ERROR_NHSNUMBER_NOT_FOUND | NHS Number not found |
| EPL-154 | ERROR_NO_DEMOGRAPHICS_MATCH | NHS Number supplied does not match the demographics |


MESH will generate these errors in the form of error reports which will be placed in the sender's mailbox to await collection and processing by the sending organisation. 

### MESH API errors ###

Please note that, when using the MESH API to send a message, errors encountered when using the automated registered practice routing will not be returned in the API response header or payload, but via a MESH error report .CTL file placed in the sending organisation MESH mailbox.

For example, where an invalid NHS Number has been supplied in the `Mex_To` HTTP header, an error report .CTL file will be returned with a `<StatusRecord>` section which provides error details as follows:

```xml
<StatusRecord>
    <DateTime>20170926135509</DateTime>
    <Event>SEND</Event>
    <Status>ERROR</Status>
    <StatusCode>EPL-152</StatusCode>
    <Description>Invalid NHS Number</Description>
  </StatusRecord>
``` 

<table class="requirement-box">
  {% for item in site.data.sendupdate_requirements.requirements %}
  {% if item.area == 'error5' %}
  <tr>
    <td id="{{item.id}}">{{item.id}}</td>
    <td>{{item.description}}</td>
  </tr>
  {% endif %}
  {% endfor %}
</table>

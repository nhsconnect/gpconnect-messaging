---
title: Send Federated Consultation Report - Error handling
keywords: use_case, itk3, mesh
tags: [use_case, itk3, mesh, send_document]
sidebar: senddocument_sidebar
permalink: senddocument_fedcon_errors.html
summary: "Error handling details for the Send Federated Consultation Report use case"
---

The following section describes error scenarios and associated error codes for this messaging use case.

## ITK3 errors ##

<table class="requirement-box">
  <tr>
    <td>GPCM-SD-65</td>
    <td>Where the received message does not conform to the requirements stated for <a href="senddocument_fedcon_itk3.html">ITK3 header</a>, or for the payload, the message <b>MUST</b> be considered invalid</td>
  </tr>
  <tr>
    <td>GPCM-SD-66</td>
    <td>Where a received message is invalid, an ITK3 Response <b>MUST</b> be generated, with the corresponding Negative ITK3 Response Code which indicates the nature of the error, and the message <b>MUST NOT</b> be accepted for downstream processing</td>
  </tr>
</table>

Details are given below of the ITK3 Negative Response which is used per error scenario:

### ITK3 Header errors ### 

<table class="requirement-box">
  <tr>
    <td>GPCM-SD-67</td>
    <td>Mandated element not present (BusAck, InfAck, RecipientType, Priority, SenderReference, MessageDefinition, Timestamp, Event) - reponse code 10008 <b>MUST</b> be used</td>
  </tr>
  <tr>
    <td>GPCM-SD-68</td>
    <td>InfAck element not set to <code>true</code> - response code 10002 <b>MUST</b> be used</td>
  </tr>
  <tr>
    <td>GPCM-SD-69</td>
    <td>BusAck element not set to <code>true</code> - response code 10003 <b>MUST</b> be used</td>
  </tr>
  <tr>
    <td>GPCM-SD-70</td>
    <td>RecipientType element not set to <code>FA</code> - response code 10010 <b>MUST</b> be used</td>
  </tr>
  <tr>
    <td>GPCM-SD-71</td>
    <td>Priority element not set to <code>routine</code> - response code 10006 <b>MUST</b> be used</td>
  </tr>
  <tr>
    <td>GPCM-SD-72</td>
    <td>Event element not set to <code>ITK007C</code> - response code 10008 <b>MUST</b> be used</td>
  </tr>
</table>


### ITK3 Payload business rules errors ###

<table class="requirement-box">
  <tr>
    <td>GPCM-SD-73</td>
    <td>Payload content business rule violated - response code 10008 <b>MUST</b> be used</td>
  </tr>
</table>

## Diagnostic information ##

<table class="requirement-box">
  <tr>
    <td>GPCM-SD-74</td>
    <td>Error context and description <b>MUST</b> be provided in the <code>OperationOutcome.diagnostic</code> element to enable the sender to correctly identify the error which has been found in their sent message.</td>
  </tr>
</table>

## Errors from MESH Endpoint Lookup ##

The following table describes error codes returned from the MESH server as a result of issues encountered using the facility to [route a message automatically to the registered practice](integration_mesh.html#message-routing-to-registered-practice). 

<table class="requirement-box">
  <tr>
    <td>GPCM-SD-75</td>
    <td>The following errors, when encountered, <b>MUST</b> be handled gracefully by the message sending system</td>
  </tr>
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

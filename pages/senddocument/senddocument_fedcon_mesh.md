---
title: MESH message configuration
keywords: document, mesh
tags: [messaging, mesh, send_document]
sidebar: senddocument_sidebar
permalink: senddocument_fedcon_mesh.html
summary: "Federated consultation - MESH configuration"
---

Please refer to [Integration to MESH](integration_mesh.html) for an introduction to the use of MESH for GP Connect Messaging use cases.

## MESH message routing ##

<table class="requirement-box">
  <tr>
    <td>GPCM-SD-56</td>
    <td>All messages sent through this use case <b>MUST</b> use MESH automated message routing in order to ensure that the message is routed correctly to the registered practice of the patient.</td>
  </tr>
</table>

Please refer to [Message routing to registered practice](integration_mesh.html#message-routing-to-registered-practice) for details of how to use this facility.

## Workflow groups and Workflow ID ##

<table class="requirement-box">
  <tr>
    <td>GPCM-SD-57</td>
    <td>Each instance of a Send Federated Consultation Report message <b>MUST</b> include the following MESH Workflow ID in the MESH message metadata: <code>TBC:WorkflowID</code></td>
  </tr>
  <tr>
    <td>GPCM-SD-58</td>
    <td>Each instance of an acknowledgement message generated as a result of receipt of a Send Federated Consultation Report message <b>MUST</b> include the following Workflow ID in the MESH message metadata: <code>TBC:WorkflowID_ACK</code></td>
  </tr>
</table>

### MESH client configuration 

When using the MESH client to send a message to the MESH server, the `.CTL` file will contain the following metadata about the message:

<table class="requirement-box">
  <tr>
    <td>GPCM-SD-59</td>
    <td><code>From_DTS</code> <b>MUST</b> contain the MESH mailbox ID of the sender of the message – in this case the federated GP practice.</td>
  </tr>
  <tr>
    <td>GPCM-SD-60</td>
    <td><code>To_DTS</code> <b>MUST</b> contain the NHS Number, DOB and Surname of the patient delimited by the underscore character ‘_’. This enables automatic routing of the message to the registered GP MESH mailbox.</td>
  </tr>
  <tr>
    <td>GPCM-SD-61</td>
    <td><code>Subject</code> <b>MUST</b> contain To contain text in the following format:<br/><br/><code>Federated consultation report for {Patient Name} , NHS Number {NHS Number}, seen at {Practice Name}, ODS Code {ODS Code}</code></td>
  </tr>
</table>


An example `.CTL` file is given below for a Federated Consultation Summary message regarding a consultation which took place for a fictional patient: Mr Richard Smith, NHS Number 1234567890, Date of birth 9th January 1955.

```xml
<DTSControl>
<Version>1.0</Version>
<AddressType>DTS</AddressType>
<MessageType>Data</MessageType>
<From_DTS>GP0001</From_DTS>
<To_DTS>GPPROVIDER_1234567890_09011955_Smith</To_DTS>
<Subject>Federated GP consultation summary for patient Mr Richard Smith , NHS Number 1234567890, with details of encounter which at practice GP0001</Subject>
<LocalId></LocalId>
<DTSId></DTSId>
<PartnerId></PartnerId>
<Compress>Y</Compress>
<Encrypted>N</Encrypted>
<WorkflowId>TBC-GPCONNECT_FEDERATED_CONSULTATION</WorkflowId>
<ProcessId></ProcessId>
<DataChecksum></DataChecksum>
<IsCompressed>Y</IsCompressed>
</DTSControl>
```

### MESH API configuration ###

Whe using the [MESH API](https://meshapi.docs.apiary.io/) the [Send Message API call](https://meshapi.docs.apiary.io/#reference/0/mesh-messages/send-a-message) will be used by a practice API client to send a message to the MESH server. MESH metadata items are defined in HTTP header fields as described below:

<table class="requirement-box">
  <tr>
    <td>GPCM-SD-62</td>
    <td><code>Mex-From</code>  <b>MUST</b> contain  the MESH mailbox ID of the sender of the message – in this case the federated GP practice.</td>
  </tr>
  <tr>
    <td>GPCM-SD-63</td>
    <td><code>Mex-To</code> <b>MUST</b> contain the NHS Number, DOB and Surname of the patient delimited by the underscore character ‘_’. This enables automatic routing of the message to the registered GP MESH mailbox.</td>
  </tr>
  <tr>
    <td>GPCM-SD-64</td>
    <td><code>Mex-Subject</code> <b>MUST</b> contain To contain text in the following format:<br/><br/><code>Federated consultation report for {Patient Name} , NHS Number {NHS Number}, seen at {Practice Name}, ODS Code {ODS Code}</code></td>
  </tr>
</table>

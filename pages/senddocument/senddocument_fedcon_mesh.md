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

All messages sent through this use case **SHALL** use MESH automated message routing in order to ensure that the message is routed correctly to the registered practice of the patient.

Please refer to [Integration to MESH](integration_mesh.html) for details of how to use this facility.

## Workflow groups and Workflow ID ##

Each instance of a Send Federated Consultation message MUST include the following MESH Workflow ID in the MESH message metadata: `TBC:WorkflowID`

Each instance of an acknowledgement message generated as a result of receipt of a Send Federated Consultation message **MUST** include the following Workflow ID in the MESH message metadata: `TBC:WorkflowID_ACK`

### MESH client configuration 

When using the MESH client to send a message to the MESH server, the `.CTL` file **MUST** contain metadata about the message.

| Metadata item | Description |
| ------------- | ----------- |
| `From_DTS` | Identifies the MESH mailbox ID of the sender of the message – in this case the federated GP practice.  |
| `To_DTS` |  The `To_DTS` field will contain NHS Number, DOB and Surname of the patient delimited by the underscore character ‘_’. This enables automatic routing of the message to the registered GP MESH mailbox. |
| `Subject` | To contain the following text: <br/>  <br/>  *Federated GP consultation summary for patient {Patient Name} , NHS Number {NHS Number}, with details of encounter which at practice {ODS Code}* |

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

The [MESH API Send Message](https://meshapi.docs.apiary.io/#reference/0/mesh-messages/send-a-message) API call will be used by a practice API client to send a message to the MESH server. MESH metadata items are defined in HTTP header fields.

| HTTP Header field | Description |
| ------------- | ----------- |
| `Mex-From` | Identifies the MESH mailbox ID of the sender of the message – in this case the federated GP practice.  |
| `Mex-To` |  The `Mex_To` field will contain NHS Number, DOB and Surname of the patient delimited by the underscore character ‘_’. This enables automatic routing of the message to the registered GP MESH mailbox. |
| `Mex-Subject` | To contain the following text: <br/>  <br/>  *Federated GP consultation summary for patient {Patient Name} , NHS Number {NHS Number}, with details of encounter which at practice {ODS Code}* |

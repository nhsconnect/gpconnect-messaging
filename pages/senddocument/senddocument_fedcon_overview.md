---
title: Overview
keywords: document, use-case
tags: [mesh, itk3, use-case, send-document]
sidebar: senddocument_sidebar
permalink: senddocument_fedcon_overview.html
summary: "Overview of the use case to send a consultation report to the registered practice of a patient"
---

## Introduction ##

When a patient is seen by another GP practice it is necessary for information from that consultation to be sent back to the patient’s registered GP practice. This is so the information can be recorded in the patient’s clinical record and is available during future consultations.


##  Appointments use case ##

This use case completes the set of capabilities required to fulfil the following workflow:

1.	the GP Connect Appointments FHIR&reg; API enables booking of a consultation at an alternative practice
2.	the GP Connect Access Record HTML FHIR&reg; API enables an amenable consultation to take place at the alternative practice through access to the patient record stored at the patient’s registered practice
3.	after the consultation, the [Send Document](senddocument.html) GP Connect Messaging enables the details of this consultation to be written back to the registered practice so that the registered practice patient record continues to provide an up-to-date view of care which the patient receives in a GP practice setting

{% include callout.html content="It is worth emphasising that the first two steps above use synchronous GP Connect FHIR&reg; API capabilities, and that an asynchronous messaging approach is taken to facilitate the update made at the registered practice by the final step." type="info" %}


## Message flows in Send Consultation use case ##

The following diagram illustrates how messages flow between the practice and the registered practice via MESH to fulfil this use case:

![Consultation Sequence Diagram](images/senddocument/sequence.png "Message flow illustration") 

The diagram above depicts a successful message flow where registered practice message processing validates and matches the initial message successfully to a patient. This involves the following steps:

| Event / Step | Description |
|------|-------------|
| 1    | **Consultation report message** |
| 1a   | After the consultation is complete, a trigger at the originating practice results in a FHIR Message being constructed which includes a PDF describing the consultation.  |
| 1b   | The MESH client at the originating practice sends the message to the MESH server where it awaits collection by the registered practice. |
| 1c   | The MESH client at the registered practice collects the message from the MESH server and makes it available to other registered practice system components for onward processing. |
| 1d   | The message is processed at the registered practice. |
|      |      |
| 2    | **Infrastructure acknowledgement ITK Response** |
| 2a   | When the consultation report message is passed from the MESH client for processing at the registered practice, the message is first validated to ensure that its structure is correct. An ITK3 Response message is generated which indicates the success of message processing at a technical level - this is known as an "infrastructure acknowledgement".  |
| 2b   | The MESH client at the registered practice sends the message to the MESH server where it awaits collection by the originating practice. |
| 2c   | The MESH client at the originating practice collects the message from the MESH server. The ITK Response is then available to other originating practice system components for onward processing. |
| 2d   | The acknowledgement message is processed as appropriate by the originating practice.  |
|      |      |
| 3    | **Business acknowledgement ITK Response** |
| 3a   | When the consultation report message is passed from the MESH client for processing at the registered practice, after successful message validation, the subject of the message contents - the patient - is looked up to ensure that patient is known and registered at the practice. An ITK3 Response message is generated which indicates the success of patient matching - this is known as a "business acknowledgement".  |
| 3b   | The MESH client at the registered practice sends the message to the MESH server where it awaits collection by the originating practice. |
| 3c   | The MESH client at the originating practice collects the message from the MESH server and makes it available to other originating practice system components for onward processing. |
| 3d   | The acknowledgement message is processed as appropriate by the originating practice.  |

 
## Message creation at originating practice ##

The following processing steps must take place at the originating practice system to create the message - as described in step 1a above.

| Step | Description |
|------|-------------|
| 1   | Initiate process to create for consultation report message. Refer to [Send Trigger](senddocument_fedcon_trigger.html) for guidance on available options. |	
| 2   | Create [ITK3 payload](senddocument_fedcon_payload.html): Construct a PDF description of the encounter. |
| 3   | Wrap the payload as an [ITK3 message](senddocument_fedcon_itk3.html), requesting infrastructure and business acknowledgements. |
| 4   | Create [MESH message](senddocument_fedcon_mesh.html). Specify NHS Number, DOB and Surname in MESH metadata to enable MESH to route to registered practice. |

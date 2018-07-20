---
title: Send Federated Consultation Summary - Overview
keywords: document, usecase
tags: [mesh, itk3, use-case]
sidebar: senddocument_sidebar
permalink: senddocument_fedcon_overview.html
summary: "Overview of the use case to send a federated consultation summary to the registered practice of a patient"
---

One of the main areas of focus for the [GP Connect product as a whole](index.html) is to support GP practice federated work patterns. 
 
This use case completes the set of capabilities required to fulfil the following workflow:

1.	The [GP Connect Appointments FHIR API](https://nhsconnect.github.io/gpconnect/appointments.html) enables booking of a consultation at a federated practice.
2.	The [GP Connect Access Record HTML FHIR API](https://developer.nhs.uk/apis/gpconnect-0-5-0/accessrecord.html) enables an amenable consultation to take place at the federated practice through access to the patient record stored at the patient’s registered practice.
3.	After the consultation, the [Send Document](senddocument.html) GP Connect Messaging enables the details of this consultation to be written back to the registered practice so that the registered practice patient record continues to provide an up-to-date view of care which the patient receives in a GP practice setting.

It is worth emphasising that the first two steps above use synchronous [GP Connect FHIR API](https://nhsconnect.github.io/gpconnect/) capabilities, and that an asynchronous messaging approach is taken to facilitate the update made at the registered practice by the final step.

## Message flows in Send Federated Consultation use case ##

The following diagram illustrates how messages flow between the federated practice and the registered practice via MESH to fulfil this use case:

![Federated Consultation Sequence Diagram](images/senddocument/federated_consultation_sequence.PNG) 

The diagram above depicts a successful message flow where registered practice message processing validates and matches the initial message successfully to a patient. This involves the following steps:

| Event / Step | Description |
|------|-------------|
| 1    | **Federated consultation summary message** |
| 1a   | After the federated consultation is complete, a trigger at the federated practice results in a FHIR Message being constructed which includes a PDF describing the consultation.  |
| 1b   | The MESH client at the federated practice sends the message to the MESH server where it awaits collection by the registered practice. |
| 1c   | The MESH client at the registered practice collects the message from the MESH server and makes it available to other registered practice system components for onward processing. |
| 1d   | The message is processed at the registered practice. Frequently this will result in a task being created in the practice workflow. |
|      |      |
| 2    | **Infrastructure acknowledgement ITK response** |
| 2a   | When the federated consultation summary message is passed from the MESH client for processing at the registered practice, the message is first validated to ensure that its structure is correct. An ITK3 Response message is generated which indicates the success of message processing at a technical level - this is known as an "infrastructure acknowledgement".  |
| 2b   | The MESH client at the registered practice sends the message to the MESH server where it awaits collection by the federated practice. |
| 2c   | The MESH client at the federated practice collects the message from the MESH server and makes it available to other federated practice system components for onward processing. |
| 2d   | The acknowledgement message is processed as appropriate by the federated practice.  |
|      |      |
| 3    | **Business acknowledgement ITK response** |
| 3a   | When the federated consultation summary message is passed from the MESH client for processing at the registered practice, after successful message validation, the subject of the message contents - the patient - is looked up to ensure that patient is known and registered at the practice. An ITK3 Response message is generated which indicates the success of patient matching - this is known as a "business acknowledgement".  |
| 3b   | The MESH client at the registered practice sends the message to the MESH server where it awaits collection by the federated practice. |
| 3c   | The MESH client at the federated practice collects the message from the MESH server and makes it available to other federated practice system components for onward processing. |
| 3d   | The acknowledgement message is processed as appropriate by the federated practice.  |

 
## Message creation at federated practice ##

The following processing steps must take place at the federated practice system to create the message - as described in step 1a above.

| Step | Description |
|------|-------------|
| 1   | Initiate process to create for federated consultation summary message. Refer to [Send Trigger](senddocument_fedcon_trigger.html) for guidance on available options. |	
| 2   | Create [ITK3 payload](senddocument_fedcon_payload.html): Construct a PDF description of the encounter, embed in Task resource, and include resources referenced from the task. |
| 3   | Wrap the payload as an [ITK3 message](senddocument_fedcon_itk3.html), requesting infrastructure and business acknowledgements. |
| 4   | Create [MESH message](senddocument_fedcon_mesh.html). Specify NHS Number, DOB and Surname in MESH metadata to enable MESH to route to registered practice. |

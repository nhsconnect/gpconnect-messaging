---
title: Spine integration illustrated
keywords: spine, mesh, itk3
tags: [integration]
sidebar: overview_sidebar
permalink: integration_illustrated.html
summary: "Illustration of the use of MESH and ITK3 to send a document"
---

All messages sent in order to update GP systems through GP Connect Messaging capabilities have the following NHS Spine integration requirements:



- use of [MESH](integration_mesh.html) to send messages


- use of [ITK3](integration_itk3.html) to provide a standard FHIR Message format

Additionally, as most of these messages will be intended to update the care record at the patient's registered practice, most messaging use cases will make use of an additional MESH capability:



- MESH Endpoint Lookup Service

An example is given below of the [Send Consultation Report](senddocument_fedcon_overview.html) messaging use case which makes use of all three of these NHS SPINE integration options.

## Example: Integrate with Spine to send a consultation report as a document ##

The following diagram illustrates the systems involved, and their responsibilities, in sending the consultation report document:

![Integration illustrated - send](images/integration/spine_integration_send.PNG "System integration illustration") 

The steps shown in the diagram are detailed below:

| Step | Description |
|------|-------------|
| 1   | The **sender system** constructs a [FHIR Message](https://www.hl7.org/fhir/messaging.html) according to the [ITK3](https://nhsconnect.github.io/ITK3-FHIR-Messaging-Distribution/) standard which contains the details of the consultation which has taken place. The message is placed in the `/OUT` directory.  |
|      |      |
| 2   | The **[MESH](https://digital.nhs.uk/services/message-exchange-for-social-care-and-health-mesh) Client** installed at the sender practice picks up the message from the `/OUT` directory and sends the message securely to the central Spine MESH server. |
|      |      |
| 3   | The **Spine MESH server** extracts patient's Surname, Date of Birth and NHS Number from the `To_DTS` field in the MESH message `.CTL` file, and then performs a [PDS](https://digital.nhs.uk/services/demographics) lookup using these details in order to discover the [ODS code](https://digital.nhs.uk/services/organisation-data-service) of the patient's registered practice. |
|      |      |
| 4   | The **Spine MESH server** then uses the ODS code of the patient's registered practice to lookup the MESH mailbox of the registered practice, where the message is then placed to await collection. |
|      |      |
| 5   | The **MESH Client** at the registered practice collects the message from registered practice mailbox and writes the collected message to the `/IN` directory. |
|      |      |
| 6   | The **Registered practice GP system** picks up the message from the `/IN` directory and updates the GP system. This is likely to be done through raising a workflow task containing the message contents. |

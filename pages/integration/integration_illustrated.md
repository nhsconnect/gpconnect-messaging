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

Use cases not intending to update the care record at the patient's registered practice will make use of the MESH API.


## Example 1: Integrate with Spine to send a consultation report as a document ##

The following diagram illustrates the systems involved, and their responsibilities, in sending the consultation report document:

<br/>
<div style="max-width:100%;max-height:100%;display:block;margin: 0 auto;" >
	{% include images/senddocument/spine_integration_send1.svg %}
</div>
<br/>

The steps shown in the diagram are detailed below:

1.  The **sender system** constructs a [FHIR Message](https://www.hl7.org/fhir/messaging.html) according to the [ITK3](https://nhsconnect.github.io/ITK3-FHIR-Messaging-Distribution/) standard which contains the details of the consultation which has taken place. The message is placed in the `/OUT` directory.
2.  The **[MESH](https://digital.nhs.uk/services/message-exchange-for-social-care-and-health-mesh) Client** installed at the sender practice picks up the message from the `/OUT` directory and sends the message securely to the central Spine MESH server.
3. The **Spine MESH server** extracts patient's Surname, Date of Birth and NHS Number from the `To_DTS` field in the MESH message `.CTL` file, and then performs a [PDS](https://digital.nhs.uk/services/demographics) lookup using these details in order to discover the [ODS code](https://digital.nhs.uk/services/organisation-data-service) of the patient's registered practice.
4. The **Spine MESH server** calls the [MESH Endpoint Lookup Service](https://digital.nhs.uk/services/message-exchange-for-social-care-and-health-mesh/mesh-guidance-hub/endpoint-lookup-service-and-workflowids) and returns the practice mailbox details. 
5. The **Spine MESH server** places the message into this mailbox.
6. The **MESH Client** at the registered practice collects the message from registered practice mailbox and writes the collected message to the `/IN` directory.
7. The **Registered practice GP system** picks up the message from the `/IN` directory and updates the GP system. This is likely to be done through raising a workflow task containing the message contents.


## Example 2: Integrate with Spine to send an Online Consultation Report as a document to an alternative care provider (for example, cmmunity pharmacy)##

The following diagram illustrates the systems involved, and their responsibilities, in sending the Online Consultation Report document:

<br/>
<div style="max-width:100%;max-height:100%;display:block;margin: 0 auto;" >
	{% include images/senddocument/spine_integration_send3.svg %}
</div>
<br/>

The steps shown in the diagram are detailed below:

1.  The **sender system** uses the MESH API Address Lookup function to request the receiving organisation MESH mailbox ID (two lookups are initiated, one for the alternative care provider, one for the patient's register GP).
2.  The **Spine MESH service** returns two responses containing the MESH mailbox ID for the alternative care provider and the patient's registered GP practice.
3. The **sender system** constructs a [FHIR Message](https://www.hl7.org/fhir/messaging.html) according to the [ITK3](https://nhsconnect.github.io/ITK3-FHIR-Messaging-Distribution/) standard which contains the details of the consultation which has taken place. The message is sent to the alternative care provider using the MESH API Send Message function labelled "For Action".
4. The **sender system** constructs a [FHIR Message](https://www.hl7.org/fhir/messaging.html) according to the [ITK3](https://nhsconnect.github.io/ITK3-FHIR-Messaging-Distribution/) standard which contains the details of the consultation which has taken place. A copy of the message is sent to the patient's registered GP practice using the MESH API Send Message function labelled "For Information".
5. The **Spine MESH server** places the messages in the receiving organisations mailboxes to await collection.
6. The **receiving organisation** (community pharmacy) uses the MESH API download message function to download the messages from their MESH mailbox.
7. The **receiving organisation** (patient's registered GP practice) uses the MESH API download message function to download the messages from their MESH mailbox.

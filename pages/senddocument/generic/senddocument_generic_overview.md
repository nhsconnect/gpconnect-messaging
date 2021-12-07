---
title: Overview
keywords: document, use-case
tags: [mesh, itk3, use-case, send-document]
sidebar: senddocument_sidebar
permalink: senddocument_generic_overview.html
summary: "Overview of the generic payload"
---

## Introduction ##

The Generic payload has been designed to fill the current gap that is blocking a large number of organisations being able to sent documents back to a patient's registered GP practice.

If an organisation is already sending documents being received by the patient's registered GP practice then they automatically qualify for using the Generic payload.

Organisation's wanting to send something new back to the patient's registered GP practice will need to contact the GP Connect team to discuss their use-case in more detail to gain approval to proceed.


## Message flow ##

The following diagram illustrates how a message can flow between the sending (originating) system and the receiving care provider via MESH to fulfil this use case:

<div style="max-width:100%;max-height:100%;display:block;margin: 0 auto;" >
	{% include images/senddocument/sequence_oc_gp.svg %}
</div>
<br/>


The diagram above depicts a successful message flow where the receiving care provider (in this example a GP) validates the message successfully and consumes. This involves the following steps:

1.  **MESH Address Lookup**

    1. The sending system initiates a MESH Address Lookup request for the patient's registered GP practice.
    2. The sending system receives a response containing the MESH mailbox ID for the patient's registered GP practice.

2.  **Document being sent in payload**

    1. A trigger at the sending system results in a FHIR Message being constructed which includes a document (as a minimum).
    2. The MESH API Send Message function is used to send the message to the mailbox acquired in step 1.
    3. The MESH server places the message in the GP practice's MESH mailbox awaiting collection.
    4. The GP practice uses the MESH API Download Message function to retrieve the message from the MESH mailbox.
    5. The message is processed at the GP practice.

3.  **Infrastructure acknowledgement ITK Response**

    1. When the payload is passed from MESH for processing at the GP practice, the message is first validated to ensure that its structure is correct. An ITK3 Response message is generated which indicates the success of message processing at a technical level - this is known as an "infrastructure acknowledgement". 
    2. The GP practice uses the MESH API Send Message function to send the acknowledgement message to the MESH server where it awaits collection by the sending system.
    3. The sending system uses the MESH API Download Message function to collect the acknowledgement message. The ITK Response is then available to the sending system components for onward processing.
    4. The acknowledgement message is processed as appropriate by the sending system.

4.  **Business acknowledgement ITK Response**

    1. When the payload is passed from MESH for processing at the GP practice, after successful message validation, the subject of the message contents are landed in the workflow of the GP practice. An ITK3 Response message is generated which indicates the success of consuming the message - this is known as a "business acknowledgement". 
    2. The GP practice uses the MESH API Send Message function to send the acknowledgement message to the MESH server where it awaits collection by the sending system.
    3. The sending system uses the MESH API Download Message function to collect the acknowledgement message. The ITK Response is then available to the sending system components for onward processing.
    4. The acknowledgement message is processed as appropriate by the sending system.



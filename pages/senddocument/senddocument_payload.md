---
title: Send Document - payload structure
keywords: document, payload
tags: [send_document]
sidebar: senddocument_sidebar
permalink: senddocument_payload.html
summary: "Send Document capability - The structure of the payload to be used for all use cases of the Send Document capability."
---

## Payload message requirements ##

{% include callout.html content="The Send Document payload recognises that for most scenarios messages which are intended to update target organisations' records will result in a task being created in the target system workflow. As a result, the Task resource is used to describe the intent of the message - to request that a task be created in the target organisation to review and perform an update." type="info" %}

The following requirements describe the structure of the Send Document payload.

- The ITK3 `MessageHeader.focus` element **MUST** be a reference to a [Bundle](https://www.hl7.org/fhir/bundle.html) resource which conforms to the [ITK-Payload-Bundle](https://fhir.nhs.uk/STU3/StructureDefinition/ITK-Payload-Bundle-1) profile.

The `ITK-Payload-Bundle` **MUST** contain the following resource entries:

- An instance of the HL7 [Task](https://www.hl7.org/fhir/task.html) base resource.
- An Organization resource which conforms to the [CareConnect-Organization-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Organization-1) profile describing the organisation which sends the message. The `Task.requester.OnBehalfOf` element **MUST** contain a reference to this resource.
- Where the message contains patient information, for example as a result of a healthcare event, a patient resource **MUST** be present which conforms to the [CareConnect-Patient-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Patient-1) profile. When present, the `Task.for` element **MUST** contain a reference to this resource.
- Where the message contains practitioner information, for example as a result of a healthcare event, a practitioner resource **MUST** be present which conforms to the [CareConnect-Practitioner-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Practitioner-1) profile. This resource describes the primary practitioner who delivered care. When present, the `Task.requester.agent` element **MUST** contain a reference to this resource.
- Where the message sender knows the single intended recipient organisation for the message, an Organization resource **MUST** be present which conforms to the [CareConnect-Organization-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Organization-1) profile, describing the organisation which is the target of the message. The `Task.requester.owner` element **MUST** contain a reference to this resource.


### Including documents in the payload ###

Each binary document sent in the payload **MUST** be included as an instance of the `Task.input` element:

-  `task.input.value` **MUST** be a FHIR Reference containing a reference to a [DocumentReference](https://www.hl7.org/fhir/documentreference.html) resource.
- The DocumentReference resource **MUST** be included as an additional `entry` in the [ITK-Payload-Bundle](https://fhir.nhs.uk/STU3/StructureDefinition/ITK-Payload-Bundle-1) and contain the following elements:
	- `created` attribute containing the date/time when the binary document was created, or if not available, the date/time when the FHIR Message was created.
	- `description` attribute containing a description of the document, intended for use as an attachment label for the document as it appears in the GP Principal Clinical System workflow user interface.
	- `content` attribute containing a FHIR [Attachment](https://www.hl7.org/fhir/datatypes.html#attachment) resource in which the `contentType` defines the MIME type of the document, and `data` contains the binary data of the document in base64 encoded format. 
<br>

{% include note.html content="Please refer to the particular use case in question for detailed requirements on the population of these payload resources. Example FHIR Messages illustrating how payloads look on-the-wire are available for each use case." %} 

## Payload message illustration ##

The payload of a GP Connect message which uses the Send Document capability **MUST** have the structure illustrated in the diagram below:

![Send Document - Payload](images/senddocument/senddocument_payload.PNG) 

## Payload message definition ##

The FHIR MessageDefinition resource provides a formal, machine-readable definition of a message shared between systems. Please refer to [ITK3 Message Definitions](https://nhsconnect.github.io/ITK3-FHIR-Messaging-Distribution/explore_defs_overview.html) for an overview of how MessageDefinition resources are used in ITK3 messages.

The GP Connect Send Document capability has defined a MessageDefinition resource instance which describes the *payload* of the FHIR Message, as defined on at [ITK3 Message Definition Patterns](https://nhsconnect.github.io/ITK3-FHIR-Messaging-Distribution/explore_defs_overview.html#message-definition-patterns)

The Message Definition for the GP Connect Send Document message payload is provided below. This definition can be used by FHIR tools such as [FHIR Check](http://clarotech.co.uk/products/tool-fhir-check/) to verify that particular instance of a Send Document message is conformant. 

<script src="https://gist.github.com/briandiggle/b0a11ccc49ad81f2f7a9edec88d8c10f.js"></script>
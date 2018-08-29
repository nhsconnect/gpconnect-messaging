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

The following requirements describe the structure of the Send Document payload:

<table class="requirement-box">
  <tr>
    <td>GPCM-SD-1</td>
    <td>The ITK3 <code>MessageHeader.focus</code> element <b>MUST</b> be a reference to a <a href="https://www.hl7.org/fhir/bundle.html">Bundle</a> resource which conforms to the <a href="https://fhir.nhs.uk/STU3/StructureDefinition/ITK-Payload-Bundle-1/_history/1.1">ITK-Payload-Bundle</a> profile.</td>
  </tr>
  <tr>
    <td>GPCM-SD-2</td>
    <td>The <code>ITK-Payload-Bundle</code> <b>MUST</b> contain an HL7 <a href="https://www.hl7.org/fhir/task.html">Task</a> base resource.</td>
  </tr>
  <tr>
    <td>GPCM-SD-3</td>
    <td>The <code>ITK-Payload-Bundle</code> <b>MUST</b> contain an Organization resource which conforms to the <a href="https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Organization-1">CareConnect-Organization-1</a> profile describing the organisation which sends the message. The <code>Task.requester.OnBehalfOf</code> element <b>MUST</b> contain a reference to this resource.</td>
  </tr>
  <tr>
    <td>GPCM-SD-4</td>
    <td>The <code>Task.requester.OnBehalfOf</code> element <b>MUST</b> contain a reference to the Organization resource.</td>
  </tr>
  <tr>
    <td>GPCM-SD-5</td>
    <td>Where the message contains patient information, for example as a result of a healthcare event, a patient resource <b>MUST</b> be present which conforms to the <a href="https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Patient-1">CareConnect-Patient-1</a> profile. When this patient resource is present, the <code>Task.for</code> element <b>MUST</b> contain a reference to this resource.</td>
  </tr>
  <tr>
    <td>GPCM-SD-6</td>
    <td>Where the message contains practitioner information, for example as a result of a healthcare event, a practitioner resource <b>MUST</b> be present which conforms to the <a href="https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Practitioner-1">CareConnect-Practitioner-1</a> profile. This resource describes the primary practitioner who delivered care. When this practitioner resource is present, the <code>Task.requester.agent</code> element <b>MUST</b> contain a reference to this resource.</td>
  </tr>
  <tr>
    <td>GPCM-SD-7</td>
    <td>Where the message sender knows the single intended recipient organisation for the message, an Organization resource <b>MUST</b> be present which conforms to the <a href="https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Organization-1">CareConnect-Organization-1</a> profile, describing the organisation which is the target of the message. The <code>Task.requester.owner</code> element <b>MUST</b> contain a reference to this resource.</td>
  </tr>
</table>


### Including documents in the payload ###

The following requirements describe how binary documents are included in the payload:

<table class="requirement-box">
  <tr>
    <td>GPCM-SD-8</td>
    <td>Each binary document sent in the payload <b>MUST</b> be included as an instance of the <code>Task.input</code> element</td>
  </tr>
</table>

Each instance of an binary document will be included as follows:

<table class="requirement-box">
  <tr>
    <td>GPCM-SD-9</td>
    <td><code>task.input.value</code> <b>MUST</b> be a FHIR Reference containing a reference to a <a href="https://www.hl7.org/fhir/documentreference.html">DocumentReference</a> resource.</td>
  </tr>
  <tr>
    <td>GPCM-SD-10</td>
    <td>The DocumentReference resource <b>MUST</b> be included as an additional <code>entry</code> in the <a href="https://fhir.nhs.uk/STU3/StructureDefinition/ITK-Payload-Bundle-1/_history/1.1">ITK-Payload-Bundle</a> </td>
  </tr>
</table>

The DocumentReference resource will be specified as follows:

<table class="requirement-box">
  <tr>
    <td>GPCM-SD-11</td>
    <td><code>DocumentReference.created</code> attribute <b>MUST</b> contain the date/time when the binary document was created, or if not available, the date/time when the FHIR Message was created.</td>
  </tr>
  <tr>
    <td>GPCM-SD-12</td>
    <td><code>DocumentReference.description</code> attribute <b>MUST</b> contain a description of the document, intended for use as an attachment label for the document as it appears in the GP Principal Clinical System workflow user interface.</td>
  </tr>
  <tr>
    <td>GPCM-SD-13</td>
    <td><code>Document.content</code> attribute <b>MUST</b> contain a FHIR <a href="https://www.hl7.org/fhir/datatypes.html#attachment">Attachment</a> resource in which the <code>contentType</code> defines the MIME type of the document, and <code>data</code> contains the binary data of the document in base64 encoded format.</td>
  </tr>
</table>

<br>

{% include note.html content="Please refer to the particular use case in question for detailed requirements on the population of these payload resources. Example FHIR Messages illustrating how payloads look on-the-wire are available for each use case." %} 

### Identifying the use case ###

The ITK3 message handling key `LocalExtension` is used to define the health or social care use case associated with the Send Document message. Please refer to the ITK3 header requirements for your particular use case.   


## Payload message illustration ##

The payload of a GP Connect message which uses the Send Document capability **MUST** have the structure illustrated in the diagram below:

![Send Document - Payload](images/senddocument/senddocument_payload.PNG) 

## Payload message definition ##

The FHIR MessageDefinition resource provides a formal, machine-readable definition of a message shared between systems. Please refer to [ITK3 Message Definitions](https://developer.nhs.uk/apis/itk3messagedistribution-2-5-0/explore_defs_overview.html) for an overview of how MessageDefinition resources are used in ITK3 messages.

The GP Connect Send Document capability has defined a MessageDefinition resource instance which describes the *payload* of the FHIR Message, as defined on at [ITK3 Message Definition Patterns](https://developer.nhs.uk/apis/itk3messagedistribution-2-5-0/explore_defs_overview.html#message-definition-patterns)

The Message Definition for the GP Connect Send Document message payload is provided below. This definition can be used by FHIR tools such as [FHIR Check](http://clarotech.co.uk/products/tool-fhir-check/) to verify that particular instance of a Send Document message is conformant. 

<script src="https://gist.github.com/briandiggle/b0a11ccc49ad81f2f7a9edec88d8c10f.js"></script>
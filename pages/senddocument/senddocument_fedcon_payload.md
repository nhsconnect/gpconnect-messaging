---
title: Send Federated Consultation Report - Payload requirements
keywords: use_case
tags: [use_case, send_document]
sidebar: senddocument_sidebar
permalink: senddocument_fedcon_payload.html
summary: "Details of the FHIR resources which make up the payload for the Send Federated Consultation Report use case."
---

Please refer to [Send Document - Payload structure](senddocument_payload) for a definition of the payload structure to be used to fulfil the [Send Federated Consultation Report](http://localhost:4006/senddocument_fedcon_overview.html#federated-appointments-use-case) use case.

The following sections describe the resources which form the payload. i.e. the resources which will be present as entries of the [ITK-Payload-Bundle](https://fhir.nhs.uk/STU3/StructureDefinition/ITK-Payload-Bundle-1/_history/1.1) resource which acts as a container for the payload. 

A [message example](senddocument_payload) is provided which illustrates these requirements to aid understanding.

## Task resource ##

<table class="requirement-box">
  <tr>
    <td>GPCM-SD-14</td>
    <td>A Task resource profiled to <a href="https://fhir.nhs.uk/STU3/StructureDefinition/GPConnect-Task-1">GPConnect-Task-1</a> resource <b>MUST</b> be present in the payload</td>
  </tr>
</table>

The following requirements describe how the Task resource is populated:

<table class="requirement-box">
  <tr>
    <td>GPCM-SD-15</td>
    <td><code>intent</code> <b>MUST</b> contain fixed value <b><code>plan</code></b></td>
  </tr>
  <tr>
    <td>GPCM-SD-16</td>
    <td><code>status</code> <b>MUST</b> contain fixed value <b><code>requested</code></b></td>
  </tr>
  <tr>
    <td>GPCM-SD-17</td>
    <td><code>priority</code> <b>MUST</b> contain fixed value: <b><code>routine</code></b> <br/><br/>Where a specific action beyond attachment to the patient record at the registered practice is expected or required, existing business processes should be used as the Send Federated Consultation Report use case is simply the act of synchronising with the registered patient record. When the GP Connect <a href="sendtask.html">Send Task</a> capability has been implemented, this could be used to request specific tasks to raised at the registered practice beyond attachment to the registered practice record.</td>
  </tr>
  <tr>
    <td>GPCM-SD-18</td>
    <td><code>description</code> <b>MUST</b> contain a summary of request in the following format:<br/> <code>Federated consultation report for {Patient Name} , NHS Number {NHS Number}, seen at {Practice Name}, ODS Code {ODS Code}</code></td>
  </tr>
  <tr>
    <td>GPCM-SD-19</td>
    <td><code>for</code> <b>MUST</b> contain a reference to Patient resource profiled to <a href="https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Patient-1">CareConnect-Patient-1</a></td>
  </tr>
  <tr>
    <td>GPCM-SD-20</td>
    <td><code>authoredOn</code> <b>MUST</b> contain the date/time when the message was generated. (A separate process such as the MESH client may be responsible for sending the message at a later date/time.) </td>
  </tr>
  <tr>
    <td>GPCM-SD-21</td>
    <td><code>requester.agent</code> <b>MUST</b> contain a reference to a federated practice Practitioner resource profiled to <a href="https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Practitioner-">CareConnect-Practitioner-1</a></td>
  </tr>
  <tr>
    <td>GPCM-SD-22</td>
    <td> <code>requester.onBehalfOf</code> <b>MUST</b> contain a reference to a federated practice Organization resource profiled to <a href="https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Organization-1">CareConnect-Organization-1</a></td>
  </tr>
  <tr>
    <td>GPCM-SD-23</td>
    <td> <code>owner</code> <b>MUST</b> contain a reference to a registered practice Organization resource profiled to <a href="[https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Organization-1">CareConnect-Organization-1</a></td>
  </tr>
</table>

### Including binary documents in the payload ###

[Send Document - Including documents in the payload](http://localhost:4006/senddocument_fedcon_payload.html#including-binary-documents-in-the-payload) defines how binary documents are included in the Send Document payload.

For this use case, the following specific requirements apply:

**Federated Consultation Report** <br/>

<table class="requirement-box">
  <tr>
    <td>GPCM-SD-24</td>
    <td>The input element <b>MUST</b> contain a binary document which provides a report of the federated consultation in PDF format. </td>
  </tr>
  <tr>
    <td>GPCM-SD-25</td>
    <td><code>input.type.text</code> <b>MUST</b> be a fixed value of <code>Federated consultation report</code></td>
  </tr>
  <tr>
    <td>GPCM-SD-26</td>
    <td>The referenced <a href="https://fhir-test.nhs.uk/STU3/StructureDefinition/GPConnect-DocumentReference-1">GPConnect-DocumentReference-1</a> resource <b>MUST</b> contain a <code>description</code> element set to a fixed value of <code>Federated Consultation Report</code> </td>
  </tr>
  <tr>
    <td>GPCM-SD-78</td>
    <td>The referenced <a href="https://fhir-test.nhs.uk/STU3/StructureDefinition/GPConnect-DocumentReference-1">GPConnect-DocumentReference-1</a> resource <b>MUST</b> contain a <code>status</code> element set to a fixed value of <code>current</code> </td>
  </tr>
  <tr>
    <td>GPCM-SD-80</td>
    <td>The referenced <a href="https://fhir-test.nhs.uk/STU3/StructureDefinition/GPConnect-DocumentReference-1">GPConnect-DocumentReference-1</a> resource <b>MUST</b> contain a <code>subject</code> element containing a reference to a Patient resource profiled to <a href="https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Patient-1">CareConnect-Patient-1</a>.<br/>
    This is the same resource refered to by <code>task.for</code></td>
  </tr>
  <tr>
    <td>GPCM-SD-81</td>
    <td>The referenced <a href="https://fhir-test.nhs.uk/STU3/StructureDefinition/GPConnect-DocumentReference-1">GPConnect-DocumentReference-1</a> resource <b>MUST</b> contain an <code>author</code> element containing a reference to a <a href="https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Practitioner-">CareConnect-Practitioner-1</a> resource. <br/>
      This is the same resource refered to by <code>task.requester.agent</code></td>
  </tr>
</table>
	
<br/>
**Additional input elements**

Message senders **MAY** include additional binary documents in the payload as each expressed as an additional instance of the task.input as described in [Send Document - payload structure](senddocument_payload.html#including-documents-in-the-payload)

<table class="requirement-box">
  <tr>
    <td>GPCM-SD-27</td>
    <td>Where binary documents are included in the payload in addition to the Federated Consulation Report, the <i>Message receiver</i> <b>MUST</b> process these according ensuring all attachments remain in the context of the encounter information delivered to downstream systems.</td>
  </tr>
</table>

## Organization resources ##

<table class="requirement-box">
  <tr>
    <td>GPCM-SD-28</td>
    <td>As described in <a href="senddocument_payload.html">Send Document - Payload structure</a>, the payload <b>MUST</b> contain an organization resource describing both the sending organisation (the federated practice) and the receiving organisation (the patient's registered practice)</td>
  </tr>
</table>

The table below outlines how these resources are populated:

<table class="requirement-box">
  <tr>
    <td>GPCM-SD-29</td>
    <td>The <code>odsOrganisationCode</code> slice of the <code>identifier</code> element <b>MUST</b> contain the ODS code</td>
  </tr>
  <tr>
    <td>GPCM-SD-30</td>
    <td>The <code>name</code> element <b>MUST</b> contain the name of the organisation</td>
  </tr>
  <tr>
    <td>GPCM-SD-31</td>
    <td>The <code>telecom</code> element <b>MUST</b> contain the telephone number of that organization. i.e. where <code>telecom.system</code> is set to a fixed value of <code>phone</code>, and <code>telecom.value</code> contains the telephone number</td>
  </tr>
</table>

## Practitioner resource ##

The [CareConnect-Practitioner-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Practitioner-1) resource present in the payload is populated as follows:

<table class="requirement-box">
  <tr>
    <td>GPCM-SD-32</td>
    <td>The SDS User ID of the practitioner <b>MUST</b> be present in the <code>sdsUserID</code> slice of the <code>identifier</code> element</td>
  </tr>
  <tr>
    <td>GPCM-SD-33</td>
    <td>The name of the practitioner <b>MUST</b> be present in the single instance of the <code>name</code> element where <code>name.use</code> is set to <code>official</code></td>
  </tr>
  <tr>
    <td>GPCM-SD-34</td>
    <td>Telephone contact details <b>MUST</b> be present if available in the <code>Telecom</code> element. i.e. <code>telecom.system</code> is set to a fixed value of <code>phone</code>, and <code>telecom.value</code> contains the telephone number</td>
  </tr>
</table>

## Patient resource ##

The [CareConnect-Patient-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Patient-1) in the payload is populated as follows:

<table class="requirement-box">
  <tr>
    <td>GPCM-SD-35</td>
    <td>The NHS Number of the patient <b>MUST</b> be specified in the <code>nhsNumber</code> slice of the <code>identifier</code> element</td>
  </tr>
  <tr>
    <td>GPCM-SD-36</td>
    <td>The name of the patient <b>MUST</b> be present in the single instance of the <code>name</code> element where <code>name.use</code> is set to <code>official</code></td>
  </tr>
  <tr>
    <td>GPCM-SD-37</td>
    <td>The date of birth of the patient <b>MUST</b> be specified in <code>YYYY-MM-DD</code> format in the <code>birthDate</code> element. Birth time is not required.</td>
  </tr>
  <tr>
    <td>GPCM-SD-38</td>
    <td>Values specified in the patient resource for surname, date of birth and NHS Number <b>MUST</b> match those specified in MESH metadata <code>To_DTS</code> field (for the MESH client) or <code>Mex_To</code> (for the MESH API) as described in <a href="senddocument_fedcon_mesh.html">MESH message configuration</a></td>
  </tr>
</table>

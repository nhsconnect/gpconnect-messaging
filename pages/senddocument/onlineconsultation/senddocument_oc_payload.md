---
title: Payload requirements
keywords: use-case
tags: [use-case, send-document]
sidebar: senddocument_sidebar
permalink: senddocument_oc_payload.html
summary: "Details of the FHIR&reg; resources which make up the payload for the Online Consultation Report use case."
---

Please refer to [Send Document - Payload structure](senddocument_payload) for a definition of the payload structure to be used to fulfil the Online Consultation use case.

The following sections describe the resources which form the payload. These are the resources that will be present as entries of the [ITK-Payload-Bundle](https://fhir.nhs.uk/STU3/StructureDefinition/ITK-Payload-Bundle-1) resource, which acts as a container for the payload. 

A [message example](senddocument_oc_example) is provided which illustrates these requirements to aid understanding.

## Resource population requirements ##

The following requirements identify the data elements that **MUST** or **SHOULD** be populated when generating the payload. Data items not explicitly referenced in this section can be populated if the source system has captured this information.

### Composition resource ###

<table class="requirement-box">
  {% for item in site.data.oc_requirements.requirements %}
  {% if item.area == 'payload_comp' %}
  <tr>
    <td id="{{item.id}}">{{item.id}}</td>
    <td>{{item.description}}</td>
  </tr>
  {% endif %}
  {% endfor %}
</table>

The following requirements describe how the Composition resource is populated:

<table class="requirement-box">
  {% for item in site.data.oc_requirements.requirements %}
  {% if item.area == 'payload_comp_pop' %}
  <tr>
    <td id="{{item.id}}">{{item.id}}</td>
    <td>{{item.description}}</td>
  </tr>
  {% endif %}
  {% endfor %}
</table>
	


**Additional input elements**

Message senders **MAY** include additional binary documents in the payload as each expressed as an additional instance of the composition.section as described in [Send Document - payload structure](senddocument_payload.html#including-documents-in-the-payload).

<table class="requirement-box">
  {% for item in site.data.oc_requirements.requirements %}
  {% if item.area == 'payload_additional' %}
  <tr>
    <td id="{{item.id}}">{{item.id}}</td>
    <td>{{item.description}}</td>
  </tr>
  {% endif %}
  {% endfor %}
</table>

### Patient resource ###

<table class="requirement-box">
  {% for item in site.data.oc_requirements.requirements %}
  {% if item.area == 'payload_patient' %}
  <tr>
    <td id="{{item.id}}">{{item.id}}</td>
    <td>{{item.description}}</td>
  </tr>
  {% endif %}
  {% endfor %}
</table>

The [CareConnect-Patient-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Patient-1) in the payload is populated as follows:

<table class="requirement-box">
  {% for item in site.data.oc_requirements.requirements %}
  {% if item.area == 'payload_patient_pop' %}
  <tr>
    <td id="{{item.id}}">{{item.id}}</td>
    <td>{{item.description}}</td>
  </tr>
  {% endif %}
  {% endfor %}
</table>

### Organization resource ###

<table class="requirement-box">
  {% for item in site.data.oc_requirements.requirements %}
  {% if item.area == 'payload_org' %}
  <tr>
    <td id="{{item.id}}">{{item.id}}</td>
    <td>{{item.description}}</td>
  </tr>
  {% endif %}
  {% endfor %}
</table>

The [CareConnect-Organization-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Organization-1) resource present in the payload is populated as follows:

<table class="requirement-box">
  {% for item in site.data.oc_requirements.requirements %}
  {% if item.area == 'payload_org_pop' %}
  <tr>
    <td id="{{item.id}}">{{item.id}}</td>
    <td>{{item.description}}</td>
  </tr>
  {% endif %}
  {% endfor %}
</table>

### Practitioner resource ###

The [CareConnect-Practitioner-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Practitioner-1) resource present in the payload is populated as follows:

<table class="requirement-box">
  {% for item in site.data.oc_requirements.requirements %}
  {% if item.area == 'payload_prac_pop' %}
  <tr>
    <td id="{{item.id}}">{{item.id}}</td>
    <td>{{item.description}}</td>
  </tr>
  {% endif %}
  {% endfor %}
</table>

### RelatedPerson resource ###

The [CareConnect-RelatedPerson-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-RelatedPerson-1) in the payload is populated as follows:

<table class="requirement-box">
  {% for item in site.data.oc_requirements.requirements %}
  {% if item.area == 'payload_related_pop' %}
  <tr>
    <td id="{{item.id}}">{{item.id}}</td>
    <td>{{item.description}}</td>
  </tr>
  {% endif %}
  {% endfor %}
</table>

### Device resource ###

The [ITK-Device-1](https://fhir.nhs.uk/STU3/StructureDefinition/ITK-Device-1) resource present in the payload is populated as follows:

<table class="requirement-box">
  {% for item in site.data.oc_requirements.requirements %}
  {% if item.area == 'payload_device_pop' %}
  <tr>
    <td id="{{item.id}}">{{item.id}}</td>
    <td>{{item.description}}</td>
  </tr>
  {% endif %}
  {% endfor %}
</table>


### Encounter resource ###

The [CareConnect-Encounter-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Encounter-1) in the payload is populated as follows:

<table class="requirement-box">
  {% for item in site.data.oc_requirements.requirements %}
  {% if item.area == 'payload_encounter_pop' %}
  <tr>
    <td id="{{item.id}}">{{item.id}}</td>
    <td>{{item.description}}</td>
  </tr>
  {% endif %}
  {% endfor %}
</table>

### List/Observation resource ###

The [CareConnect-List-1](https://fhir.nhs.uk/STU3/StructureDefinition/CareConnect-List-1) in the payload is populated as follows:

<table class="requirement-box">
  {% for item in site.data.oc_requirements.requirements %}
  {% if item.area == 'payload_list_pop' %}
  <tr>
    <td id="{{item.id}}">{{item.id}}</td>
    <td>{{item.description}}</td>
  </tr>
  {% endif %}
  {% endfor %}
</table>

Each [CareConnect-Observation-1](https://fhir.nhs.uk/STU3/StructureDefinition/CareConnect-Observation-1) in the payload is populated as follows:

<table class="requirement-box">
  {% for item in site.data.oc_requirements.requirements %}
  {% if item.area == 'payload_obs_pop' %}
  <tr>
    <td id="{{item.id}}">{{item.id}}</td>
    <td>{{item.description}}</td>
  </tr>
  {% endif %}
  {% endfor %}
</table>

### Questionnaire resource ###

The [CareConnect-Questionnaire-1](https://fhir.nhs.uk/STU3/StructureDefinition/CareConnect-Questionnaire-1) in the payload is populated as follows:

<table class="requirement-box">
  {% for item in site.data.oc_requirements.requirements %}
  {% if item.area == 'payload_quest_pop' %}
  <tr>
    <td id="{{item.id}}">{{item.id}}</td>
    <td>{{item.description}}</td>
  </tr>
  {% endif %}
  {% endfor %}
</table>


### QuestionnaireResponse resource ###

The [CareConnect-QuestionnaireResponse-1](https://fhir.nhs.uk/STU3/StructureDefinition/CareConnect-QuestionnaireResponse-1) in the payload is populated as follows:

<table class="requirement-box">
  {% for item in site.data.oc_requirements.requirements %}
  {% if item.area == 'payload_questresp_pop' %}
  <tr>
    <td id="{{item.id}}">{{item.id}}</td>
    <td>{{item.description}}</td>
  </tr>
  {% endif %}
  {% endfor %}
</table>


### ReferralRequest resource ###

The [CareConnect-ReferralRequest-1](https://fhir.nhs.uk/STU3/StructureDefinition/CareConnect-ReferralRequest-1) in the payload is populated as follows:

<table class="requirement-box">
  {% for item in site.data.oc_requirements.requirements %}
  {% if item.area == 'payload_referral_pop' %}
  <tr>
    <td id="{{item.id}}">{{item.id}}</td>
    <td>{{item.description}}</td>
  </tr>
  {% endif %}
  {% endfor %}
</table>


## Resource optionality and cardinality ##

The following table lists the optionality and cardinality for each resource:

<table>
  <thead>
  <tr>
    <th>Resource</th>
    <th>Optionality</th>
	<th>Cardinality</th>
  </tr>
  </thead>
  <tbody>
  <tr>
    <td><a href="https://fhir.nhs.uk/STU3/StructureDefinition/ITK-Payload-Bundle-1)ITK-Payload-Bundle">ITK-Payload-Bundle</a></td>
    <td>Mandatory</td>
	<td>1..1</td>
  </tr>
  <tr>
    <td><a href="https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Composition-1">CareConnect-Composition-1</a></td>
    <td>Mandatory</td>
	<td>1..1</td>
  </tr>
  <tr>
    <td><a href="https://fhir.nhs.uk/STU3/StructureDefinition/ITK-Attachment-Binary-1">ITK-Attachment-Binary-1</a></td>
    <td>Mandatory</td>
	<td>1..*</td>
  </tr>
  <tr>
    <td><a href="https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Patient-1">CareConnect-Patient-1</a></td>
    <td>Mandatory</td>
	<td>1..1</td>
  </tr>
  <tr>
    <td><a href="https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Organization-1">CareConnect-Organization-1</a></td>
    <td>Mandatory</td>
	<td>1..1</td>
  </tr>
  <tr>
    <td><a href="https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Practitioner-1">CareConnect-Practitioner-1</a></td>
    <td>Required</td>
	<td>0..1</td>
  </tr>
  <tr>
    <td><a href="https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-RelatedPerson-1">CareConnect-RelatedPerson-1</a></td>
    <td>Required</td>
	<td>0..1</td>
  </tr>
  <tr>
    <td><a href="https://fhir.nhs.uk/STU3/StructureDefinition/ITK-Device-1">ITK-Device-1</a></td>
    <td>Required</td>
	<td>0..1</td>
  </tr>
  <tr>
    <td><a href="https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Encounter-1">CareConnect-Encounter-1</a></td>
    <td>Optional</td>
	<td>0..1</td>
  </tr>
  <tr>
    <td><a href="https://fhir.nhs.uk/STU3/StructureDefinition/CareConnect-List-1">CareConnect-List-1</a></td>
    <td>Optional</td>
	<td>0..1</td>
  </tr>
  <tr>
    <td><a href="https://fhir.nhs.uk/STU3/StructureDefinition/CareConnect-Observation-1">CareConnect-Observation-1</a></td>
    <td>Optional</td>
	<td>0..*</td>
  </tr>
  <tr>
    <td><a href="https://fhir.nhs.uk/STU3/StructureDefinition/CareConnect-Questionnaire-1">CareConnect-Questionnaire-1</a></td>
    <td>Optional</td>
	<td>0..1</td>
  </tr>
  <tr>
    <td><a href="https://fhir.nhs.uk/STU3/StructureDefinition/CareConnect-QuestionnaireResponse-1">CareConnect-QuestionnaireResponse-1</a></td>
    <td>Optional</td>
	<td>0..1</td>
  </tr>
  <tr>
    <td><a href="https://fhir.nhs.uk/STU3/StructureDefinition/CareConnect-ReferralRequest-1">CareConnect-ReferralRequest-1</a></td>
    <td>Optional</td>
	<td>0..1</td>
  </tr>
  </tbody>
</table>









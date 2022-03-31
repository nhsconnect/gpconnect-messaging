---
title: Patient requirements
keywords: use-case
tags: [use-case, send-update]
sidebar: sendupdate_sidebar
permalink: sendupdate_patient.html
summary: "Details of the Patient FHIR&reg; resource which make up the Send Update payload."
---

Please refer to [Send Update - Payload structure](sendupdate_payload.html) for a definition of the payload structure to be used.

## Patient resource population requirements ##

The following requirements identify the data elements that **MUST** or **SHOULD** be populated when generating the payload. Data items not explicitly referenced in this section can, and should, be populated if the source system has captured this information, and the resource being populated supports it.


### Patient resource ###

<table class="requirement-box">
  {% for item in site.data.sendupdate_usecase_requirements.requirements %}
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
  {% for item in site.data.sendupdate_usecase_requirements.requirements %}
  {% if item.area == 'payload_patient_pop' %}
  <tr>
    <td id="{{item.id}}">{{item.id}}</td>
    <td>{{item.description}}</td>
  </tr>
  {% endif %}
  {% endfor %}
</table>

### Patient example ###

{% highlight xml %}

<Patient>
	<id value="31686b67-9f20-4644-9a54-193d2f91de11" />
	<meta>
		<profile value="https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Patient-1" />
	</meta>
	<active value="true" />
	<identifier>
		<extension url="https://fhir.hl7.org.uk/STU3/StructureDefinition/Extension-CareConnect-NHSNumberVerificationStatus-1">
			<valueCodeableConcept>
				<coding>
					<system value="https://fhir.hl7.org.uk/STU3/CodeSystem/CareConnect-NHSNumberVerificationStatus-1" />
					<code value="01" />
					<display value="Number present and verified" />
				</coding>
			</valueCodeableConcept>
		</extension>
		<system value="https://fhir.nhs.uk/Id/nhs-number" />
		<value value="9989453457" />
	</identifier>
	<name>
		<use value="official" />
		<family value="Smith" />
		<given value="Richard" />
		<prefix value="Mr" />
	</name>
	<birthDate value="1957-01-09" />
	<gender value="male" />
	<address>
		<line value="2 Oxdale close" />
		<city value="Leeds" />
		<district value="West Yorkshire" />
		<postalCode value="LS112WS" />
	</address>
	<telecom>
		<system value="email" />
		<value value="example@gmail.com" />
	</telecom>
	<telecom>
		<system value="phone" />
		<value value="01273546540" />
	</telecom>
	<generalPractitioner>
		<display value="Example Dr" />
	</generalPractitioner>
</Patient>

{% endhighlight %}
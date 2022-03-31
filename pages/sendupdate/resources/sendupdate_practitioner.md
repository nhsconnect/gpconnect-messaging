---
title: Practitioner requirements
keywords: use-case
tags: [use-case, send-update]
sidebar: sendupdate_sidebar
permalink: sendupdate_practitioner.html
summary: "Details of the Practitioner FHIR&reg; resource which make up the Send Update payload."
---

Please refer to [Send Update - Payload structure](sendupdate_payload.html) for a definition of the payload structure to be used.

## Practitioner resource population requirements ##

The following requirements identify the data elements that **MUST** or **SHOULD** be populated when generating the payload. Data items not explicitly referenced in this section can, and should, be populated if the source system has captured this information, and the resource being populated supports it.


### Practitioner resource ###

The [CareConnect-Practitioner-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Practitioner-1) resource present in the payload is populated as follows:

<table class="requirement-box">
  {% for item in site.data.sendupdate_usecase_requirements.requirements %}
  {% if item.area == 'payload_prac_pop' %}
  <tr>
    <td id="{{item.id}}">{{item.id}}</td>
    <td>{{item.description}}</td>
  </tr>
  {% endif %}
  {% endfor %}
</table>

### Practitioner example ###

{% highlight xml %}

<Practitioner>
	<id value="d0269177-3edc-468b-9f70-971189158bcb" />
	<meta>
		<profile value="https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Practitioner-1" />
	</meta>
	<identifier>
		<system value="https://fhir.nhs.uk/Id/sds-user-id" />
		<value value="033345750518" />
	</identifier>
	<name>
		<family value="generated" />
		<given value="system" />
		<prefix value="exampleOCsystem" />
		<use value="official" />
	</name>
	<telecom>
		<system value="phone" />
		<value value="01136323200" />
		<use value="work" />
	</telecom>
</Practitioner>
			
{% endhighlight %}
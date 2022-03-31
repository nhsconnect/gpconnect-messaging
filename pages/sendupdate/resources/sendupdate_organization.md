---
title: Organization requirements
keywords: use-case
tags: [use-case, send-update]
sidebar: sendupdate_sidebar
permalink: sendupdate_organization.html
summary: "Details of the Organization FHIR&reg; resource which make up the Send Update payload."
---

Please refer to [Send Update - Payload structure](sendupdate_payload.html) for a definition of the payload structure to be used.


## Organization resource population requirements ##

The following requirements identify the data elements that **MUST** or **SHOULD** be populated when generating the payload. Data items not explicitly referenced in this section can, and should, be populated if the source system has captured this information, and the resource being populated supports it.


### Organization resource ###

<table class="requirement-box">
  {% for item in site.data.sendupdate_usecase_requirements.requirements %}
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
  {% for item in site.data.sendupdate_usecase_requirements.requirements %}
  {% if item.area == 'payload_org_pop' %}
  <tr>
    <td id="{{item.id}}">{{item.id}}</td>
    <td>{{item.description}}</td>
  </tr>
  {% endif %}
  {% endfor %}
</table>

### Organization example ###

{% highlight xml %}

<Organization>
	<id value="ab71659b-8b8d-43df-b6ba-7f755e9dca64" />
	<meta>
		<profile value="https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Organization-1" />
	</meta>
	<identifier>
		<system value="https://fhir.nhs.uk/Id/ods-organization-code" />
		<value value="8JJ28" />
	</identifier>
	<name value="exampleOCsystem" />
	<telecom>
		<system value="phone" />
		<value value="01136323200" />
		<use value="work" />
	</telecom>
</Organization>

{% endhighlight %}
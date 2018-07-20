---
title: Send Document - Payload structure
keywords: document, payload
tags: [document]
sidebar: senddocument_sidebar
permalink: senddocument_payload.html
summary: "Send Document capability - payload structure"
---

The payload of a GP Connect message which uses the Send Document capability **MUST** have the structure illustrated in the diagram below:

![Send Document - Payload](images/senddocument/senddocument_payload.png) 

The Send Document payload recognises that for most scenarios, messages which are intended to update target organisations’ records will result in a task being created in the target system workflow. As a result, the Task resource is used to describe the intent of the message - to request that a task be created in the target organisation to review and perform an update.

The following requirements describe the structure of the Send Document payload:

- The ITK3 `MessageHeader.focus` element **MUST** be a reference to a [Bundle](https://www.hl7.org/fhir/bundle.html) resource which conforms to the [ITK-Payload-Bundle](https://fhir.nhs.uk/STU3/StructureDefinition/ITK-Payload-Bundle-1) profile.

The `ITK-Payload-Bundle` **MUST** contain the following resource entries:

- An instance of the HL7 [Task](https://www.hl7.org/fhir/task.html) base resource.
- An Organization resource which conforms to the [CareConnect-Organization-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Organization-1) profile describing the organisation which sends the message. The `Task.requester.OnBehalfOf` element **MUST** contain a reference to this resource.
- Where the message contains patient information, for example as a result of a healthcare event, a patient resource **MUST** be present which conforms to the [CareConnect-Patient-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Patient-1) profile. When present, the `Task.for` element **MUST** contain a reference to this resource.
- Where the message contains patient information, for example as a result of a healthcare event, a practitioner resource **MUST** be present which conforms to the [CareConnect-Practitioner-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Patient-1) profile. This resource describes the primary practitioner who delivered care. When present, the `Task.requester.agent` element **MUST** contain a reference to this resource.
- Where the message sender knows the single intended recipient organisation for the message, an Organization resource **MUST** be present which conforms to the [CareConnect-Organization-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Organization-1) profile, describing the organisation which is the target of the message. The `Task.requester.owner` element **MUST** contain a reference to this resource.
 

Please refer to the particular use case in question for detailed requirements on the population of these payload resources.

## Payload Message Definition ##

The FHIR MessageDefinition resource provides a formal, machine-readable definition of a message shared between systems. Please refer to [ITK3 Message Definitions](https://nhsconnect.github.io/ITK3-FHIR-Messaging-Distribution/explore_defs_overview.html) for an overview of how MessageDefinition resources are used in ITK3 messages.

The GP Connect Send Document capability has defined a MessageDefinition resource instance which describes the *payload* of the FHIR Message, as defined on at [ITK3 Message Definition Patterns](https://nhsconnect.github.io/ITK3-FHIR-Messaging-Distribution/explore_defs_overview.html#message-definition-patterns)

The Message Definition for the GP Connect Send Document message payload is provided below. This definition can be used by FHIR tools such as [FHIR Check](http://clarotech.co.uk/products/tool-fhir-check/) to verify that particular instance of a Send Document message is conformant.


```xml

<MessageDefinition xmlns="http://hl7.org/fhir" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://hl7.org/fhir ../Schemas/messagedefinition.xsd">
	<meta>
		<profile value="https://fhir.nhs.uk/STU3/StructureDefinition/ITK-MessageDefinition-1"/>
	</meta>
	<url value="https://fhir.nhs.uk/STU3/MessageDefinition/ITK-SendTask-MessageDefinition-Instance-1"/>
	<identifier>
		<system value="https://tools.ietf.org/html/rfc4122"/>
		<value value="425b5f3a-faf0-469f-a2dc-5f716a777e02">
		</value>
	</identifier>
	<version value="1.0.0"/>
	<title value="GP Connect Writeback Message Definition"/>
	<status value="active"/>
	<date value="2018-02-23T16:06:00+00:00"/>
	<event>
		<system value="https://fhir.nhs.uk/STU3/CodeSystem/ITK-MessageEvent-2"/>
		<code value="ITK007C"/>
		<display value="ITK GP Connect Send Document"/>
	</event>
	<category value="Notification"/>
	<focus>
		<code value="Bundle"/>
		<profile>
			<extension url="https://fhir.nhs.uk/STU3/StructureDefinition/Extension-ITK-BundledAssets-1">
			
				<!-- to allow STU3 ITK-Payload-Bundle-1 to be used in the payload -->				
				<extension url="utilisedAsset">
					<extension url="type">
						<valueCoding>
							<system value="https://fhir.nhs.uk/STU3/CodeSystem/ITK-AssetType"/>
							<code value="P"/>
							<display value="Profile"/>
						</valueCoding>
					</extension>
					<extension url="reference">
						<valueReference>
							<reference value="https://fhir.nhs.uk/STU3/StructureDefinition/ITK-Payload-Bundle-1"/>
						</valueReference>
					</extension>
					<extension url="version">
						<valueString value="1.0.0"/>
					</extension>
				</extension>			
			
				<!-- to allow STU3 CareConnect-Patient-1 to be used in the payload -->				
				<extension url="utilisedAsset">
					<extension url="type">
						<valueCoding>
							<system value="https://fhir.nhs.uk/STU3/CodeSystem/ITK-AssetType"/>
							<code value="P"/>
							<display value="Profile"/>
						</valueCoding>
					</extension>
					<extension url="reference">
						<valueReference>
							<reference value="https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Patient-1"/>
						</valueReference>
					</extension>
					<extension url="version">
						<valueString value="1.0.0"/>
					</extension>
				</extension>
				
				<!-- to allow STU3 CareConnect-Practitioner-1 to be used in the payload -->					
				<extension url="utilisedAsset">
					<extension url="type">
						<valueCoding>
							<system value="https://fhir.nhs.uk/STU3/CodeSystem/ITK-AssetType"/>
							<code value="P"/>
							<display value="Profile"/>
						</valueCoding>
					</extension>
					<extension url="reference">
						<valueReference>
							<reference value="https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Practitioner-1"/>
						</valueReference>
					</extension>
					<extension url="version">
						<valueString value="1.0.0"/>
					</extension>
				</extension>
				
				<!-- to allow STU3 CareConnect-Organization-1 to be used in the payload -->				
				<extension url="utilisedAsset">
					<extension url="type">
						<valueCoding>
							<system value="https://fhir.nhs.uk/STU3/CodeSystem/ITK-AssetType"/>
							<code value="P"/>
							<display value="Profile"/>
						</valueCoding>
					</extension>
					<extension url="reference">
						<valueReference>
							<reference value="https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Organization-1"/>
						</valueReference>
					</extension>
					<extension url="version">
						<valueString value="1.0.0"/>
					</extension>
				</extension>
				
				<!-- to allow STU3 base Task to be used in the payload -->
				<extension url="utilisedAsset">
					<extension url="type">
						<valueCoding>
							<system value="https://fhir.nhs.uk/STU3/CodeSystem/ITK-AssetType"/>
							<code value="P"/>
							<display value="Profile"/>
						</valueCoding>
					</extension>
					<extension url="reference">
						<valueReference>
							<reference value="https://www.hl7.org/fhir/task.html"/>
						</valueReference>
					</extension>
					<extension url="version">
						<valueString value="1.0.0"/>
					</extension>
				</extension>

				<!-- to allow SNOMED CT to be used in the payload -->
				<extension url="utilisedAsset">
					<extension url="type">
						<valueCoding>
							<system value="https://fhir.nhs.uk/STU3/CodeSystem/ITK-AssetType"/>
							<code value="VS"/>
							<display value="Value set"/>
						</valueCoding>
					</extension>
					<extension url="reference">
						<valueReference>
							<reference value="http://snomed.info/sct"/>
						</valueReference>
					</extension>
					<extension url="version">
						<valueString value="latest release"/>
					</extension>
				</extension>

				<!-- to allow for any code system used in payload -->
				<extension url="utilisedAsset">
					<extension url="type">
						<valueCoding>
							<system value="https://fhir.nhs.uk/STU3/CodeSystem/ITK-AssetType"/>
							<code value="CS"/>
							<display value="Code System"/>
						</valueCoding>
					</extension>
					<extension url="reference">
						<valueReference>
							<reference value="https://fhir.nhs.uk/STU3/CodeSystem/any"/>
						</valueReference>
					</extension>
					<extension url="version">
						<valueString value="any"/>
					</extension>
				</extension>
				
				<!-- to allow any concept map to be used in the payload -->
				<extension url="utilisedAsset">
					<extension url="type">
						<valueCoding>
							<system value="https://fhir.nhs.uk/STU3/CodeSystem/ITK-AssetType"/>
							<code value="CM"/>
							<display value="Concept Map"/>
						</valueCoding>
					</extension>
					<extension url="reference">
						<valueReference>
							<reference value="https://fhir.nhs.uk/STU3/ConceptMap/any"/>
						</valueReference>
					</extension>
					<extension url="version">
						<valueString value="any"/>
					</extension>
				</extension>				
			</extension>
			<reference value="https://fhir.nhs.uk/STU3/StructureDefinition/ITK-Payload-Bundle-1"/>
		</profile>
	</focus>
	
	<allowedResponse>
		<message>
			<reference value="https://fhir.nhs.uk/STU3/MessageDefinition/ITK-BusAck-MessageDefinition-1">
			</reference>
		</message>
	</allowedResponse>
	<allowedResponse>
		<message>
			<reference value="https://fhir.nhs.uk/STU3/MessageDefinition/ITK-InfAck-MessageDefinition-1">
			</reference>
		</message>
	</allowedResponse>

</MessageDefinition>

```



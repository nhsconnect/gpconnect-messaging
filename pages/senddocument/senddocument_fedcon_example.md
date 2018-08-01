---
title: Example Message
keywords: document, usecase
tags: [mesh, itk3, use-case]
sidebar: senddocument_sidebar
permalink: senddocument_fedcon_example.html
summary: "Federated encounter summary - example message."
---

The message given below arises from the following fictional scenario:

>*Mr Richard Smith has attended an out-of-hours appointment at Cumbria Starling Medical Centre where he saw Dr Pritchard. His registered practice, Osprey Medical Centre is part of a federation which includes Starling, and the federation has set up a rotating out-of-hours evening surgery which runs one night per week. This week's out-of-hours appointments were provided by Starling.*

>*After the consultation, the clinical system used by Cumbria Starling Medical Centre sends a message to the clinical system used by Osprey with details of the consultation, in order that Mr Smith's care record is updated.*

Message example:

```xml
<?xml version="1.0" encoding="UTF-8"?>
<Bundle xmlns="http://hl7.org/fhir">
  <!-- ================START of the ITK FHIR message (bundle of type "message"   ======================= -->
  <id value="d12dc439-ca5c-4177-bb70-4fece88edab0" />
  <meta>
    <profile value="https://fhir.nhs.uk/STU3/StructureDefinition/ITK-Message-Bundle-1" />
  </meta>
  <type value="message" />
  <!-- ================ITK message header (always the first resource in the FHIR message bundle)======== -->
  <entry>
    <fullUrl value="urn:uuid:ea7221b8-3cc0-4b11-bc95-585b056b5428" />
    <resource>
      <MessageHeader>
        <id value="ea7221b8-3cc0-4b11-bc95-585b056b5428" />
        <meta>
          <profile value="https://fhir.nhs.uk/STU3/StructureDefinition/ITK-MessageHeader-2" />
        </meta>
        <extension url="https://fhir.nhs.uk/STU3/StructureDefinition/Extension-ITK-MessageHandling-2">
          <!-- Request Business ACK -->
          <extension url="BusAckRequested">
            <valueBoolean value="true" />
          </extension>
          <!-- Request Infrastructure ACK -->
          <extension url="InfAckRequested">
            <valueBoolean value="true" />
          </extension>
          <!-- For Information / For Action -->
          <extension url="RecipientType">
            <valueCoding>
              <system value="https://fhir.nhs.uk/STU3/CodeSystem/ITK-RecipientType-1" />
              <code value="FA" />
              <display value="For Action" />
            </valueCoding>
          </extension>
          <!-- Message priority -->
          <extension url="Priority">
            <valueCoding>
              <system value="https://fhir.nhs.uk/STU3/CodeSystem/ITK-Priority-1" />
              <code value="routine" />
              <display value="Routine" />
            </valueCoding>
          </extension>
          <!-- Message payload definition for GP Connect -->
          <extension url="MessageDefinition">
            <valueReference>
              <reference value="https://fhir.nhs.uk/STU3/MessageDefinition/ITK-SendTask-MessageDefinition-Instance-1" />
            </valueReference>
          </extension>
          <!-- Sender Reference - unique identifier of consultation -->
          <extension url="SenderReference">
            <valueString value="846ebe66-5ff8-4499-bc57-a112d3d0daa3" />
          </extension>
        </extension>
        <!-- MESH mailbox ID of message sender -->
        <source>
          <endpoint value="MESHGP0001" />
        </source>
        <event>
          <system value="https://fhir.nhs.uk/STU3/CodeSystem/ITK-MessageEvent-2" />
          <code value="ITK007C" />
          <display value="ITK GP Connect Send Document" />
        </event>
        <sender>
          <reference value="Organization/c0bee62f-9932-4468-9508-71c67a9f0c2c" />
        </sender>
        <timestamp value="2018-07-12T10:30:16+00:00" />
        <!--- The ITK3 message payload contained within the resource referenced -->
        <focus>
          <reference value="Bundle/70c35c4a-65f4-4a03-bcf7-d1041ab999fd" />
        </focus>
      </MessageHeader>
    </resource>
  </entry>
  <!--- ITK3 message header reference to message sender  -->
  <entry>
    <fullUrl value="urn:uuid:c0bee62f-9932-4468-9508-71c67a9f0c2c" />
    <resource>
      <Organization>
        <id value="c0bee62f-9932-4468-9508-71c67a9f0c2c" />
        <meta>
          <profile value="https://fhir.nhs.uk/STU3/StructureDefinition/CareConnect-ITK-Header-Organization-1" />
        </meta>
        <identifier>
          <system value="https://fhir.nhs.uk/Id/ods-organization-code" />
          <value value="GP0001" />
        </identifier>
      </Organization>
    </resource>
  </entry>
  <!--- ITK3 payload bundle, referenced from ITK3 message header focus -->
  <entry>
    <fullUrl value="urn:uuid:70c35c4a-65f4-4a03-bcf7-d1041ab999fd" />
    <resource>
      <bundle>
        <id value="70c35c4a-65f4-4a03-bcf7-d1041ab999fd" />
        <meta>
          <profile value="https://fhir.nhs.uk/STU3/StructureDefinition/ITK-Payload-Bundle-1" />
        </meta>
        <type value="collection" />
        <!-- ================Task in Payload Bundle - request to create new task at registered practice======= -->
        <entry>
          <fullUrl value="urn:uuid:e1580b71-99bd-4c5b-8d54-9b420418135f" />
          <resource>
            <Task>
              <id value="e1580b71-99bd-4c5b-8d54-9b420418135f" />
              <meta>
                <profile value="https://fhir.hl7.org.uk/StructureDefinition/STU3/CareConnect-Task-1" />
              </meta>
              <intent value="plan" />
              <status value="requested" />
              <description value="Request to update patient record with NHS Number {NHS Number} with the details of the encounter which took place at practice {ODS Code}" />
              <for>
                <!-- Patient reference -->
                <reference value="Patient/31686b67-9f20-4644-9a54-193d2f91de11" />
              </for>
              <requester>
                <agent>
                  <!-- Federated practice Practitioner reference -->
                  <reference value="Practitioner/d0269177-3edc-468b-9f70-971189158bcb" />
                </agent>
                <onBehalfOf>
                  <!-- Federated practice Organization reference -->
                  <reference value="Organization/ab71659b-8b8d-43df-b6ba-7f755e9dca64" />
                </onBehalfOf>
              </requester>
              <owner>
                <!-- Registered practice Organization reference -->
                <reference value="Organization/53edbfae-7043-410d-aaa6-205e465abfdf" />
              </owner>
              <input>
                <!-- Embedded PDF encounter details -->
                <type>
                  <text value="Federated Encounter Summary" />
                </type>
                <valueAttachment>
                  <contentType value="application/pdf" />
                  <data value="Tm90IHdvcnRoIGRlY29kaW5nIQTm90IHTm90IHdvcnRoIGRlY29kaW5nIQdvcnRoIGRlY29kaW5nIQTm90IHdvcnRoIGRlY29kaW5nIQTm90IHdvcnRoIGRlY29kaW5nIQTm90IHdvcnRoIGRlY29kaW5nIQTm90IHdvcnRoIGRlY29kaW5nIQ==" />
                </valueAttachment>
              </input>
            </Task>
          </resource>
        </entry>
        <!-- ================Practitioner in Payload Bundle - Practitioner who delivered care================= -->
        <entry>
          <fullUrl value="urn:uuid:d0269177-3edc-468b-9f70-971189158bcb" />
          <resource>
            <Practitioner>
              <id value="d0269177-3edc-468b-9f70-971189158bcb" />
              <meta>
                <profile value="https://fhir.hl7.org.uk/StructureDefinition/STU3/CareConnect-Practitioner-1" />
              </meta>
              <identifier>
                <system value="https://fhir.nhs.uk/Id/sds-user-id" />
                <value value="033345750518" />
              </identifier>
              <name>
                <family value="Pritchard" />
                <given value="Gary" />
                <prefix value="Dr" />
              </name>
              <telecom>
                <system value="phone" />
                <value value="01136323200" />
                <use value="work" />
              </telecom>
            </Practitioner>
          </resource>
        </entry>
        <!-- ================Organization in Payload Bundle - Federated practice where encounter took place=== -->
        <entry>
          <fullUrl value="urn:uuid:ab71659b-8b8d-43df-b6ba-7f755e9dca64" />
          <resource>
            <Organization>
              <id value="ab71659b-8b8d-43df-b6ba-7f755e9dca64" />
              <meta>
                <profile value="https://fhir.hl7.org.uk/StructureDefinition/CareConnect-Organization-1" />
              </meta>
              <identifier>
                <system value="https://fhir.nhs.uk/Id/ods-organization-code" />
                <value value="GP0001" />
              </identifier>
              <name value="Cumbria Starling Medical Centre" />
              <telecom>
                <system value="phone" />
                <value value="01136323200" />
                <use value="work" />
              </telecom>
            </Organization>
          </resource>
        </entry>
        <!-- ================Organization in Payload Bundle- Registered practice of patient=================== -->
        <entry>
          <fullUrl value="urn:uuid:31686b67-9f20-4644-9a54-193d2f91de22" />
          <resource>
            <Organization>
              <id value="31686b67-9f20-4644-9a54-193d2f91de22" />
              <meta>
                <profile value="https://fhir.hl7.org.uk/StructureDefinition/CareConnect-Organization-1" />
              </meta>
              <identifier>
                <system value="https://fhir.nhs.uk/Id/ods-organization-code" />
                <value value="GP0002" />
              </identifier>
              <name value="Cumbria Osprey Medical Centre" />
              <telecom>
                <system value="phone" />
                <value value="01136323201" />
                <use value="work" />
              </telecom>
            </Organization>
          </resource>
        </entry>
        <!-- ================Patient in Payload Bundle- Subject of encounter at federated practice============ -->
        <entry>
          <fullUrl value="urn:uuid:31686b67-9f20-4644-9a54-193d2f91de11" />
          <resource>
            <Patient>
              <id value="urn:uuid:31686b67-9f20-4644-9a54-193d2f91de11" />
              <meta>
                <profile value="https://fhir.hl7.org.uk/StructureDefinition/CareConnect-Patient-1" />
              </meta>
              <active value="true" />
              <name>
                <use value="official" />
                <family value="Smith" />
                <given value="Richard" />
                <prefix value="Mr" />
              </name>
              <birthDate value="1957-01-09" />
            </Patient>
          </resource>
        </entry>
      </bundle>
      <!---end of payload bundle -->
    </resource>
  </entry>
</Bundle>
<!-- end of message bundle -->
<!-- ==========================END OF FHIR Message bundle================================================= -->
```





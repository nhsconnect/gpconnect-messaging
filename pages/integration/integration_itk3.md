---
title: Use of the ITK3 to support GP Connect Messaging
keywords: mesh, itk3
tags: [integration, mesh, itk3]
sidebar: overview_sidebar
permalink: integration_itk3.html
summary: "Use of ITK3 to support GP Connect Messaging"
---

## Using ITK3 to support GP Connect Messaging ##

<table class="requirement-box">
  <tr>
    <td><strong>GPCM-C-2</strong></td>
    <td>All FHIR Messages <strong>MUST</strong> conform to the ITK3 Message Distribution Standard, v2.5.0</td>
  </tr>
</table>

As described in [Design Principles](design_principles.html#reliability-itk3), the [ITK3 Message Distribution standard, v2.5.0](https://developer.nhs.uk/apis/itk3messagedistribution-2-5-0/) has been adopted by GP Connect Messaging capabilities to provide message reliability and to facilitate alignment with practice workflow.

### FHIR messages ###

All messages sent according to the ITK3 standard specification are constructed using the HL7 FHIR&reg; STU3 standard using the FHIR Messaging framework.

The ITK3 standard builds on the [FHIR Messaging framework](https://www.hl7.org/fhir/messaging.html) through a set of messaging extensions, which are provided through a [profile of FHIR MessageHeader](https://fhir.nhs.uk/STU3/StructureDefinition/ITK-MessageHeader-2/_history/2.1) resource. 

This extension of the FHIR messaging framework provides some messaging options such as:

- the ability for a sender to request a positive or negative "infrastructure" acknowledgement message to be returned which indicates the success or failure of the processing of the message at a technical level
- the ability for a sender to request a positive or negative "business" acknowledgement message to be returned which indicates the success or failure of the processing of the message at a business process level
- various message meta-data elements

Please refer to the [messaging capability](senddocument.html) and [messaging use case](senddocument_fedcon_overview.html) pages for details of which of these options is mandated or recommended for the particular message being created.

### ITK3 response processing ###

Where the message sender requests an ITK3 acknowledgement (known as ITK3 Response), the sending system is responsible for processing the received acknowledgement and acting accordingly.

For example, where an ITK3 Response indicates that a technical error was processed by the receiver when validating the message, the message sender is responsible for taking the action necessary to re-send a corrected message.    

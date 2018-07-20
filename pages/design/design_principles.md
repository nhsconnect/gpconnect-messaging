---
title: GP Connect Messaging - Design Principles
keywords: design, messaging
tags: [design,messaging, itk3, mesh]
sidebar: overview_sidebar
permalink: design_principles.html
summary: "Principles which guide the GP Connect Messaging product"
---

## Design principles ##

The following design principles have guided the approach to how updates to GP systems are facilitated.

### Business process integration ###

GP system suppliers have implemented rich workflow solutions to enable management of incoming healthcare events. Frequently these incoming events result in the creation of tasks with associated workflows, which are assigned in a flexible and configurable way by each practice to suit their particular requirements. These solutions provide options for practices to define how this information is treated according to message type and content - enabling the definition of rules to automate the application of updates where this is deemed appropriate.

Senders of healthcare events frequently follow business processes which include a requirement that the target organisation not only acknowledges receipt of the message, but also includes expectation of notification of workflow events which cannot immediately be generated upon message receipt.  

Therefore, the approach taken to facilitate updates to GP systems originating outside the practice has sought to align closely with these existing practice workflow capabilities and requirements.

### Communication paradigm: asynchronous messaging ###

An asynchronous messaging approach offered a clearest alignment to the long-running workflow processes described above.  

An HTTP synchronous approach, as used by the [GP Connect FHIR API](https://nhsconnect.github.io/gpconnect/), was considered. However, a synchronous model fits best the immediacy of a request/response pattern used when reading GP practice data for a direct care use case.  For this reason, the extension of the GP Connect FHIR API to support record updates was not selected.

### Asynchronous transport: MESH ###

With the choice of an asynchronous communication paradigm, the natural choice for transport was [MESH](https://digital.nhs.uk/services/message-exchange-for-social-care-and-health-mesh), which is the strategic platform already in place to support the asynchronous messaging needs of the NHS.

MESH (and its predecessor DTS) is a proven platform which has successfully supported NHS messaging requirements for a number of years. One of the main benefits of which MESH brings is excellent reach.

MESH connectivity has already been implemented widely across the NHS, and importantly, is already built into support message flows incoming to GP practices in all GP core clinical system implementations.  

### Asynchronous messaging paradigms ###

Messages flowing into GP practices on MESH will arise mainly from the following two patterns of event notification:

#### 1. Point to point event notification ####

Where the message sender knows which party or parties the message is intended for, a point to point event notification is often used. Here the sender directs the message to a known recipient or set of recipients.

For example, the [Send federated consultation summary](senddocument_fedcon.html) use case of the [Send Document](senddocument.html) capability uses this pattern. The federated practice knows that the consultation summary is intended only for a single known recipient organisation - the registered practice of the patient. Therefore, this pattern is used for this use case, and the MESH Endpoint Lookup Service is used as a broker to facilitate this message delivery pattern


#### 2. Publish/Subscribe event notification ####

This pattern would be more applicable where a healthcare event has taken place, but the message sender does not know all the parties who are interested in that event.

In this model, organisations will subscribe at an event hub to those events in which they have a legitimate interest. The sender publishes an event to this event hub, and all the subscribers to the event will receive the event details.  


### Messaging format : FHIR STU3 Messages ###

The [HL7 FHIR Message framework](https://www.hl7.org/fhir/messaging.html) was chosen as the standard means of communicating health event information in a messaging context. 

### Reliability: ITK3 ###

As these messages usually convey information about a clinical event which has taken place in delivering patient healthcare, it is necessary that this message is delivered reliably.

Reliable delivery of a message can be considered from the perspective of the sender and the receiver:

- a message sender is likely to need confirmation that the message has been successfully delivered and acted upon. In addition, the sender will often need to know if the receiver encountered an issue when processing the message in order to take action
- a message receiver is likely to require a capability that the sender can be notified if a technical or business process issue occurs in processing of the message

The [ITK3 Message Distribution Standard](https://nhsconnect.github.io/ITK3-FHIR-Messaging-Distribution/) provides a standard means of delivering these message reliability requirements. As the ITK3 standard is built using a lightweight FHIR STU3 profile of the FHIR Message framework to deliver these requirements, it was the natural choice as design component to provide message reliability.

ITK3 also makes available a number of message metadata elements which enable better integration with practice workflow systems.
    
### Re-usability: payload re-use ###

In designing a payload to meet a particular use case, care has been taken to design the payload in such a way that it may be re-used to fulfil other identified uses cases through configuration change only.

For example, the "Send federated encounter summary" use case makes use of the more general payload type [Send Document](senddocument.html). Should a future use case arise where a document needs to be sent, the same payload can be re-used.


 

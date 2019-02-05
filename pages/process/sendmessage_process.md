---
title: Process map
keywords: use-case
tags: [use-case]
sidebar: senddocument_sidebar
permalink: sendmessage_process.html
summary: "Process map for Send Federated Consultation Report"
---

## Purpose ##

This page describes the business process for the Send Federated Consultation Report use case in order to fully understand the business requirements.
 
## Process ##

This process describes the steps/actions involved in the Federated Consultation Report use case where a consultation is written within the provider system and is sent to the consumer system at the patient’s registered GP practice.

Two common requirements must be met for this process to proceed:
- the clinician writes a consultation for a patient; and
- the patient being treated is not registered at the practice where the consultation is written AND is registered at a GP practice within the same federation (or a group of GP practices working together to deliver a service)

Federated consultation reports will be sent three hours (locally configurable) after the consultation is saved and committed to the patient’s clinical record.
 
Where a clinician makes further updates to the consultation notes before the three hour gap, a single report is sent.

Where the consultation notes are edited after the report has already been sent, an updated version of the report is sent.
 
Additional reports are clearly marked with a version number. 
 
 
### Process map ###

![Send Federated Consultation Report process map](images/senddocument/sendmessage_process.jpg "Send Federated Consultation Report process map") 

 
### Steps ###

**1. Write consultation**

Clinician inputs the details of the consultation into the GP provider system. Data inputted could be free text or clinical codes which may be entered manually or through the use of clinical templates. It could include adding attachments/documents (for example pain point diagram, ECG, photo). This is no different from the normal method of writing a consultation for a patient registered at the GP practice.

**2. Save consultation**

The clinician manually saves the consultation notes and commits them to the patient record.

**3. Save consultation into patient record**

The provider system saves the consultation notes into the patient’s electronic record at the federated GP practice.

**4. Wait three hours (locally configurable)**

The provider system waits three hours before the process moves on. This gives time for the clinician to make any necessary updates to the consultation to reduce the chance of the report being sent multiple times.

The period of time that the clinical system waits before sending a message can be configured by each GP practice to meet their local needs.

**5. Further updates to the consultation?**

If the user makes changes to the consultation notes in the patient record within three hours, the process moves back to step 1.

Otherwise, the process moves on to step 6.

There may be many reasons why the consultation is not completed when initially saved: 
- the clinician may not have time to finish the consultation notes and must continue with treating other patients
- the clinician may wish to ask a colleague for advice
- the clinician may be off-site and will finish writing the consultation notes when they have returned to the GP practice
- the results of a test may be required before the clinician can complete their notes
- the clinician may have forgotten to add some important information when originally writing the consultation notes

**6. Generate PDF and metadata**

A FHIR message is generated which contains a PDF which contains all the information recorded in the consultation (including free text, clinical coding and other data entered relating to the consultation).

The ITK3 FHIR Message is generated, which must include:
- FHIR MessageHeader
- FHIR STU3 task
- PDF file, its contents and metadata
- all attachments/documents recorded with the consultation

Further details on the message content can be found at:
[Send Document Payload](senddocument_payload.html)

When the PDF is generated, the provider system checks for previous versions of the PDF linked to this consultation. A previous version will exist if the clinician updates the consultation more than three hours after it was initially saved and committed. If there are no previous versions, the PDF is designated as [version 1]. If there are previous versions, the PDF is designated [version 2/3/4…n]. The version number is displayed in the title of the PDF ("Federated Consultation Report Version x") and version field within the document itself. 

**7. Send message via MESH**

The provider system passes the message to the MESH client.

**8. MESH file transfer**

The MESH client transfers the message to the MESH inbox of the patient’s registered GP practice.

**9. Retrieve message from MESH**

The consumer system of the registered practice retrieves the message from their MESH inbox.

**10. Send infrastructure acknowledgement**

The consumer system sends an ITK3 FHIR Message to the provider system containing:
- FHIR MessageHeader
- FHIR OperationOutcome (ITK3 response with response code 10001 to 20013)

**11. Receive infrastructure acknowledgement**

The provider system records the infrastructure acknowledgement. If no acknowledgement is received within a reasonable time-frame (to be defined by system supplier), the provider system notifies an appropriate end user.

**12.	Add message into workflow**

The consumer system matches the message to a registered GP patient and presents the message to an appropriate user in a designated workflow.

**13. Send business acknowledgement**

The consumer system sends an ITK3 FHIR Message to the provider system containing:
- FHIR MessageHeader
- FHIR OperationOutcome (ITK3 response with response code 30001 to 30003)

**14. Receive business acknowledgement**

The provider system records the business acknowledgement. If no acknowledgement is received within a reasonable time-frame (configurable), the provider system notifies an appropriate end user.





---
title: Process map
keywords: use-case
tags: [use-case]
sidebar: senddocument_sidebar
permalink: sendmessage_oc_process.html
summary: "Process map for Online Consultation Report"
---

## Purpose ##

This page describes the business process for the Online Consultation Report use case in order to fully understand the business requirements.

## Process ##

This process describes the steps/actions involved in the Online Consultation Report use case where a online consultation is written within the OC system and is sent to the consumer system either at the patient’s registered GP practice, or an alternative care provider (for example, a community pharmacy).
 
## Process flows ##

The following process flows have be investigated and mapped out:

1. Online Consultation auto triage to an alternative care provider - the OC system has the ability to auto triage based on the information entered by the patient. The OC system makes the decision to send to an alternative care provider (in this case a community pharmacy).
2. Online Consultation auto triage to GP - the OC system has auto triaged the OC and made a decision to send back to the patient's registered GP practice.
3. Online Consultation manual triage to GP or an alternative care provider - the OC system has workflow functionality and OCs are worked on in the system. A decision is then made manually to either send the OC back to the patient's registered GP, or to forward to an alternative care provider (in this case a community pharmacy)


## Process map ##

Send Document – Online Consultation Report – Full process flow

![Online Consultation Report process map](images/senddocument/full_oc_process.png "Online Consultation Report process map") 

<a href="images/senddocument/full_oc_process.png" target="_blank">Open full process flow in new tab</a>

Each of the process flows covered in this diagram are broken down into their own diagrams with step explanations in the sections below.

### Process flow 1 ###

Send Document - Online Consultation Report - Process flow 1  (OC auto triage to alternative care provider, for example community pharmacy (CP))

![Online Consultation Report process map](images/senddocument/oc_process_1.png "Online Consultation Report process flow 1")

<a href="images/senddocument/oc_process_1.png" target="_blank">Open process flow 1 in new tab</a>
 
#### Steps ####

**1. Auto triage decision**

The OC system makes the decision to send the Online Consultation Report to a community pharmacy.

**2. OC Payload generation**

The OC payload is created, containing a PDF of the Online Consultation Report and any FHIR coded resources applicable.

**3. Send copy to GP practice**

A copy of the OC payload is sent to the patient's registered GP practice.

**4. Copy received by GP practice**

The copy OC payload is received by the GP practice. The payload is labelled as "For Information".

**5. Save online consultation into patient record**

The provider system saves the Online Consultation Report into the patient’s electronic record at the GP practice.

**6. Send OC payload to CP**

The OC payload is sent to the community pharmacy requested by the patient.

**7. Payload received by CP**

The OC payload is received by the community pharmacy. The payload is labelled as "For Action".

**8. DECISION A - CP accepts the OC**

The community pharmacy accepts the OC and saves the Online Consultation Report in the CP system.

**9. CP actions the OC**

The community pharmacy provides care for the patient.

**10. DECISION B - CP escalates the OC**

The community pharmacy does not accept the OC and escalates the OC back to the patient's registered GP practice.

**10. Send OC payload to GP**

The OC payload is sent to the patient's registered GP practice.

**11. Payload received by GP**

The OC payload is received by the patient's registered GP practice. The payload is labelled as "For Action".

**12. GP actions the OC**

The patient's registered GP practice accepts the OC and provides care for the patient.

### Process flow 2 ###
Send Document - Online Consultation Report - Process flow 2  (OC auto triage to GP practice)

![Online Consultation Report process map](images/senddocument/oc_process_2.png "Online Consultation Report process flow 2")

<a href="images/senddocument/oc_process_2.png" target="_blank">Open process flow 2 in new tab</a>

#### Steps ####

**1. Auto triage decision**

The OC system makes the decision to send the Online Consultation Report to the patient's registered GP practice.

**2. OC Payload generation**

The OC payload is created, containing a PDF of the Online Consultation Report and any FHIR coded resources applicable.

**3. Send OC to GP practice**

The OC payload is sent to the patient's registered GP practice.

**4. Payload received by GP practice**

The OC payload is received by the GP practice. The payload is labelled as "For Action".

**5. Save online consultation into patient record**

The provider system saves the Online Consultation Report into the patient’s electronic record at the GP practice.

**6. GP actions the OC**

The patient's registered GP practice provides care for the patient.

### Process flow 3 ###
Send Document - Online Consultation Report - Process flow 3  (Manual triage to GP or alternative care provider, for example community pharmacy (CP))

![Online Consultation Report process map](images/senddocument/oc_process_3.png "Online Consultation Report process flow 3")

<a href="images/senddocument/oc_process_3.png" target="_blank">Open process flow 3 in new tab</a>

#### Steps ####

**1. DECISON A - Manual triage decision to community pharmacy**

The clinician working in the OC system makes the decision to send the Online Consultation Report to a community pharmacy.

**2. OC Payload generation**

The OC payload is created, containing a PDF of the Online Consultation Report and any FHIR coded resources applicable.

**3. Send copy to GP practice**

A copy of the OC payload is sent to the patient's registered GP practice.

**4. Copy received by GP practice**

The copy OC payload is received by the GP practice. The payload is labelled as "For Information".

**5. Save online consultation into patient record**

The provider system saves the Online Consultation Report into the patient’s electronic record at the GP practice.

**6. Send OC payload to CP**

The OC payload is sent to the community pharmacy requested by the patient.

**7. Payload received by CP**

The OC payload is received by the community pharmacy. The payload is labelled as "For Action".

**8. DECISION C - CP accepts the OC**

The community pharmacy accepts the OC and saves the Online Consultation Report in the CP system.

**9. CP actions the OC**

The community pharmacy provides care for the patient.

**10. DECISION D - CP escalates the OC**

The community pharmacy does not accept the OC and escalates the OC back to the patient's registered GP practice.

**10. Send OC payload to GP**

The OC payload is sent to the patient's registered GP practice.

**11. Payload received by GP**

The OC payload is received by the patient's registered GP practice. The payload is labelled as "For Action".

**12. GP actions the OC**

The patient's registered GP practice accepts the OC and provides care for the patient.

**13. DECISON B - Manual triage decision to GP practice**

The clinician working in the OC system makes the decision to send the Online Consultation Report to the GP practice.

**14. OC Payload generation**

The OC payload is created, containing a PDF of the Online Consultation Report and any FHIR coded resources applicable.

**15. Send OC to GP practice**

The OC payload is sent to the patient's registered GP practice.

**16. Payload received by GP practice**

The OC payload is received by the GP practice. The payload is labelled as "For Action".

**17. Save online consultation into patient record**

The provider system saves the Online Consultation Report into the patient’s electronic record at the GP practice.

**18. GP actions the OC**

The patient's registered GP practice provides care for the patient.
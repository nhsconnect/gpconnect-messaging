---
title: GP Connect Messaging 1.4.0-beta release notes
keywords: GP Connect Messaging, release notes
tags: [release]
sidebar: overview_sidebar
permalink: overview_release_notes_1_4_0.html
summary: "GP Connect 1.4.0-beta released on xxth March 2021"
toc: false
---

## Release overview ##

The GP Connect Messaging 1.4.0-beta release is a patch release including:

- additional use case to support Online Consultation Reports - sending an online consultation back to the patient’s registered GP practice, or to a patient selected alternative care provider. A PDF must be sent, but additional FHIR resources can be populated.
- additional use case to support Generic Send - sending generic documents in PDF format back to the patient’s registered GP practice.
- Send Document payload has been updated to contain the following FHIR resources:
  - [GPConnect-Device-1](https://fhir.nhs.uk/STU3/StructureDefinition/GPConnect-Device-1)
  - [CareConnect-GPC-List-1](https://fhir.nhs.uk/STU3/StructureDefinition/CareConnect-GPC-List-1)
  - [CareConnect-GPC-Observation-1](https://fhir.nhs.uk/STU3/StructureDefinition/CareConnect-GPC-Observation-1)
  - [CareConnect-QuestionnaireResponse-1](https://fhir.nhs.uk/STU3/StructureDefinition/CareConnect-QuestionnaireResponse-1)
  - [CareConnect-GPC-Location-1](https://fhir.nhs.uk/STU3/StructureDefinition/CareConnect-GPC-Location-1)

All requirements listed in 1.4.0 have been renumbered to align with core Send Document requirements and specific use case requirements.
 
## Page-by-page breakdown of changes ##

Pages updated to support new use cases:
- [Introduction to GP Connect Messaging](index.html)
- [Spine integration illustrated](integration_illustrated.html)
- [Integration to MESH](integration_mesh.html)
- [Send Document - Introduction](senddocument.html)
- [Send Document - Message payload](senddocument_payload.html)

Pages added to support Online Consultation Report use case:
- [Overview](senddocument_oc_overview.html)
- [Process map](sendmessage_oc_process.html)
- [User stories](senddocument_oc_userstories.html)
- [Clinical engagement](senddocument_oc_busreq_clinical.html)
- [Payload requirements](senddocument_oc_payload.html)
- [ITK3 header requirements](senddocument_oc_itk3.html)
- [MESH message configuration](senddocument_oc_mesh.html)
- [Triggering message creation](senddocument_oc_trigger.html)
- [Message example](senddocument_oc_example.html)

Pages added to support Generic Send use case:
- [Overview](senddocument_generic_overview.html)
- [Process map](sendmessage_generic_process.html)
- [User stories](senddocument_generic_userstories.html)
- [Clinical engagement](senddocument_generic_busreq_clinical.html)
- [Payload requirements](senddocument_generic_payload.html)
- [ITK3 header requirements](senddocument_generic_itk3.html)
- [MESH message configuration](senddocument_generic_mesh.html)
- [Triggering message creation](senddocument_generic_trigger.html)
- [Message example](senddocument_generic_example.html)

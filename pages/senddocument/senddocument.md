---
title: Send Document
keywords: document
tags: [send-document, messaging]
sidebar: senddocument_sidebar
permalink: senddocument.html
summary: "Introduction to the GP Connect Messaging Send Document capability"
---

The Send Document capability provides a simple and standardised means of sending a document, such as a PDF, an image, or HTML file to a care provider system. Each message sent using the Send Document capability makes use of the GP Connect Messaging components, ITK3, and MESH to deliver the message. 

All messages sent using this capability will be FHIR&reg; Messages, defined as a [FHIR composition](https://www.hl7.org/fhir/STU3/composition.html), constructed to meet the ITK3 standard and have a specific payload structure defined in each use case.

Use cases covered in this version of the specification:

1.  [Consultation Summary](senddocument_fedcon_overview.html) - supports sending a PDF summary of a patient encounter from a care organisation (GP, community nurse etc...) back to the patient's registered GP practice.
2.  [Online Consultation](senddocument_oc_overview.html) - supports sending an online consultation back to the patient's registered GP practice, or to a patient selected alternative care provider. A PDF must be sent, but additional FHIR resources can be populated.
3.  [Generic Send](senddocument_generic_overview.html) - supports sending generic documents in PDF format back to the patient's registered GP practice.

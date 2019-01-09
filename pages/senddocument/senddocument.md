---
title: Send Document
keywords: document
tags: [send-document, messaging]
sidebar: senddocument_sidebar
permalink: senddocument.html
summary: "Introduction to the GP Connect Messaging Send Document capability"
---

The Send Document capability provides a simple and standardised means of sending a document, such as a PDF, an image, or HTML file to a GP practice system. Each message sent using the Send Document capability makes use of the GP Connect Messaging components MESH and ITK3, [integrating with Spine](integration_illustrated.html) to deliver the message. 

All messages sent using this capability will be FHIR Messages constructed to meet the ITK3 standard and have a specific [payload](senddocument_payload) structure.

Each instance of a message which conforms to the Send Document capability will arise in the context of a specific health care use case, the first of which is the [Send Federated Consultation Summary](senddocument_fedcon_overview.html) use case. Specific messaging requirements will be associated with each use case.


{% include note.html content="**Disambiguation:**<br/>The Send Document capability does not include FHIR messages where the payload is defined as a [FHIR composition](https://www.hl7.org/fhir/composition.html), meeting the requirements of the [FHIR Document](https://www.hl7.org/fhir/documents.html) framework. This capability focuses primarily on facilitating the flow of binary documents across the NHS.
" %}

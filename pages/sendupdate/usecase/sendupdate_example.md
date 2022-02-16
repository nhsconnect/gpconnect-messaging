---
title: Message example
keywords: document, use-case
tags: [mesh, itk3, use-case, send-document]
sidebar: senddocument_sidebar
permalink: senddocument_generic_example.html
toc: false
summary: "Generic payload - example messages"
---

The message given below arises from the following fictional scenario:

>*Mr Richard Smith has completed an online consultation survey as requested by his GP. His registered practice is Osprey Medical Centre.*

>*After the online consultation, the online consultation system used by Osprey Starling Medical Centre sends a message to the clinical system used by Osprey Starling Medical Centre with details of the online consultation, in order that Mr Smith's care record is updated.*

### Message example ###

The following FHIR Message would be present as the .DAT file which is sent by the MESH client (or in the body of the HTTP response when [downloading a message from the MESH API](https://meshapi.docs.apiary.io/#reference/0/mesh-messages/download-message)).


{% include senddocument/oc_consultation_report.xml %}
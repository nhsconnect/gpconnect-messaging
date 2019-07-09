---
title: Message example
keywords: document, use-case
tags: [mesh, itk3, use-case, send-document]
sidebar: senddocument_sidebar
permalink: senddocument_fedcon_example.html
summary: "Send Federated Consultation Report - example message."
---

The message given below arises from the following fictional scenario:

>*Mr Richard Smith has attended an out-of-hours appointment at Cumbria Starling Medical Centre where he saw Dr Pritchard. His registered practice, Osprey Medical Centre is part of a federation which includes Starling, and the federation has set up a rotating out-of-hours evening surgery which runs one night per week. This week's out-of-hours appointments were provided by Starling.*

>*After the consultation, the clinical system used by Cumbria Starling Medical Centre sends a message to the clinical system used by Osprey with details of the consultation, in order that Mr Smith's care record is updated.*

### Message example ###

The following FHIR Message would be present as the .DAT file which is sent by the MESH client (or in the body of the HTTP response when [downloading a message from the MESH API](https://meshapi.docs.apiary.io/#reference/0/mesh-messages/download-message))


{% include senddocument/Send_Federated_Consultation_Report.xml %}
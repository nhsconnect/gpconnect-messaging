---
title: Message sender testing
keywords: testing, itk3, mesh
tags: [testing, itk3, mesh]
sidebar: overview_sidebar
permalink: testing_sender.html
summary: "Overview of the testing approach and tools available to support and assure message senders"
---

## Testing approach ##

Message senders will need to verify as part of the development process that messages being created are valid - meeting the requirements as stated in this specification for the use case in question.

NHS Digital will provide a "synthetic receiver" solution which will act as follows:

- a message sender sends a message to specific MESH mailbox ID which NHS Digital will provide
- this message arrives at the test mailbox and is picked up and validated by a FHIR Message validation tool 
- validation output is sent as a report to the message sender detailing any issues found with the message
- [TODO  - When the MESH Endpoint lookup service is used - how will test mailbox be targeted?]
- [TODO  - How is the report delivered? Email, MESH. How is this recipient address identified from the incoming message?]
- where the message has requested acknowledgements, the message validation tool will generate these responses as exemplars [Is this true?]

The validation report will indicate conformance to the specification at the following levels:
1. MESH / ITK requirements
2. Payload specific requirements

Please contact [NHS Digital Solution Assurance](https://digital.nhs.uk/services/solution-assurance) for further details.

---
title: Message sender testing
keywords: testing, itk3, mesh
tags: [testing, itk3, mesh]
sidebar: overview_sidebar
permalink: testing_sender.html
summary: "Overview of the testing approach and tools available to support and assure message senders"
---

## Testing approach ##

As part of the development process, message senders will need to verify that the messages being created are valid, and meet the requirements as stated in this specification for the use case in question

NHS Digital will provide a "synthetic receiver" solution which will act as follows:

- a message sender sends a message to specific MESH mailbox ID which NHS Digital will provide
- this message arrives at the test mailbox and is picked up and validated by a FHIR Message validation tool 
- validation output is sent as a report to the message sender detailing any issues found with the message
- where the message has requested acknowledgements, the message validation tool will generate these responses as exemplars. Default behaviour is to send positive acknowledgements, but negative acknowledgement can be triggered
 
Note: There are two ways of routing to the synthetic receiver, either through the specific MESH mailbox ID, or through the endpoint lookup service within the test environment. The endpoint lookup uses patient details (NHS No., DOB, Surname) within the MESH .ctl file to identify the synthetic receiver mailbox id, and then subsequently route onwards.

The validation report will indicate conformance to the specification at the following levels:
1. MESH / ITK requirements
2. payload specific requirements

For more information, please refer to [ITK3 test harness](https://developer.nhs.uk/itk3-test-harness/) and [ITK3 test harness user guidance](https://developer.nhs.uk/wp-content/uploads/2018/07/NHS-Digital-ITK3-TestHarness-UserGuidance-v1.0.pdf) on the NHS Developer Network.

Please contact [NHS Digital Solution Assurance](https://digital.nhs.uk/services/solution-assurance) for more specific queries regarding testing and assurance of your GP Connect messaging use case.


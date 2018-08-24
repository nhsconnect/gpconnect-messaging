---
title: Message receiver testing
keywords: receiver testing
tags: [testing, mesh, itk]
sidebar: overview_sidebar
permalink: testing_receiver.html
summary: "Overview of the testing approach and tools available to support and assure message receivers"
---

## Testing approach ##

GP principal clinical system suppliers wishing to validate their capability to receive and process messages received through GP Connect Messaging use cases will be provided with a "synthetic sender" solution to facilitate their development process.

This capability is currently at the design phase. However, it is envisaged that NHS Digital will provide access to a test portal where GP system providers will be able to manually trigger the sending of a test message selected from a set of exemplar messages which conform to the set of messaging use cases defined at the time.  

For example, the following steps would represent validation that a message receiver appropriately handles a particular messaging use case:
1. GP System Supplier tester logs on to NHS Digital portal, selects the GP Connect Message "Send Federated Consultation Summary" use case, and triggers sending of an exemplar message for this use case.
2. The exemplar message is sent to the MESH mailbox associated with the portal login context.
3. The GP system supplier retrieves the message from the MESH inbox, and processes the message.
4. During message processing, any requested acknowledgements are sent by the GP provider system to a test mailbox ID specified by NHSD.
5. The validation reports for the acknowledgements are emailed back to the sender (relies on an email/mailbox having been registered within the synthetic sender).
   
Note: positive and negative acknowledgement responses can be triggered, either by using specific patients, already loaded into the open test environment, or by setting the practitioner given name to a specific value. Details on these trigger responses are available on the developer network (https://developer.nhs.uk/downloads-data/itk3-test-harness-user-guidance).

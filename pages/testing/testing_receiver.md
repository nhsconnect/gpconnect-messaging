---
title: Message receiver testing
keywords: receiver testing
tags: [testing, mesh, itk]
sidebar: overview_sidebar
permalink: testing_receiver.html
summary: ""
---

## Testing approach ##

GP principal clinical system suppliers wishing to validate their capability to receive and process messages received through GP Connect Messaging use cases will be provided with a "synthetic sender" solution to facilitate their development process.

This capability is currently at the design phase. However, it is envisaged that NHS Digital will provide access to a test portal where GP system providers will be able to manually trigger the sending of a test message selected from a set of exemplar messages which conform to the set of messaging use cases defined at the time.  

For example, the following steps would represent validation that a message receiver appropriately handles a particular messaging use case:
1. GP System Supplier tester logs on to NHS Digital portal, selects the GP Connect Message "Send Federated Consultation Summary" use case, and triggers sending of an exemplar message for this use case.
2. The exemplar message is sent to the MESH mailbox associated with the portal login context.
3. The GP system supplier retrieves the message from the MESH inbox, and processes the message.
4. During message processing, any requested acknowledgements are sent by the GP provider system to a test mailbox ID specified by NHSD.
5. [TODO - Is a validation report sent back at the end of the process saying "got the correct acknowlegement etc?]
   
[TODO - how are negative and positive scenarios handled which would result in negative and positive acks? Assume the set of exemplars will include various versions for the same use case which have errors etc]
[TODO  - test data - how would a "patient matched" scenario be fulfilled? Would there be an assumption that a test patient exists in a GP test system?]
  

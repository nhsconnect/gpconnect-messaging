---
title: Send Federated Consultation Summary - Send Trigger
keywords: 
tags: [document]
sidebar: senddocument_sidebar
permalink: senddocument_fedcon_trigger.html
summary: "Options for triggering the creation of a federated consultation summary message"
---


This page provides guidance on how systems which send a federated consolation summary should initiate the message creation action.

## Guiding principles ##

The following two principles should guide the implementation choice:

1.	Write-back **MUST** take place for 100% of federated practice encounters to ensure that the registered practice care record is an accurate statement of care delivered in a primary care setting.

2.	The write-back send facility **SHOULD** be implemented in such a way as to minimise administrative burden on the federated practice.

## Recommended solution ##

The following solution is presented as the preferred option:

### Automated message creation ###

The message creation process is hidden from the clinician – in a similar way that synchronisation with Summary Care Record (SCR) takes place without the involvement of a clinician, the GP IT system is responsible for the background task of ensuring that the registered practice record is updated.

Where the encounter details at a federated practice are updated later (for example, at the end of a clinic), an additional message would result to ensure that the latest complete picture of the encounter was made available to the registered practice. Note that each additional federated encounter summary message would contain a complete encounter summary, and not simply the delta to the previous instance.

The trigger for the background process would be at or near the time when a federated practice encounter is saved.

Additional write-back could be clearly marked as such. As the GUID of the encounter is present in the ITK3 SenderReference field, all messages associated with that encounter can be identified.

As the write-back process is automated, message priority cannot be set, as this would require a review by the clinician. As a result, the message priority of all messages for this use case will be set to `routine` indicating that the federated practice is simply requesting that information about the federated practice encounter be attached to the registered practice record.

Where specific actions are required at the registered practice as a result of the encounter, the federated practice clinician will follow existing business processes.
 


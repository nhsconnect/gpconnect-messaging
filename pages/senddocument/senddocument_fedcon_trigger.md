---
title: Triggering message creation
keywords: send-document
tags: [send-document]
sidebar: senddocument_sidebar
permalink: senddocument_fedcon_trigger.html
summary: "Options for triggering the creation of a federated consultation summary message"
---


This page provides guidance on how systems which send a federated consolation summary should initiate the message creation action.

## Guiding principles ##

The following two principles should guide the implementation choice:

<table class="requirement-box">
  {% for item in site.data.senddoc_requirements.requirements %}
  {% if item.area == 'trigger' %}
  <tr>
    <td id="{{item.id}}">{{item.id}}</td>
    <td>{{item.description}}</td>
  </tr>
  {% endif %}
  {% endfor %}
</table>

## Recommended solution ##

The following solution is presented as the preferred option:

### Automated message creation ###

The message creation process is hidden from the clinician – in a similar way that synchronisation with Summary Care Record (SCR) takes place without the involvement of a clinician, the GP Principal Clinical System is responsible for the background task of ensuring that the registered practice record is updated.

Where the encounter details at a federated practice are updated later (for example, at the end of a clinic), an additional message would result to ensure that the latest complete picture of the encounter was made available to the registered practice. Note that each additional federated encounter summary message would contain a complete encounter summary, and not simply the delta to the previous instance.

The trigger for the background process would be at or near the time when a federated practice encounter is saved.

Any additional federated consultation report could be clearly marked as such. As the GUID of the encounter is present in the ITK3 SenderReference field, all messages associated with that encounter can be identified.

As the process to generate and sent a federated consultation report is automated, message priority cannot be set, as this would require a review by the clinician. As a result, the message priority of all messages for this use case will be set to `routine` indicating that the federated practice is simply requesting that information about the federated practice encounter be attached to the registered practice record.

Where specific actions are required at the registered practice as a result of the encounter, the federated practice clinician will follow existing business processes.
 
## Defining whether message should be sent ##

Irrespective of the means of triggering message creation, the first step the sending system must perform is to ascertain whether a message must be sent to the registered practice.

The message sender performs the following steps to ascertain whether a message should be sent to the registered practice:

1. if the patient registration type of the patient record at the appointment hosting practice is Regular (GMS/PMS) then no further action is required. (I.e. the registered practice care record is already up-to-date)
2. perform a PDS lookup of the patient to determine the ODS code of the registered practice of the patient
3. the system at the appointment hosting practice determines whether the registered practice is in the same federation as the hosting organisation ODS code using the local federation definition. If this check passes, the message is sent

Steps 2 and 3 are required as should the message not be destined for another practice in the federation, MESH mailbox configuration at the target practice would cause any message to be undeliverable. MESH will be [configured to allow message flow](integration_mesh.html#configurating-mesh-to-enable-message-flow) for this use case only within a federation boundary.

Additionally, in a scenario where both the sending and receiving practice are operating the same GP principal clinical system, updating the registered practice may be performed directly within that system infrastructure.

## PDF Format and business process ##

Please refer to [Send Federated Consultation Report - Business Requirements](senddocument_userstories.html) for business requirement context for the creation of the message together with details of the PDF format to be used.


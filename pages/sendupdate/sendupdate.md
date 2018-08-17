---
title: Send Update
keywords: task, 
tags: [task]
sidebar: overview_sidebar
permalink: sendupdate.html
summary: "Introduction to the Send Update capability"
---

### Send Update ###

The Send Update capability will enable an organisation to send a message to a target organisation which is intended to update the patient record at that organisation. The payload for this capability will include the ability to supply structured and coded clinical information.

{% include callout.html content="The Send Update payload will recognise that for most scenarios, messages which are intended to update target organisations' records will result in a task being created in the target system workflow. As a result, the Task resource will be used to describe the intent of the message - to request that a task be created in the target organisation to review and perform an update." type="info" %}


{% include roadmap.html content="Send Task is a roadmap item and has not been included in this version of the specification." %}
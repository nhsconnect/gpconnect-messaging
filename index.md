---
title: Introduction to GP Connect Messaging
keywords: homepage
tags: [messaging, overview, mesh, itk3]
sidebar: home_sidebar
permalink: index.html
toc: false
summary: A brief introduction to getting started with GP Connect Messaging capabilities 
---

{% include warning.html content="This site is intended primarily for those engaged with NHS Digital in First of Type activities. Other parties are advised not to develop against these specifications until a formal announcement has been made." %}

{% comment %}
[![Semver](http://img.shields.io/badge/semver-2.0.0-yellow.svg)](http://semver.org/spec/v2.0.0.html){:target="_blank" class="no_icon"} [![License](http://img.shields.io/:license-apache2-blue.svg)](http://www.apache.org/licenses/LICENSE-2.0.html){:target="_blank" class="no_icon"} 
{% endcomment %}

GP Connect aims to support better clinical care by opening up information and data held within GP principal clinical systems for use across health and social care. The GP Connect vision will be achieved by standardising integration and simplifying the operating model. Find out more on the [NHS Digital GP Connect homepage](https://digital.nhs.uk/services/gp-connect).

GP Connect has initially focused on delivering HTTP FHIR&reg; APIs. The current GP Connect FHIR API specification is found at [https://digital.nhs.uk/services/gp-connect/](https://digital.nhs.uk/services/gp-connect/gp-connect-specifications-for-developers). An additional set of capabilities, under the badge GP Connect Messaging, is described in this specification. These new capabilities are focused on enabling updates to GP practice systems. 


## Using Messaging to perform updates ##

In contrast to the synchronous FHIR&reg; API approach, which has been taken to enable read-only access to patient information, updates to patient data will be fulfilled through a *messaging* approach.

Update messages will:

- be sent using [MESH](https://digital.nhs.uk/services/message-exchange-for-social-care-and-health-mesh "MESH")
- use the [HL7 FHIR&reg; STU3](http://hl7.org/fhir/stu3/index.html) interoperability standard to define their structure
- include FHIR&reg; messaging information as defined by the [ITK3 message distribution, v2.10.0](https://developer.nhs.uk/apis/itk3messagedistribution-2-10-0/) standard


## Who will be interested in these capabilities? ##

Two main audiences will be interested in this specification:

1. message senders: NHS organisations seeking to send messages
2. message receivers: GP practices seeking to receive and process messages

This specification is primarily aimed at message senders. Where the specification contains information for message receivers, this is explicitly stated.


{% include twitterfollow.html %}

{% include gitterbadge.html %}


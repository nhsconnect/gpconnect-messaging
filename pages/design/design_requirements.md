---
title: GP Connect Messaging - Requirements
keywords: design, messaging
tags: [design,messaging]
sidebar: overview_sidebar
permalink: design_requirements.html
summary: "Details of how requirements are presented in the GP Connect Specification"
toc: false
---

## Requirements ##

Where specific mandated requirements exist in the GP Connect Messaging specification, they are presented in the following format:

<table class="requirement-box">
  <tr>
    <td><strong>ID</strong></td>
    <td>Requirement description</td>
  </tr>
</table> 

The Requirement ID provides a unique requirement identifier within this specification, as is constructed according to the following format:

`GPCM-{SD|ST|SU}-N` 

The second section, `{C|SD|ST|SU}` provides a capability identifier where `SD` refers to [Send Document](senddocument.html), `ST` refers to [Send Task](sendtask.html), `SU` refers to [Send Update](sendupdate.html). Requirements which apply to all capabilities are indicated by `C` (common)

The keywords ‘**MUST**’ and ‘**MUST NOT**’ on this site are to be interpreted as described in [RFC 2119](https://www.ietf.org/rfc/rfc2119.txt).

{% include download.html content="Spreadsheet containing full list of [requirement identifiers](downloads/GPConnectMessaging-Requirements.xlsx) found in this specification." %}
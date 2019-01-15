---
title: PDF layout
keywords: use-case, send-document, messaging
tags: [use-case, send-document, messaging]
sidebar: senddocument_sidebar
permalink: senddocument_fedcon_busreq_pdf.html
summary: "PDF layout for Send Federated Consultation Report use case"
toc: true
---

## Purpose ##

The PDF layout defines the requirements of the document layout and detailed information about data that is used to populate the document. 


## Requirements ##

Requirements are given below which define how the PDF is populated for this use case:

<table class="requirement-box">
  {% for item in site.data.senddoc_requirements.requirements %}
  {% if item.area == 'pdf' %}
  <tr>
    <td id="{{item.id}}">{{item.id}}</td>
    <td>{{item.description}}</td>
  </tr>
  {% endif %}
  {% endfor %}
</table>


## Layout ##

The PDF below defines the expected document layout, to download click the download icon:

<embed src="pages/senddocument/GP Connect Messaging - PDF Layout.pdf" width="847px" height="2200px" />


## Field descriptions ##

The following describe each of the fields used in the PDF:

|	Field name 	|	Description	|	
|	-------------	|	-------------	|
|	`Version [x]` &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;	|	The version of the consultation report sent. The first time it is sent, the report will display "Version 1". If a clinician re-opens and edits and a second version is sent, the PDF will display "Version 2".	|
|	`Number of related documents`	|	The number of documents attached to the message eg: pain point diagram, ECG, photo. These will be all documents recorded on the GP system that are linked to the consultation	|
|	`Page [x] of [y]`	|	The page number and total pages of the PDF	|
|	`Surname, Forename(s)`	|	The surname and forename(s) of the patient. This may wrap over multiple lines depending on the length of the name	|
|	`D.O.B.`	|	The date of birth of the patient in the format `dd-Mmm-yyyy	`|
|	`NHS no.`	|	The NHS number of the patient in the format `### ### ####`	|
|	`Gender`	|	The gender of the patient	|
|	`Tel No.`	|	The patient's contact telephone number(s)	|
|	`Address`	|	The current address of the patient, presented line by line, including post code. This may wrap over multiple lines depending on the length of the address	|
|	`Clinical Notes`	|	All data entered by the clinician at the federated practice into the 'Clinical notes [notes]' section of the PDF document. This includes all free text, clinical/SNOMED CT codes, dm+d codes and any other data entered relating to the consultation. This data must be displayed in a format that matches how the consultation is displayed on screen or when printed.	|
|	`Date seen`	|	The date and time of the patient's appointment at the federated GP practice in the format `dd-Mmm-yyyy`	|
|	`Date consultation sent`	|	The date and time the consultation report was sent by the federated practice in the format `dd-Mmm-yyyy  hh:mm`	|
|	`Clinician`	|	The full name and role of the treating clinician for the consultation	|
|	`Surgery Tel No.`	|	The main telephone number of the federated practice available for other GP practices in the federation	|
|	`Surgery email`	|	The main email address of the federated practice	|
|	`Place of consultation`	|	The name of the federated practice and the town specified in its full address	|



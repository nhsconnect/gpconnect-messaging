---
title: PDF layout
keywords: use-case, send-document, messaging
tags: [use-case, send-document, messaging]
sidebar: senddocument_sidebar
permalink: senddocument_fedcon_busreq_pdf.html
summary: "PDF layout for Send Consultation Report use case"
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

The PDF below defines the expected document layout, if your browser is not compatible to display the PDF please right click and select "Save as" to download, or use this [link](GP_Connect_Messaging_-_PDF_Layout.pdf):

<object
  data="pages/senddocument/GP_Connect_Messaging_-_PDF_Layout.pdf"
  type="application/pdf"
  width="847"
  height="2200">
</object>

<object data="pages/senddocument/GP_Connect_Messaging_-_PDF_Layout.pdf" type="application/pdf" width="847" height="0">      
</object>



## Field descriptions ##

The following describe each of the fields used in the PDF:

|	Field name  	|	Description 	|	Confidential item  |
|	-------------	|	-------------	| :----------------: |
|	`Version [x]` |	The version of the consultation report sent	|
|	`Number of related documents`	|	The number of documents attached to the message eg: pain point diagram, ECG, photo. These will be all documents recorded on the GP system that are linked to the consultation	|
|	`Page [x] of [y]`	|	The page number and total pages of the PDF	|
|	`Surname, Forename(s)`	|	The surname and forename(s) of the patient. This may wrap over multiple lines depending on the length of the name	|
|	`D.O.B.`	|	The date of birth of the patient in the format `dd-Mmm-yyyy	`|
|	`NHS no.`	|	The NHS number of the patient in the format `### ### ####`	|
|	`Gender`	|	The gender of the patient	|
|	`Tel No.`	|	The patient's contact telephone number(s)	|
|	`Current Tel No.`	|	If the patient is currently staying at a temporary location, the number(s) for contacting the patient at that location. If the patient is not at a temporary location this will be blank and the 'Current Tel No.' label will not be shown.	|
|	`Registered Address`	|	The registered address of the patient, presented line by line, including post code. This may wrap over multiple lines depending on the length of the address.	|
|	`Current Address`	|	If the patient is currently staying at a temporary location, the address of that location. If the patient is not at a temporary location this will be blank and the 'Current Address' label will not be shown.	|
|	`Clinical Notes`	|	All data entered by the clinician at the practice into the 'Clinical notes [notes]' section of the PDF document. Where the consultation has been set to confidential the data from the consultation is not displayed. It is replaced by the text 'The details of this consultation have been set as confidential'. | x |
|	`Date seen`	|	The date and time of the patient's appointment at the GP practice in the format `dd-Mmm-yyyy`	|
|	`Date consultation sent`	|	The date and time the consultation report was sent by the practice in the format `dd-Mmm-yyyy  hh:mm`	|
|	`Clinician`	|	The full name and role of the treating clinician for the consultation. Where the consultation has been set to confidential the data from the consultation is not displayed.	| x |
|	`Surgery Tel No.`	|	The main telephone number of the practice available for other GP practices. Where the consultation has been set to confidential the data from the consultation is not displayed.	| x |
|	`Surgery email`	|	The main email address of the practice. Where the consultation has been set to confidential the data from the consultation is not displayed.	| x |
|	`Place of consultation`	|	The name of the practice and the town specified in its full address. Where the consultation has been set to confidential the data from the consultation is not displayed.	| x |



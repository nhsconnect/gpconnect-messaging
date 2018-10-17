---
title: Send Document - User stories
keywords: 
tags: [messaging]
sidebar: senddocument_sidebar
permalink: senddocument_userstories.html
summary: "Mock-up for user stories"
---

Business requirements that apply across all of GP Connect Send Document


## Send report for correct patient ##

<div>
<table class='resource-attributes'>
  <tr>
    <td><b>ID:</b><code>GPC-SD01</code></td>
    <td><b>Source:</b> <a href="sendmessage_process.html" target="_blank">Process 4.1</a></td>
  </tr>
</table>

<div class="bs-callout bs-callout-primary">
	<div>	
		<p><b>Description</b></p>
		<p style="margin-left: 30px"><i>As a clinician at the federated practice...</i></p>
		<p style="margin-left: 30px"><i>I want to send a document containing a patient’s consultation notes when the patient is registered at another practice within my GP federation...</i></p>
		<p style="margin-left: 30px"><i>so that the patient’s medical record is kept up to date with a full treatment history.</i></p>
		<br/>
	</div>

	<div>	
		<p><b>Acceptance criteria - provider</b></p>
		<p>
			<ol type="1">
				<li>The provider system must send a federated consultation report when the patient in question is registered at another GP practice within the federation (or group of GP practices working together to deliver a service).</li>
				<li>The provider system must follow the following method of determining whether a patient is registered at another GP practice within the same federation:
					<ol type="i">
						<li>Check the patient registration type. If the patient registration type of the patient record at the appointment hosting practice is Regular (GMS/PMS) then no further action is required.</li>
						<li>If the patient does not have a Regular (GMS/PMS) registration then, perform a PDS lookup of the patient to determine the ODS code of the registered practice of the patient.</li>
						<li>Determine whether the registered practice is in the same federation (or group of GP practices) as the hosting organisation ODS code using the local federation definition. This is consistent with the federation discoverability architectural foundations for the GP Connect Appointment Management capability as set out at https://nhsconnect.github.io/gpconnect/appointments_design.html#responsibilities-in-a-federated-booking-context.</li>
					</ol>
				</li>
				<li>If the provider system determines the registered practice is outside the GP federation (or group of GP practices), no federated consultation report is sent and usual business processes should be followed.</li>
			</ol>
		</p>
		<br/>
		<p><b>Acceptance criteria - consumer</b></p>
		<p>
			N/A
		</p>
		<br/>
	</div>

	<div>	
		<p><b>Notes</b></p>
		<p>Checking whether the registered practice is within the same federation (or group of GP practices) is required. If the message is destined for another practice outside the federation, the MESH mailbox configuration at the target practice would cause any message to be undeliverable. MESH will be configured to allow message flow only within a federation boundary for this use case.</p>
		<br/>
		<p><b>Related requirements</b></p>
		<p>
			None
		</p>
	</div>	

</div>
</div>




## Routing the report to the correct practice ##

<div>
<table class='resource-attributes'>
  <tr>
    <td><b>ID:</b><code>GPC-SD02</code></td>
    <td><b>Source:</b> <a href="sendmessage_process.html" target="_blank">Process 4.1</a></td>
  </tr>
</table>

<div class="bs-callout bs-callout-primary">
	<div>	
		<p><b>Description</b></p>
		<p style="margin-left: 30px"><i>As a clinician...</i></p>
		<p style="margin-left: 30px"><i>I want to send a document containing a patient’s consultation notes  when the patient is registered at another practice within my GP federation...</i></p>
		<p style="margin-left: 30px"><i>so that the patient’s medical record is kept up to date with a full treatment history.</i></p>
		<br/>
	</div>

	<div>	
		<p><b>Acceptance criteria - provider</b></p>
		<p>
			<ol type="1">
				<li>All federated consultation reports will use MESH automated message routing in order to ensure that the message is routed correctly to the registered practice of the patient. It is not necessary for the provider system to specify a destination MESH mailbox ID.</li>
				<li>The provider system must specify the patient’s NHS Number, Surname and Date of Birth in the message header and use these to populate the Mex-To HTTP header in the MESH endpoint lookup service.</li>
				<li>The provider system must be set up so that it allows the flow of MESH messages to all consumer systems within their GP federation (or group of GP practices).</li>
				<li>The provider system must be allocated a MESH Workflow ID to be associated solely with the GP Connect Send Document capability.</li>
			</ol>
		</p>
		<br/>
		<p><b>Acceptance criteria - consumer</b></p>
		<p>
			<ol type="1">
				<li>Where the message received is for a patient who is not registered at the GP practice, the consumer system must send an error message back to the sending GP practice.</li>
				<li>The consumer system must be set up so that it allows the flow of MESH messages from all provider systems within their GP federation (or group of GP practices).</li>
				<li>The consumer system must be allocated a MESH Workflow ID to be associated solely with the GP Connect Send Document capability.</li>
			</ol>
		</p>
		<br/>
	</div>

	<div>	
		<p><b>Notes</b></p>
		<p>
			None
		</p>
		<br/>
		<p><b>Related requirements</b></p>
		<p>
			None
		</p>
	</div>	

</div>
</div>



## Routing the report to the correct practice ##

<div>
<table class='resource-attributes'>
  <tr>
    <td><b>ID:</b><code>GPC-SD02</code></td>
    <td><b>Source:</b> <a href="sendmessage_process.html" target="_blank">Process 4.1</a></td>
  </tr>
</table>

<div class="bs-callout bs-callout-primary">
	<div>	
		<p><b>Description</b></p>
		<p style="margin-left: 30px"><i>As a clinician...</i></p>
		<p style="margin-left: 30px"><i>I want to send a document containing a patient’s consultation notes  when the patient is registered at another practice within my GP federation...</i></p>
		<p style="margin-left: 30px"><i>so that the patient’s medical record is kept up to date with a full treatment history.</i></p>
		<br/>
	</div>

	<div>	
		<p><b>Acceptance criteria - provider</b></p>
		<p>
			<ol type="1">
				<li>All federated consultation reports will use MESH automated message routing in order to ensure that the message is routed correctly to the registered practice of the patient. It is not necessary for the provider system to specify a destination MESH mailbox ID.</li>
				<li>The provider system must specify the patient’s NHS Number, Surname and Date of Birth in the message header and use these to populate the Mex-To HTTP header in the MESH endpoint lookup service.</li>
				<li>The provider system must be set up so that it allows the flow of MESH messages to all consumer systems within their GP federation (or group of GP practices).</li>
				<li>The provider system must be allocated a MESH Workflow ID to be associated solely with the GP Connect Send Document capability.</li>
			</ol>
		</p>
		<br/>
		<p><b>Acceptance criteria - consumer</b></p>
		<p>
			<ol type="1">
				<li>Where the message received is for a patient who is not registered at the GP practice, the consumer system must send an error message back to the sending GP practice.</li>
				<li>The consumer system must be set up so that it allows the flow of MESH messages from all provider systems within their GP federation (or group of GP practices).</li>
				<li>The consumer system must be allocated a MESH Workflow ID to be associated solely with the GP Connect Send Document capability.</li>
			</ol>
		</p>
		<br/>
	</div>

	<div>	
		<p><b>Notes</b></p>
		<p>
			None
		</p>
		<br/>
		<p><b>Related requirements</b></p>
		<p>
			None
		</p>
	</div>	

</div>
</div>
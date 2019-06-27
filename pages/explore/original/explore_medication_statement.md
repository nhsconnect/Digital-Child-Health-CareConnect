---
title: Medication Statement Event Message Bundle
keywords:  messaging, bundles
tags: [fhir,messaging]
sidebar: foundations_sidebar
permalink: explore_medication_statement.html
summary: "The FHIR profiles used for the Medication Statement Event Message Bundle"
---

The following FHIR profiles are used to form the Medication Statement Event Message Bundle:

- [DCH-Bundle-1](https://fhir.nhs.uk/STU3/StructureDefinition/DCH-Bundle-1)
- [DCH-MessageHeader-1](https://fhir.nhs.uk/STU3/StructureDefinition/DCH-MessageHeader-1) - where the coding and display elements for the 'event' type are fixed to 'CH019 - Medication Statement'
- [CareConnect-Organization-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Organization-1)
- [DCH-HealthcareService-1](https://fhir.nhs.uk/STU3/StructureDefinition/DCH-HealthcareService-1)
- [CareConnect-DCH-Patient-1](https://fhir.nhs.uk/STU3/StructureDefinition/CareConnect-DCH-Patient-1)
- [CareConnect-DCH-Encounter-1](https://fhir.nhs.uk/STU3/StructureDefinition/CareConnect-DCH-Encounter-1)
- [CareConnect-Location-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Location-1)
- [CareConnect-DCH-Practitioner-1](https://fhir.nhs.uk/STU3/StructureDefinition/CareConnect-DCH-Practitioner-1)
- [CareConnect-DCH-PractitionerRole-1](https://fhir.nhs.uk/STU3/StructureDefinition/CareConnect-DCH-PractitionerRole-1)
- [CareConnect-DCH-Medication-1](https://fhir.nhs.uk/STU3/StructureDefinition/CareConnect-DCH-Medication-1)
- [CareConnect-DCH-MedicationStatement-1](https://fhir.nhs.uk/STU3/StructureDefinition/CareConnect-DCH-MedicationStatement-1) 
- [CareConnect-ITK-Medication-List-1](https://fhir.nhs.uk/STU3/StructureDefinition/CareConnect-ITK-Medication-List-1)

### Medication Statement data item mapping to FHIR profiles ###
The Medication Statement follows the same pattern as Medication Statement in Transfer of Care. As such there are 2 distinct lists - one for the active medications, and one for the discontinued medications. Following the Transfer of Care pattern, each list uses a FHIR List resource.

The Mapping tables shown below defines the FHIR elements that SHALL be used to encode the Healthy Child Event Specification data items for each DCH Event Message payload.  Some common data item mappings, such as patient, publisher or Date/Time of event information, are defined within the [Header mapping table](explore_event_header_design.html) and SHALL be considered in parallel with the payload mapping.

#### Medication Statement for Active Medications ####
Active medications uses a List resource to bound all the active medications. Active medications include those that the patient is known to be actively taking. Active medications include medications that have been changed within this episode of care. Changed medication details appear in the MedicationChangeSummary extension of the MedicationStatement resource.

The Child Health Event data items are fulfilled by elements within the FHIR resources listed below:

**Medication Statement List (Active Medications)**

Note that CareConnect-ITK-Medication-List-1.entry.flag & CareConnect-ITK-Medication-List-1.entry.emptyReason must not be used.

<table>
<tr><th>DCH Data Item</th><th>FHIR Resource element</th><th>Mandatory/<br/>Required/<br/>Optional</th><th>Notes</th></tr>
<tr><td>List.code</td><td>CareConnect-ITK-Medication-List-1.code</td><td>Mandatory</td><td>Fixed value code="1102411000000102" display="Active medications" system="http://snomed.info/sct"</td></tr>
<tr><td>List.status</td><td>CareConnect-ITK-Medication-List-1.status</td><td>Mandatory</td><td>Fixed value="current"</td></tr>
<tr><td>List.mode</td><td>CareConnect-ITK-Medication-List-1.mode</td><td>Mandatory</td><td>Fixed value="snapshot"</td></tr>
<tr><td>List.title</td><td>CareConnect-ITK-Medication-List-1.title</td><td>Mandatory</td><td>Fixed value="Medication Active List"</td></tr>
<tr><td>List.subject</td><td>CareConnect-ITK-Medication-List-1.subject</td><td>Mandatory</td><td></td></tr>
<tr><td>List.encounter</td><td>CareConnect-ITK-Medication-List-1.encounter</td><td>Mandatory</td><td></td></tr>
<tr><td>List.date</td><td>CareConnect-ITK-Medication-List-1.date</td><td>Mandatory</td><td>The date the List was created</td></tr>
<tr><td>List.source</td><td>CareConnect-ITK-Medication-List-1.source</td><td>Mandatory</td><td>The practitioner who created the List</td></tr>
<tr><td>List.entry.item</td><td>CareConnect-ITK-Medication-List-1.entry.item</td><td>Mandatory</td><td>Link to the active MedicationStatement</td></tr>
</table>

**Medication Statement (Active Medications)**

<table>
<tr><th>DCH Data Item</th><th>FHIR Resource element</th><th>Mandatory/<br/>Required/<br/>Optional</th><th>Notes</th></tr>
<tr><td>Date/Time</td><td>CareConnect-DCH-MedicationStatement-1.effectivePeriod.start</td><td>Mandatory</td><td></td></tr>
<tr><td>Medication Name</td><td>CareConnect-DCH-Medication-1.code</td><td>Required</td><td>Where medication code is not known, the name of the medication should be sent as text in Medication.code.text</td></tr>
<tr><td>Form</td><td>CareConnect-DCH-Medication-1.form</td><td>Optional</td><td></td></tr>
<tr><td>Route</td><td>CareConnect-DCH-MedicationStatement-1.dosage.route</td><td>Optional</td><td></td></tr>
<tr><td>Site</td><td>CareConnect-DCH-MedicationStatement-1.dosage.site</td><td>Optional</td><td></td></tr>
<tr><td>Method</td><td>CareConnect-DCH-MedicationStatement-1.dosage.method</td><td>Optional</td><td></td></tr>
<tr><td>Dose directions description</td><td>CareConnect-DCH-MedicationStatement-1.dosage.text</td><td>Optional</td><td></td></tr>
<tr><td>Dose amount description</td><td>CareConnect-DCH-MedicationStatement-1.dosage.text</td><td>Optional</td><td>Dose amount should be concatenated with the dose description text</td></tr>
<tr><td>Dose timing description</td><td>CareConnect-DCH-MedicationStatement-1.dosage.text</td><td>Optional</td><td>Dose timing should be concatenated with the dose description text</td></tr>
<tr><td>Structured dose direction cluster</td><td>CareConnect-DCH-MedicationStatement-1.dosage.additionalInstruction</td><td>Optional</td><td>MedicationStatement.additionalInstruction to be used as a string element for "Continue Indefinitely"; "Do not discontinue" and "Stop when course complete".</td></tr>
<tr><td>Dose direction duration</td><td>CareConnect-DCH-MedicationStatement-1.dosage.additionalInstruction</td><td>Optional</td><td>Structured duration instructions may use the FHIR element MedicationStatement.effective[x].effectivePeriod otherwise FHIR element MedicationStatement.note as a degrade to text.</td></tr>
<tr><td>Additional instruction</td><td>CareConnect-DCH-MedicationStatement-1.note</td><td>Optional</td><td></td></tr>
</table>

**Medication Statement for Changed Medications**

If a medication is changed, the changeSummary extension for the [new] medication should be completed as follows:

<table>
<tr><th>DCH Data Item</th><th>FHIR Resource element</th><th>Mandatory/<br/>Required/<br/>Optional</th><th>Notes</th></tr>
<tr><td>status</td><td>CareConnect-DCH-MedicationStatement-1.Extension-CareConnect-MedicationChangeSummary-1.status</td><td>Optional</td><td></td></tr>
<tr><td>Indication</td><td>CareConnect-DCH-MedicationStatement-1.Extension-CareConnect-MedicationChangeSummary-1.indication</td><td>Optional</td><td></td></tr>
<tr><td>Date of Change</td><td>CareConnect-DCH-MedicationStatement-1.Extension-CareConnect-MedicationChangeSummary-1.dateChanged</td><td>Optional</td><td></td></tr>
<tr><td>Description of Amendment</td><td>CareConnect-DCH-MedicationStatement-1.Extension-CareConnect-MedicationChangeSummary-1.detailsOfAmendment</td><td>Optional</td><td></td></tr>
</table>

#### Medication Statement for Medical Devices (not coded in dm+d) ####

Some medical devices, trial drugs, non-UK sourced drugs etc. are not coded in dm+d. In these cases, the same pattern as for Medication Statement (Active Medications) should be following, using Medication.code.text, rather than Medication.code.
<table>
<tr><th>DCH Data Item</th><th>FHIR Resource element</th><th>Mandatory/<br/>Required/<br/>Optional</th><th>Notes</th></tr>
<tr><td>Medication Device Entry (not in dm+d)</td><td>CareConnect-DCH-Medication-1.code.text</td><td>Optional</td><td>Medication and medical devices not in dm+d should use Medication.code.text, and follow the same pattern as Medication Statement (Active Medications)</td></tr>
</table>

#### Medication Statement for Discontinued Medications ####

Discontinued medications uses a List resource to bound all the discontinued medications. Discontinued medications include those that have been stopped during this episode of care.

The Child Health Event data items are fulfilled by elements within the FHIR resources listed below:

**Medication Statement List (Discontinued Medications)**

Note that CareConnect-ITK-Medication-List-1.entry.flag & CareConnect-ITK-Medication-List-1.entry.emptyReason must not be used.

<table>
<tr><th>DCH Data Item</th><th>FHIR Resource element</th><th>Mandatory/<br/>Required/<br/>Optional</th><th>Notes</th></tr>
<tr><td>List.code</td><td>CareConnect-ITK-Medication-List-1.code</td><td>Mandatory</td><td>Fixed value code="1102191000000100" display="Discontinued medications" system="http://snomed.info/sct"</td></tr>
<tr><td>List.status</td><td>CareConnect-ITK-Medication-List-1.status</td><td>Mandatory</td><td>Fixed value="current"</td></tr>
<tr><td>List.mode</td><td>CareConnect-ITK-Medication-List-1.mode</td><td>Mandatory</td><td>Fixed value="snapshot"</td></tr>
<tr><td>List.title</td><td>CareConnect-ITK-Medication-List-1.title</td><td>Mandatory</td><td>Fixed value="Medication Discontinued List"</td></tr>
<tr><td>List.subject</td><td>CareConnect-ITK-Medication-List-1.subject</td><td>Mandatory</td><td></td></tr>
<tr><td>List.encounter</td><td>CareConnect-ITK-Medication-List-1.encounter</td><td>Mandatory</td><td></td></tr>
<tr><td>List.date</td><td>CareConnect-ITK-Medication-List-1.date</td><td>Mandatory</td><td>The date the List was created</td></tr>
<tr><td>List.source</td><td>CareConnect-ITK-Medication-List-1.source</td><td>Mandatory</td><td>The practitioner who created the List</td></tr>
<tr><td>List.entry.item</td><td>CareConnect-ITK-Medication-List-1.entry.item</td><td>Mandatory</td><td>Link to the discontinued MedicationStatement</td></tr>
</table>

**Medication Statement (Discontinued Medications)**

<table>
<tr><th>DCH Data Item</th><th>FHIR Resource element</th><th>Mandatory/<br/>Required/<br/>Optional</th><th>Notes</th></tr>
<tr><td>Name of discontinued medication</td><td>CareConnect-DCH-Medication-1.code</td><td>Required</td><td>Where medication code is not known, the name of the medication should be sent as text in Medication.code.text</td></tr>
<tr><td>Status</td><td>CareConnect-DCH-MedicationStatement-1.status</td><td>Mandatory</td><td>Fixed value="stopped"</td></tr>
<tr><td>Indication</td><td>CareConnect-DCH-MedicationStatement-1.reasonCode.text</td><td>Optional</td><td></td></tr>
<tr><td>Date of latest change</td><td>CareConnect-DCH-MedicationStatement-1.effectiveDateTime</td><td>Optional</td><td></td></tr>
<tr><td>Description of amendment</td><td>CareConnect-DCH-MedicationStatement-1.note</td><td>Optional</td><td></td></tr>
<tr><td>Comment</td><td>CareConnect-DCH-MedicationStatement-1.note</td><td>Optional</td><td></td></tr>
</table>

### Reference Linkage Diagram ###

This Linkage diagram defines the required references that SHALL be made between resources within the DCH Event Message bundle. It includes both Header and Payload resources (but omits the DCH-Bundle-1 wrapper).

<img src="images/explore/MedicationStatement.png">

### Medication Statement Event Bundle XML Example ###

<script src="https://gist.github.com/IOPS-DEV/f73b0374f63b7971bf36655f5ca7f868.js"></script>

### Medication Statement Event Bundle JSON Example ###

<script src="https://gist.github.com/IOPS-DEV/044b54a4953b9beed7071b6eb023f7a4.js"></script>
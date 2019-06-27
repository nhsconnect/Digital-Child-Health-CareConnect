---
title: Emergency Care Attendance Event Message Bundle
keywords:  messaging, bundles
tags: [fhir,messaging]
sidebar: foundations_sidebar
permalink: explore_emergency_care_attendance.html
summary: "The FHIR profiles used for the Emergency Care Attendance Event Message Bundle"
---

The following FHIR profiles are used to form the Emergency Care Attendance Event Message Bundle:

- [DCH-Bundle-1](https://fhir.nhs.uk/STU3/StructureDefinition/DCH-Bundle-1)
- [DCH-MessageHeader-1](https://fhir.nhs.uk/STU3/StructureDefinition/DCH-MessageHeader-1) - where the coding and display for the event element is fixed to 'CH011 - Emergency Care Attendance'
- [CareConnect-Organization-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Organization-1)
- [DCH-HealthcareService-1](https://fhir.nhs.uk/STU3/StructureDefinition/DCH-HealthcareService-1)
- [CareConnect-DCH-Patient-1](https://fhir.nhs.uk/STU3/StructureDefinition/CareConnect-DCH-Patient-1)
- [CareConnect-DCH-Emergency-Encounter-1](https://fhir.nhs.uk/STU3/StructureDefinition/CareConnect-DCH-Emergency-Encounter-1)
- [CareConnect-Location-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Location-1)
- [CareConnect-DCH-EmergencyCare-Procedure-1](https://fhir.nhs.uk/STU3/StructureDefinition/CareConnect-DCH-EmergencyCare-Procedure-1)
- [DCH-RelatedPerson-1](https://fhir.nhs.uk/STU3/StructureDefinition/DCH-RelatedPerson-1)
- [DCH-ProfessionalComment-Communication-1](https://fhir.nhs.uk/STU3/StructureDefinition/DCH-ProfessionalComment-Communication-1)

### Emergency Care Attendance Event data item mapping to FHIR profiles ###

The Child Health Event data items are fulfilled by elements within the FHIR resources listed below:

<table>
<tr>
<th>DCH Data Item</th><th>FHIR resource element</th><th>Mandatory/<br/>Required/<br/>Optional</th><th>Note</th>
</tr>
<tr>
<td>Date and Time of attendance</td><td>CareConnect-DCH-Emergency-Encounter-1.period.start</td><td>Mandatory</td><td></td>
</tr>
<tr>
<td>Date and Time of discharge</td><td>CareConnect-DCH-Emergency-Encounter-1.period.end</td><td>Required</td><td></td>
</tr>
<tr>
<td>ODS/ORD Site Code</td><td>CareConnect-Location-1.identifier (ODS Site Code)</td><td>Required</td><td></td>
</tr>
<tr>
<td>Accompanied by (Name)</td><td>DCH-RelatedPerson-1.name</td><td>Required</td><td></td>
</tr>
<tr>
<td>Accompanied by (Relationship)</td><td>DCH-RelatedPerson-1.relationship</td><td>Required</td><td>"For Emergency Care Attendance, the relationship code must come from the valueSet provided)"</td>
</tr>
<tr>
<td>Attendance Source</td><td>CareConnect-DCH-Emergency-Encounter-1.hospitalization.admitSource</td><td>Required</td><td></td>
</tr>
<tr>
<td>Presenting Complaint</td><td>CareConnect-DCH-Emergency-Encounter-1.reason</td><td>Mandatory</td><td></td>
</tr>
<tr>
<td>Procedure</td><td>CareConnect-DCH-EmergencyCare-Procedure-1.code</td><td>Required</td><td></td>
</tr>
<tr>
<td>Discharge destination</td><td>CareConnect-DCH-Emergency-Encounter-1.hospitalization.dischargeDisposition</td><td>Mandatory</td><td></td>
</tr>
<tr>
<td>Discharge status</td><td>CareConnect-DCH-Emergency-Encounter-1.emergencyDischargeStatus</td><td>Mandatory</td><td></td>
</tr>
<tr>
<td>Clinical Narrative</td><td>DCH-ProfessionalComment-Communication-1</td><td>Optional</td><td></td>
</tr>
</table>



### Linkage Diagram ###

<img src="images/explore/EmergencyCareAttendanceEvent.png">

### Emergency Care Attendance Event XML Example ###

<script src="https://gist.github.com/IOPS-DEV/da57b30b053b500f49e62a0af8b6bf3f.js"></script>

### Emergency Care Attendance Event JSON Example ###

<script src="https://gist.github.com/IOPS-DEV/0575b51eb7c66b39c33d66e9d6f46abc.js"></script>
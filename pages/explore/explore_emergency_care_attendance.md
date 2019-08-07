---
title: Emergency Care Attendance Event Message Bundle
keywords:  messaging, bundles
tags: [fhir,messaging]
sidebar: foundations_sidebar
permalink: explore_emergency_care_attendance.html
summary: "The FHIR profiles used for the Emergency Care Attendance Event Message Bundle"
---

## FHIR Profiles ##

The following FHIR profiles are used to form the Emergency Care Attendance Event Message Bundle:

- [Bundle](http://hl7.org/fhir/STU3/StructureDefinition/Bundle)
- [Event-MessageHeader-1](https://fhir.nhs.uk/STU3/StructureDefinition/Event-MessageHeader-1) - where the coding and display for the event element is fixed to ‘emergency-care-attendance-1 \| Emergency Care Attendance’
- [CareConnect-Organization-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Organization-1)
- [CareConnect-HealthcareService-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-HealthcareService-1)
- [CareConnect-Patient-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Patient-1)
- [CareConnect-Encounter-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Encounter-1)
- [CareConnect-Location-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Location-1)
- [CareConnect-Procedure-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Procedure-1)
- [CareConnect-RelatedPerson-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-RelatedPerson-1)
- [CareConnect-Communication-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Communication-1)

## Bundle Structure

Specifies referencing within the Event Message Bundle.


<div style="text-align:center; margin-bottom:20px" >
	<a href="images/explore/dch-emergencycareattendance.png" target="_blank"><img src="images/explore/dch-emergencycareattendance.png"></a><br/>
	Emergency Care Attendance <a href="images/explore/dch-emergencycareattendance.png" target="_blank">(open in new TAB)</a>
</div>

## Emergency Care Attendance Event data item mapping to FHIR profiles ##

This Mapping table defines the FHIR elements that SHALL be used to encode the Healthy Child Event Specification data items for each DCH Event Message payload.  
Some common data item mappings, such as patient, publisher or Date/Time of event information, are defined within the [Header mapping table](explore_event_header_design.html) and SHALL be considered in parallel with the payload mapping.

The Child Health Event data items are fulfilled by elements within the FHIR resources listed below:


<table>
<tr>
<th>DCH Data Item</th><th>FHIR resource element</th><th>Mandatory/<br/>Required/<br/>Optional</th><th>Note</th>
</tr>
<tr>
<td>Date and Time of attendance</td><td>CareConnect-Encounter-1.period.start</td><td>Mandatory</td><td></td>
</tr>
<tr>
<td>Date and Time of discharge</td><td>CareConnect-Encounter-1.period.end</td><td>Required</td><td></td>
</tr>
<tr>
<td>ODS/ORD Site Code</td><td>CareConnect-Location-1.identifier (ODS Site Code)</td><td>Required</td><td></td>
</tr>
<tr>
<td>Accompanied by (Name)</td><td>CareConnect-RelatedPerson-1.name</td><td>Required</td><td></td>
</tr>
<tr>
<td>Accompanied by (Relationship)</td><td>CareConnect-RelatedPerson-1.relationship</td><td>Required</td><td>"For Emergency Care Attendance, the relationship code must come from the valueSet provided)"</td>
</tr>
<tr>
<td>Attendance Source</td><td>CareConnect-Encounter-1.hospitalization.admitSource</td><td>Required</td><td></td>
</tr>
<tr>
<td>Presenting Complaint</td><td>CareConnect-Encounter-1.reason</td><td>Mandatory</td><td></td>
</tr>
<tr>
<td>Procedure</td><td>CareConnect-Procedure-1.code</td><td>Required</td><td></td>
</tr>
<tr>
<td>Discharge destination</td><td>CareConnect-Encounter-1.hospitalization.dischargeDisposition</td><td>Mandatory</td><td></td>
</tr>
<tr>
<td>Discharge status</td><td>CareConnect-Encounter-1.emergencyDischargeStatus</td><td>Mandatory</td><td></td>
</tr>
<tr>
<td>Clinical Narrative</td><td>CareConnect-Communication-1</td><td>Optional</td><td></td>
</tr>
</table>

## Resource Population Requirements and Guidance ##

The following requirements and resource population guidance should be followed in addition to the requirements and guidance outlined in the data item mapping above and in the [Event Header](https://developer.nhs.uk/apis/ems-beta/explore_event_header_information.html) requirements page.

#### _list profiles used (and sustituted L3 variants)_ ####

## Emergency Care Attendance Example ##

#### _placeholder using additional demographics_ ####

<script src="https://gist.github.com/IOPS-DEV/646f784bcb1db6e7aa3d924aaaf423d1.js"></script>


## Profile Change Mappings for Emergency Care Attendance ##

Profiles used in [Demographics Update Event Messages 1.2.1-Release Candidate](https://developer.nhs.uk/apis/demographicupdates-120-rc/index.html) are replaced with:

| Demographic-Event-Messages | Demographic-Event-Messages-CareConnect |
|----------------------------|----------------------------------------|
| DCH-Bundle-1 | Bundle |
| DCH-MessageHeader-1 | Event-MessageHeader-1 |
| CareConnect-Organization-1 | CareConnect-Organization-1 |
| DCH-HealthcareService-1 | CareConnect-HealthcareService-1 |
| CareConnect-DCH-Patient-1 | CareConnect-Patient-1 |
| CareConnect-DCH-Emergency-Encounter-1 | CareConnect-Encounter-1 |
| CareConnect-Location-1 | CareConnect-Location-1 |
| CareConnect-DCH-EmergencyCare-Procedure-1 | CareConnect-Procedure-1 |
| DCH-RelatedPerson-1 | CareConnect-RelatedPerson-1 |
| DCH-ProfessionalComment-Communication-1 | CareConnect-Communication-1 |

<hr/>
<hr/>

## Old Stuff ##

#### retain until new content completed then remove ####



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
---
title: Professional Summary Event Message Bundle
keywords:  messaging, bundles
tags: [fhir,messaging]
sidebar: foundations_sidebar
permalink: explore_professional_summary.html
summary: "The FHIR profiles used for the Professional Summary Event Message Bundle"
---

The following FHIR profiles are used to form the Professional Summary Event Message Bundle:

- [DCH-Bundle-1](https://fhir.nhs.uk/STU3/StructureDefinition/DCH-Bundle-1)
- [DCH-MessageHeader-1](https://fhir.nhs.uk/STU3/StructureDefinition/DCH-MessageHeader-1) - where the coding and display elements for the event type are fixed to 'CH026 - Professional Summary'
- [CareConnect-Organization-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Organization-1)
- [DCH-HealthcareService-1](https://fhir.nhs.uk/STU3/StructureDefinition/DCH-HealthcareService-1)
- [CareConnect-DCH-Patient-1](https://fhir.nhs.uk/STU3/StructureDefinition/CareConnect-DCH-Patient-1)
- [CareConnect-DCH-Encounter-1](https://fhir.nhs.uk/STU3/StructureDefinition/CareConnect-DCH-Encounter-1)
- [CareConnect-Location-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Location-1)
- [CareConnect-DCH-Practitioner-1](https://fhir.nhs.uk/STU3/StructureDefinition/CareConnect-DCH-Practitioner-1)
- [CareConnect-DCH-PractitionerRole-1](https://fhir.nhs.uk/STU3/StructureDefinition/CareConnect-DCH-PractitionerRole-1)
- [DCH-ProfessionalComment-Communication-1](https://fhir.nhs.uk/STU3/StructureDefinition/DCH-ProfessionalComment-Communication-1)
- [DCH-RelatedPerson-1](https://fhir.nhs.uk/STU3/StructureDefinition/DCH-RelatedPerson-1)


### Professional Summary Event data item mapping to FHIR profiles ###

The Child Health Event data items are fulfilled by elements within the FHIR resources listed below:

<table>
<tr>
<th>DCH Data Item</th><th>FHIR resource element</th><th>Mandatory/<br/>Required/<br/>Optional</th><th>Notes</th>
</tr>
<tr>
<td>Date</td><td>DCH-ProfessionalComment-Communication-1.sent</td><td>Mandatory</td><td></td>
</tr>
<tr>
<td>ODS Site Code</td><td>CareConnect-Location-1.identifier (ODS Site Code)</td><td>Required</td><td></td>
</tr>
<tr>
<td>SDS Job Role Name</td><td>CareConnect-DCH-PractitionerRole-1.code (SDS Job Role Name)</td><td>Required</td><td></td>
</tr>
<tr>
<td>Professional Name</td><td>CareConnect-DCH-Practitioner.name</td><td>Required</td><td></td>
</tr>
<tr>
<td>Summary</td><td>DCH-ProfessionalComment-Communication-1.payload.contentString</td><td>Required</td><td></td>
</tr>
<tr>
<td>Recipient</td><td>DCH-RelatedPerson-1.relationship</td><td>Optional</td><td></td>
</tr>
</table>

### Linkage Diagram ###

<img src="images/explore/Professional-Summary.png">

### Professional Summary XML Example ###

<script src="https://gist.github.com/IOPS-DEV/45fab86391469df4b330c9ce86601f47.js"></script>

### Professional Summary JSON Example ###

<script src="https://gist.github.com/IOPS-DEV/24aa903f6e43d95352e93f596d2017cb.js"></script>
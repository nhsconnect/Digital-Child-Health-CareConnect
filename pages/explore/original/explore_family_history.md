---
title: Family History Event Message Bundle
keywords:  messaging, bundles
tags: [fhir,messaging]
sidebar: foundations_sidebar
permalink: explore_family_history.html
summary: "The FHIR profiles used for the Family History Event Message Bundle"
---

The following FHIR profiles are used to form the Family History Event Message Bundle:

- [DCH-Bundle-1](https://fhir.nhs.uk/STU3/StructureDefinition/DCH-Bundle-1)
- [DCH-MessageHeader-1](https://fhir.nhs.uk/STU3/StructureDefinition/DCH-MessageHeader-1) - where the coding and display for the event element is fixed to 'CH013 - Family History'
- [CareConnect-Organization-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Organization-1)
- [DCH-HealthcareService-1](https://fhir.nhs.uk/STU3/StructureDefinition/DCH-HealthcareService-1)
- [CareConnect-DCH-Patient-1](https://fhir.nhs.uk/STU3/StructureDefinition/CareConnect-DCH-Patient-1)
- [CareConnect-DCH-Encounter-1](https://fhir.nhs.uk/STU3/StructureDefinition/CareConnect-DCH-Encounter-1)
- [CareConnect-Location-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Location-1)
- [CareConnect-DCH-FamilyMemberHistory-1](https://fhir.nhs.uk/STU3/StructureDefinition/CareConnect-DCH-FamilyMemberHistory-1)
- [CareConnect-DCH-MaternalProblemsInPregnancy-FamilyMemberHistory-1](https://fhir.nhs.uk/STU3/StructureDefinition/CareConnect-DCH-MaternalProblemsInPregnancy-FamilyMemberHistory-1)
- [DCH-ProfessionalComment-Communication-1](https://fhir.nhs.uk/STU3/StructureDefinition/DCH-ProfessionalComment-Communication-1)

### Family History Event data item mapping to FHIR profiles ###

The Child Health Event data items are fulfilled by elements within the FHIR resources listed below:

<table>
<tr>
<th>DCH Data Item</th><th>FHIR resource element</th><th>Mandatory/<br/>Required/<br/>Optional</th><th>Notes</th>
</tr>
<tr>
<td>Date/Time</td><td>CareConnect-DCH-Encounter-1.period.start</td><td>Mandatory</td><td></td>
</tr>
<tr>
<td>ODS/ORD Site Code</td><td>CareConnect-Location-1.identifier (ODS Site Code)</td><td>Required</td><td></td>
</tr>
<tr>
<td>Family History</td><td>CareConnect-DCH-FamilyMemberHistory-1.condition.code</td><td>Mandatory</td><td></td>
</tr>
<tr>
<td>Relationship to child</td><td>CareConnect-DCH-FamilyMemberHistory-1.relationship.code</td><td>Required</td><td></td>
</tr>
<tr>
<td>Maternal Problems in Pregnancy Impacting Fetus</td><td>CareConnect-DCH-MaternalProblemsInPregnancy-FamilyMemberHistory-1.condition.code.text</td><td>Required</td><td></td>
</tr>
<tr>
<td>Maternal or Paternal relation</td><td>CareConnect-DCH-FamilyMemberHistory-1.relationship.code</td><td>Required</td><td>CareConnect-DCH-FamilyMemberHistory-1.relationship.code shall contain 2 codes - one for the relationship type and a further code to confirm whether the relation is part of the maternal or paternal side of the family</td>
</tr>
<tr>
<td>Comment</td><td>DCH-ProfessionalComment-Communication-1</td><td>Optional</td><td></td>
</tr>
</table>

### Linkage Diagram ###

<img src="images/explore/Family-History.png">

### Family History XML Example ###

<script src="https://gist.github.com/IOPS-DEV/52f95cfa66f11598ca4be4dbc40d930f.js"></script>

### Family History JSON Example ###

<script src="https://gist.github.com/IOPS-DEV/195d5cc44005f4e4d31b0c40226da13c.js"></script>




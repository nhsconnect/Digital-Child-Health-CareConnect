---
title: Examination Findings Event Message Bundle
keywords:  messaging, bundles
tags: [fhir,messaging]
sidebar: foundations_sidebar
permalink: explore_examination_findings.html
summary: "The FHIR profiles used for the Examination Findings Event Message Bundle"
---

## FHIR Profiles ##

The following FHIR profiles are used to form the Examination Findings Event Message Bundle:

- [Bundle](http://hl7.org/fhir/STU3/StructureDefinition/Bundle)
- [Event-MessageHeader-1](https://fhir.nhs.uk/STU3/StructureDefinition/Event-MessageHeader-1) - where the coding and display for the event element is fixed to '​examination-findings-1 \| ​Examination Findings  '
- [CareConnect-Organization-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Organization-1)
- [CareConnect-HealthcareService-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-HealthcareService-1)
- [CareConnect-Patient-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Patient-1)
- [CareConnect-Encounter-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Encounter-1)
- [CareConnect-Location-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Location-1)
- [CareConnect-Practitioner-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Practitioner-1)
- [CareConnect-PractitionerRole-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-PractitionerRole-1)
- [CareConnect-Procedure-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Procedure-1)

## Bundle Structure

Specifies referencing within the Event Message Bundle.

<div style="text-align:center; margin-bottom:20px" >
	<a href="images/explore/dch-examinationfindings.png" target="_blank"><img src="images/explore/dch-examinationfindings.png"></a><br/>
	Examination Findings <a href="images/explore/dch-examinationfindings.png" target="_blank">(open in new TAB)</a>
</div>

## Examination Findings data item mapping to FHIR profiles ##

This Mapping table defines the FHIR elements that SHALL be used to encode the Healthy Child Event Specification data items for each DCH Event Message payload.  
Some common data item mappings, such as patient, publisher or Date/Time of event information, are defined within the [Header mapping table](explore_event_header_design.html) and SHALL be considered in parallel with the payload mapping.

The Child Health Event data items are fulfilled by elements within the FHIR resources listed below:

| DCH Data Item            | FHIR resource element                                 | Mandatory/Required/Optional |
|--------------------------|-------------------------------------------------------|-----------------------------|
| Date/Time                                       | CareConnect-Encounter-1.period.start                            | Mandatory                              | Format is YYYY-MM-DD”T”HH:MM:SS |
| ODS/ORD Site Code                               | CareConnect-Organization-1.identifier                               | Required                               |                                 |
| Performing Professional                         | CareConnect-Practitioner-1.name                                 | Required                               |                                 |
| SDS Job Role Name                               | CareConnect-PractitionerRole-1.code (SDS Job Role Name)         | Mandatory                              |                                 |
| Examination                                     | CareConnect-Procedure-1.code.coding.code     | Required                               | When no code is available for the Examination, a text description of the examination may be entered in code.text                                |
| Examination Finding                             | CareConnect-Procedure-1.outcome.coding.code  | Required                               | Allow SNOMED CT only            |


## Resource Population Requirements and Guidance ##

The following requirements and resource population guidance should be followed in addition to the requirements and guidance outlined in the data item mapping above and in the [Event Header](https://developer.nhs.uk/apis/ems-beta/explore_event_header_information.html) requirements page.

#### _list profiles used (and sustituted L3 variants)_ ####

## Examination Findings Example ##

<script src="https://gist.github.com/IOPS-DEV/805279f5a1bf72dd6f00032aec5b9e2e.js"></script>


## Profile Change Mappings for Examination Findings ##

Profiles used in [Demographics Update Event Messages 1.2.1-Release Candidate](https://developer.nhs.uk/apis/demographicupdates-120-rc/index.html) are replaced with:

| Demographic-Event-Messages | Demographic-Event-Messages-CareConnect |
|----------------------------|----------------------------------------|
| DCH-Bundle-1 | Bundle |
| DCH-MessageHeader-1 | Event-MessageHeader-1 |
| CareConnect-Organization-1 | CareConnect-Organization-1 |
| DCH-HealthcareService-1 | CareConnect-HealthcareService-1 |
| CareConnect-DCH-Patient-1 | CareConnect-Patient-1 |
| CareConnect-DCH-Encounter-1 | CareConnect-Encounter-1 |
| CareConnect-Location-1 | CareConnect-Location-1 |
| CareConnect-DCH-Practitioner-1 | CareConnect-Practitioner-1 |
| CareConnect-DCH-PractitionerRole-1 | CareConnect-PractitionerRole-1 |
| CareConnect-DCH-ExaminationFinding-Procedure-1 | CareConnect-Procedure-1 |


<hr/>
<hr/>

## Old Stuff ##

#### retain until new content completed then remove ####



The following FHIR profiles are used to form the Examination Findings Event Message Bundle:

- [DCH-Bundle-1](https://fhir.nhs.uk/STU3/StructureDefinition/DCH-Bundle-1)
- [DCH-MessageHeader-1](https://fhir.nhs.uk/STU3/StructureDefinition/DCH-MessageHeader-1) - where the coding and display for the event element is fixed to 'CH012 - Examination Findings'
- [CareConnect-Organization-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Organization-1)
- [DCH-HealthcareService-1](https://fhir.nhs.uk/STU3/StructureDefinition/DCH-HealthcareService-1)
- [CareConnect-DCH-Patient-1](https://fhir.nhs.uk/STU3/StructureDefinition/CareConnect-DCH-Patient-1)
- [CareConnect-DCH-Encounter-1](https://fhir.nhs.uk/STU3/StructureDefinition/CareConnect-DCH-Encounter-1)
- [CareConnect-Location-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Location-1)
- [CareConnect-DCH-Practitioner-1](https://fhir.nhs.uk/STU3/StructureDefinition/CareConnect-DCH-Practitioner-1)
- [CareConnect-DCH-PractitionerRole-1](https://fhir.nhs.uk/STU3/StructureDefinition/CareConnect-DCH-PractitionerRole-1)
- [CareConnect-DCH-ExaminationFinding-Procedure-1](https://fhir.nhs.uk/STU3/StructureDefinition/CareConnect-DCH-ExaminationFinding-Procedure-1)

### Examination Findings Event data item mapping to FHIR profiles ###

This Mapping table defines the FHIR elements that SHALL be used to encode the Healthy Child Event Specification data items for each DCH Event Message payload.  
Some common data item mappings, such as patient, publisher or Date/Time of event information, are defined within the [Header mapping table](explore_event_header_design.html) and SHALL be considered in parallel with the payload mapping.

The Child Health Event data items are fulfilled by elements within the FHIR resources listed below:

| DCH Data Item                                   | FHIR resource element                                               | Mandatory/<br/>Required/<br/>Optional  |  Note                           |
|-------------------------------------------------|--------------------------------------------------------------------------------------------------------------|---------------------------------|
| Date/Time                                       | CareConnect-DCH-Encounter-1.period.start                            | Mandatory                              | Format is YYYY-MM-DD”T”HH:MM:SS |
| ODS/ORD Site Code                               | CareConnect-Organization-1.identifier                               | Required                               |                                 |
| Performing Professional                         | CareConnect-DCH-Practitioner-1.name                                 | Required                               |                                 |
| SDS Job Role Name                               | CareConnect-DCH-PractitionerRole-1.code (SDS Job Role Name)         | Mandatory                              |                                 |
| Examination                                     | CareConnect-DCH-ExaminationFinding-Procedure-1.code.coding.code     | Required                               | When no code is available for the Examination, a text description of the examination may be entered in code.text                                |
| Examination Finding                             | CareConnect-DCH-ExaminationFinding-Procedure-1.outcome.coding.code  | Required                               | Allow SNOMED CT only            |

### Linkage Diagram ###

This Linkage diagram defines the required references that SHALL be made between resources within the DCH Event Message bundle. It includes both Header and Payload resources (but omits the DCH-Bundle-1 wrapper).

<img src="images/explore/ExaminationFindings.png">

### Examination Findings XML Example ###

<script src="https://gist.github.com/IOPS-DEV/c64035456e26959021847c204a5ab57d.js"></script>

### Examination Findings JSON Example ###

<script src="https://gist.github.com/IOPS-DEV/232228535fe1ad5d01eb8f6953efa13c.js"></script>
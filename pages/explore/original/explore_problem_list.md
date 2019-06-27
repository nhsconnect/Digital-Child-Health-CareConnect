---
title: Problem List Event Message Bundle
keywords:  messaging, bundles
tags: [fhir,messaging]
sidebar: foundations_sidebar
permalink: explore_problem_list.html
summary: "The FHIR profiles used for the Problem List Event Message Bundle"
---

The following FHIR profiles are used to form the Problem List Event Message Bundle:

- [DCH-Bundle-1](https://fhir.nhs.uk/STU3/StructureDefinition/DCH-Bundle-1)
- [DCH-MessageHeader-1](https://fhir.nhs.uk/STU3/StructureDefinition/DCH-MessageHeader-1) - where the coding and display elements for the 'event' type are fixed to 'CH008 - Problem List'
- [CareConnect-Organization-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Organization-1)
- [DCH-HealthcareService-1](https://fhir.nhs.uk/STU3/StructureDefinition/DCH-HealthcareService-1)
- [CareConnect-DCH-Patient-1](https://fhir.nhs.uk/STU3/StructureDefinition/CareConnect-DCH-Patient-1)
- [CareConnect-DCH-Encounter-1](https://fhir.nhs.uk/STU3/StructureDefinition/CareConnect-DCH-Encounter-1)
- [CareConnect-Location-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Location-1)
- [CareConnect-DCH-Diagnosis-Condition-1](https://fhir.nhs.uk/STU3/StructureDefinition/CareConnect-DCH-Diagnosis-Condition-1)
- [CareConnect-DCH-FetalDiagnosis-Condition-1](https://fhir.nhs.uk/STU3/StructureDefinition/CareConnect-DCH-FetalDiagnosis-Condition-1)
- [CareConnect-DCH-Practitioner-1](https://fhir.nhs.uk/STU3/StructureDefinition/CareConnect-DCH-Practitioner-1)
- [CareConnect-DCH-PractitionerRole-1](https://fhir.nhs.uk/STU3/StructureDefinition/CareConnect-DCH-PractitionerRole-1)

### Problem List Event Event data item mapping to FHIR profiles ###

This Mapping table defines the FHIR elements that SHALL be used to encode the Healthy Child Event Specification data items for each DCH Event Message payload.  
Some common data item mappings, such as patient, publisher or Date/Time of event information, are defined within the [Header mapping table](explore_event_header_design.html) and SHALL be considered in parallel with the payload mapping.

The Child Health Event data items are fulfilled by elements within the FHIR resources listed below:

| DCH Data Item           | FHIR resource element                                    | Mandatory/<br/>Required/<br/>Optional | Note                    |
|-------------------------|----------------------------------------------------------|---------------------------------------|-------------------------|
| Date/Time               | CareConnect-DCH-Diagnosis-Condition-1.assertedDate       | Mandatory                             | Format is YYYY-MM-DD”T”HH:MM:SS  |
| ODS/ORD Site Code       | CareConnect-Organization-1.identifier (odsSiteCode)      | Required                              |                         |
| SDS Job Role Name       | CareConnect-DCH-PractitionerRole-1.code (sdsJobRoleName) | Required                              |                         |
| Performing Professional | CareConnect-DCH-Practitioner-1.name                      | Required                              |                         |
| Condition               | CareConnect-DCH-Diagnosis-Condition-1.code               | Mandatory                             |                         |
| Condition onset date    | CareConnect-DCH-Diagnosis-Condition-1.onsetDateTime or onsetString | Required                    |To allow free text and date, rather than just date.  Uses the [FHIR date time format](http://hl7.org/fhir/stu3/datatypes.html#dateTime )                         |
| Condition end date      | CareConnect-DCH-Diagnosis-Condition-1.abatementDateTime or abatementString  | Required                    |Uses the [FHIR date time format](http://hl7.org/fhir/stu3/datatypes.html#dateTime )                         |
| Fetal Diagnosis         | CareConnect-DCH-FetalDiagnosis-Condition-1               | Optional                              |                         |
| Comment                 | CareConnect-DCH-Diagnosis-Condition-1.note               | Optional                              | Free text (no maximum characters) |


### Reference Linkage Diagram ###

This Linkage diagram defines the required references that SHALL be made between resources within the DCH Event Message bundle. It includes both Header and Payload resources (but omits the DCH-Bundle-1 wrapper).

<img src="images/explore/ProblemList.png">

### Problem List Bundle XML Example ###

<script src="https://gist.github.com/IOPS-DEV/86f4c784c063366f7e90a32cc9e9c50f.js"></script>

### Problem List Bundle JSON Example ###

<script src="https://gist.github.com/IOPS-DEV/a5123084e12eef41b1cdbb0f78fe8370.js"></script>
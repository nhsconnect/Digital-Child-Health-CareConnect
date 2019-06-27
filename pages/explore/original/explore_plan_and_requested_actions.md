---
title: Plan and Requested Actions Event Message Bundle
keywords:  messaging, bundles
tags: [fhir,messaging]
sidebar: foundations_sidebar
permalink: explore_plan_and_requested_actions.html
summary: "The FHIR profiles used for the Plan and Requested Actions Event Message Bundle"
---

The following FHIR profiles are used to form the Plan and Requested Actions Event Message Bundle:

- [DCH-Bundle-1](https://fhir.nhs.uk/STU3/StructureDefinition/DCH-Bundle-1)
- [DCH-MessageHeader-1](https://fhir.nhs.uk/STU3/StructureDefinition/DCH-MessageHeader-1) - where the coding and display for the event element is fixed to 'CH025 - Plan and Requested Actions'
- [CareConnect-Organization-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Organization-1)
- [DCH-HealthcareService-1](https://fhir.nhs.uk/STU3/StructureDefinition/DCH-HealthcareService-1)
- [CareConnect-DCH-Patient-1](https://fhir.nhs.uk/STU3/StructureDefinition/CareConnect-DCH-Patient-1)
- [CareConnect-DCH-Encounter-1](https://fhir.nhs.uk/STU3/StructureDefinition/CareConnect-DCH-Encounter-1)
- [CareConnect-Location-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Location-1)
- [DCH-PlanAndRequestedActions-CarePlan-1](https://fhir.nhs.uk/STU3/StructureDefinition/DCH-PlanAndRequestedActions-CarePlan-1)
- [DCH-RelatedPerson-1](https://fhir.nhs.uk/STU3/StructureDefinition/DCH-RelatedPerson-1)
- [CareConnect-DCH-Practitioner-1](https://fhir.nhs.uk/STU3/StructureDefinition/CareConnect-DCH-Practitioner-1)
- [CareConnect-DCH-PractitionerRole-1](https://fhir.nhs.uk/STU3/StructureDefinition/CareConnect-DCH-PractitionerRole-1)


### Plan and Requested Actions Event data item mapping to FHIR profiles ###

The Child Health Event data items are fulfilled by elements within the FHIR resources listed below:

| DCH Data Item     | FHIR resource element                             | Mandatory/<br/>Required/<br/>Optional |Note        |
|-------------------|---------------------------------------------------|---------------------------------------|------------|
| Date/Time         | CareConnect-DCH-Encounter-1.period.start          | Mandatory                             |            |
| ODS/ORD Site Code | CareConnect-Location-1.identifier                 | Mandatory                             |            |
| SDS Job Role Name | CareConnect-DCH-PractitionerRole-1.code           | Required                              |            |
| Performing Professional | CareConnect-DCH-Practitioner-1.name         | Required                              |            |
| Actions           | DCH-PlanAndRequestedActions-CarePlan-1.description| Mandatory                             |            |
| Recipient         | DCH-RelatedPerson-1.relationship                  | Required                              |For Plan & Requested Actions the relationship type must be from the ValueSet provided|

## Reference Linkage Diagram ##

<img src="images/explore/PlanAndRequestedActions.png" style="width:90%;max-width:90%;">


## Examples ##

<script src="https://gist.github.com/IOPS-DEV/8b32ef61f276ecf9275d22c6f7ae92a6.js"></script>

<script src="https://gist.github.com/IOPS-DEV/44c807d6eea7ccab0649dd37e37c0ef0.js"></script>
---
title: Safety Alerts Event Message Bundle
keywords:  messaging, bundles
tags: [fhir,messaging]
sidebar: foundations_sidebar
permalink: explore_safety_alerts.html
summary: "The FHIR profiles used for the Safety Alerts Event Message Bundle"
---

The following FHIR profiles are used to form the Safety Alerts Event Message Bundle:

- [DCH-Bundle-1](https://fhir.nhs.uk/STU3/StructureDefinition/DCH-Bundle-1)
- [DCH-MessageHeader-1](https://fhir.nhs.uk/STU3/StructureDefinition/DCH-MessageHeader-1) - where the coding and display for the event element is fixed to 'CH029 - Safety Alerts'
- [CareConnect-Organization-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Organization-1)
- [DCH-HealthcareService-1](https://fhir.nhs.uk/STU3/StructureDefinition/DCH-HealthcareService-1)
- [CareConnect-DCH-Patient-1](https://fhir.nhs.uk/STU3/StructureDefinition/CareConnect-DCH-Patient-1)
- [CareConnect-DCH-Encounter-1](https://fhir.nhs.uk/STU3/StructureDefinition/CareConnect-DCH-Encounter-1)
- [CareConnect-Location-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Location-1)
- [CareConnect-DCH-Practitioner-1](https://fhir.nhs.uk/STU3/StructureDefinition/CareConnect-DCH-Practitioner-1)
- [CareConnect-DCH-PractitionerRole-1](https://fhir.nhs.uk/STU3/StructureDefinition/CareConnect-DCH-PractitionerRole-1) 
- [CareConnect-Observation-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Observation-1)

### Safety Alerts Event data item mapping to FHIR profiles ###

This Mapping table defines the FHIR elements that SHALL be used to encode the Healthy Child Event Specification data items for each DCH Event Message payload.  
Some common data item mappings, such as patient, publisher or Date/Time of event information, are defined within the [Header mapping table](explore_event_header_design.html) and SHALL be considered in parallel with the payload mapping.

The Child Health Event data items are fulfilled by elements within the FHIR resources listed below:

| DCH Data Item     | FHIR Resource element                                       | Mandatory/<br/>Required/<br/>Optional | Note                                                                 |
|-------------------|-------------------------------------------------------------|---------------------------------------|----------------------------------------------------------------------|
| Date              | CareConnect-DCH-Encounter-1.period.start                    | Mandatory                             |                                                                      |
| ODS Site Code     | CareConnect-Location-1.identifier (ODS Site Code)           | Required                              |                                                                      |
| SDS Job Role Name | CareConnect-DCH-PractitionerRole-1.code (SDS Job Role Name) | Required                              |                                                                      |
| Professional Name | CareConnect-DCH-Practitioner-1.name                         | Required                              |                                                                      |
| Risk Type         | CareConnect-Observation-1.code.text                         | Required                              | Risk type SHALL be represented by setting code.text to 'Risk to self', 'Risk to others' or 'Risk from others'  |
| Risk End Date     | CareConnect-Observation-1.effectivePeriod.end               | Required                              |                                                                      |
| Risk Details      | CareConnect-Observation-1.valueString                       | Required                              | The identified risk is documented in Observation.valueString as free text.          |

Multiple 'Risks' SHALL be recorded as multiple, separate Observation resources within the Safety Alerts Event Message Bundle.

### Linkage Diagram ###

This Linkage diagram defines the required references that SHALL be made between resources within the DCH Event Message bundle. It includes both Header and Payload resources (but omits the DCH-Bundle-1 wrapper).

<img src="images/explore/SafetyAlerts.png">

### Safety Alerts XML Example ###

<script src="https://gist.github.com/IOPS-DEV/9cabbe020c71b79b32c8595c17661098.js"></script>

### Safety Alerts JSON Example ###

<script src="https://gist.github.com/IOPS-DEV/898e56846e6b7553efe70e0ce336f565.js"></script>
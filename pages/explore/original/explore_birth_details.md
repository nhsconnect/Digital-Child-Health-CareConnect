---
title: Birth Details Event Message Bundle
keywords:  messaging, bundles
tags: [fhir,messaging]
sidebar: foundations_sidebar
permalink: explore_birth_details.html
summary: "The FHIR profiles used for the Birth Details Event Message Bundle"
---

The following FHIR profiles are used to form the Birth Details Event Message Bundle:

- [DCH-Bundle-1](https://fhir.nhs.uk/STU3/StructureDefinition/DCH-Bundle-1)
- [DCH-MessageHeader-1](https://fhir.nhs.uk/STU3/StructureDefinition/DCH-MessageHeader-1) - where the coding and display for the event element is fixed to 'CH005 - Birth Details'
- [CareConnect-Organization-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Organization-1)
- [DCH-HealthcareService-1](https://fhir.nhs.uk/STU3/StructureDefinition/DCH-HealthcareService-1)
- [CareConnect-DCH-Patient-1](https://fhir.nhs.uk/STU3/StructureDefinition/CareConnect-DCH-Patient-1)
- [CareConnect-DCH-Encounter-1](https://fhir.nhs.uk/STU3/StructureDefinition/CareConnect-DCH-Encounter-1) - where the type element is represented using Child Health Encounter type '003 - Birth'
- [CareConnect-DCH-PhysicalProblemAtBirth-Condition-1](https://fhir.nhs.uk/STU3/StructureDefinition/CareConnect-DCH-PhysicalProblemAtBirth-Condition-1)
- [CareConnect-DCH-ProblemDuringDelivery-Condition-1](https://fhir.nhs.uk/STU3/StructureDefinition/CareConnect-DCH-ProblemDuringDelivery-Condition-1)
- [CareConnect-DCH-APGARScore-Observation-1](https://fhir.nhs.uk/STU3/StructureDefinition/CareConnect-DCH-APGARScore-Observation-1)
- [CareConnect-DCH-LengthOfGestation-Observation-1](https://fhir.nhs.uk/STU3/StructureDefinition/CareConnect-DCH-LengthOfGestation-Observation-1)
- [CareConnect-DCH-NumberOfBirths-Observation-1](https://fhir.nhs.uk/STU3/StructureDefinition/CareConnect-DCH-NumberOfBirths-Observation-1)
- [CareConnect-DCH-SpontaneousRespirationOnset-Observation-1](https://fhir.nhs.uk/STU3/StructureDefinition/CareConnect-DCH-SpontaneousRespirationOnset-Observation-1)
- [CareConnect-DCH-NeonatalResuscitationMethod-Procedure-1](https://fhir.nhs.uk/STU3/StructureDefinition/CareConnect-DCH-NeonatalResuscitationMethod-Procedure-1)
- [CareConnect-DCH-FinalDeliveryType-Procedure-1](https://fhir.nhs.uk/STU3/StructureDefinition/CareConnect-DCH-FinalDeliveryType-Procedure-1)
- [CareConnect-DCH-AttemptedDeliveryType-Condition-1](https://fhir.nhs.uk/STU3/StructureDefinition/CareConnect-DCH-AttemptedDeliveryType-Condition-1)
- [CareConnect-DCH-PutToBreastIndicator-Observation-1](https://fhir.nhs.uk/STU3/StructureDefinition/CareConnect-DCH-PutToBreastIndicator-Observation-1)
- [CareConnect-DCH-Delivery-Location-1](https://fhir.nhs.uk/STU3/StructureDefinition/CareConnect-DCH-Delivery-Location-1)

### Birth Details Event data item mapping to FHIR profiles ###

This Mapping table defines the FHIR elements that SHALL be used to encode the Healthy Child Event Specification data items for each DCH Event Message payload.  
Some common data item mappings, such as patient, publisher or Date/Time of event information, are defined within the [Header mapping table](explore_event_header_design.html) and SHALL be considered in parallel with the payload mapping.

The Child Health Event data items are fulfilled by elements within the FHIR resources listed below:

| DCH Data Item                       | FHIR resource element                                                   | Mandatory/Required/Optional |
|-------------------------------------|-------------------------------------------------------------------------|-----------------------------|
| Location of Birth                   | CareConnect-DCH-Delivery-Location-1.identifier (ODS Site Code)           | Mandatory                   |
| Delivery Place Type Code            | CareConnect-DCH-Delivery-Location-1.identifier (ODS Site Code)          | Mandatory                   |
| Birth Order                         | CareConnect-DCH-Patient-1.multipleBirthInteger                     | Mandatory                   |
| Length of Gestation at Birth        | CareConnect-DCH-LengthOfGestation-Observation-1.valueQuantity           | Mandatory                   |
| Number of Births in confinement     | CareConnect-DCH-NumberOfBirths-Observation-1.valueQuantity                  | Mandatory                    |
| Problems during Delivery            | CareConnect-DCH-ProblemDuringDelivery-Condition-1.code                          | Required                    |
| Physical Problems detected at Birth | CareConnect-DCH-PhysicalProblemAtBirth-Condition-1.code            | Required                    |
| Neonatal Resuscitation Method       | CareConnect-DCH-NeonatalResuscitationMethod-Procedure-1.code                           | Required                 |
| Date and Time of Birth              | CareConnect-DCH-Patient-1.birthDate (with patient-BirthTime extension)                           | Mandatory                 |
| Type of Delivery                    | CareConnect-DCH-FinalDeliveryType-Procedure-1.code   | Mandatory                    |
| Attempted Type of Delivery          | CareConnect-DCH-AttemptedDeliveryType-Condition-1.code   | Required                    |
| Onset of Spontaneous Respiration    | CareConnect-DCH-SpontaneousRespirationOnset-Observation-1.component  | Required                    |
| APGAR Score (1 Minute)              | CareConnect-DCH-APGARScore-Observation-1.valueQuantity                 | Mandatory                   |
| APGAR Score (5 Minute)              | CareConnect-DCH-APGARScore-Observation-1.valueQuantity                  | Mandatory                   |
| APGAR Score (10 Minute)             | CareConnect-DCH-APGARScore-Observation-1.valueQuantity                | Required                    |
| Put To Breast                       | CareConnect-DCH-PutToBreastIndicator-Observation-1.code                  | Required                    |

### Reference Linkage Diagram ###

This Linkage diagram defines the required references that SHALL be made between resources within the DCH Event Message bundle. It includes both Header and Payload resources (but omits the DCH-Bundle-1 wrapper).

<img src="images/explore/BirthDetails1.png">

Allowed Birth Details conditions, observations and procedures are: 

<img src="images/explore/BirthDetails2.png">

### Examples ###

<script src="https://gist.github.com/IOPS-DEV/20d86f149c4bf1abae4ec53bbd60b883.js"></script>

<script src="https://gist.github.com/IOPS-DEV/113951f86f8db0eae46433cdfe46481e.js"></script>
---
title: Observations Event Message Bundle
keywords:  messaging, bundles
tags: [fhir,messaging]
sidebar: foundations_sidebar
permalink: explore_observations.html
summary: "The FHIR profiles used for the Observations Event Message Bundle"
---

The following FHIR profiles are used to form the Observations Event Message Bundle:

- [DCH-Bundle-1](https://fhir.nhs.uk/STU3/StructureDefinition/DCH-Bundle-1)
- [DCH-MessageHeader-1](https://fhir.nhs.uk/STU3/StructureDefinition/DCH-MessageHeader-1) - where the c
oding and display for the event element is fixed to 'CH018 - Observations'
- [CareConnect-Organization-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Organization-1)
- [DCH-HealthcareService-1](https://fhir.nhs.uk/STU3/StructureDefinition/DCH-HealthcareService-1)
- [CareConnect-DCH-Patient-1](https://fhir.nhs.uk/STU3/StructureDefinition/CareConnect-DCH-Patient-1)
- [CareConnect-DCH-Encounter-1](https://fhir.nhs.uk/STU3/StructureDefinition/CareConnect-DCH-Encounter-1)
- [CareConnect-Location-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Location-1)
- [CareConnect-DCH-Practitioner-1](https://fhir.nhs.uk/STU3/StructureDefinition/CareConnect-DCH-Practitioner-1)
- [CareConnect-DCH-PractitionerRole-1](https://fhir.nhs.uk/STU3/StructureDefinition/CareConnect-DCH-PractitionerRole-1) 
- [CareConnect-DCH-Weight-Observation-1](https://fhir.nhs.uk/STU3/StructureDefinition/CareConnect-DCH-Weight-Observation-1)
- [CareConnect-DCH-Height-Observation-1](https://fhir.nhs.uk/STU3/StructureDefinition/CareConnect-DCH-Height-Observation-1)
- [CareConnect-DCH-Length-Observation-1](https://fhir.nhs.uk/STU3/StructureDefinition/CareConnect-DCH-Length-Observation-1)
- [CareConnect-DCH-HeadCircumference-Observation-1](https://fhir.nhs.uk/STU3/StructureDefinition/CareConnect-DCH-HeadCircumference-Observation-1)
- [CareConnect-DCH-BMICentile-Observation-1](https://fhir.nhs.uk/STU3/StructureDefinition/CareConnect-DCH-BMICentile-Observation-1)
- [CareConnect-BloodPressure-Observation-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-BloodPressure-Observation-1)
- [CareConnect-HeartRate-Observation-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-HeartRate-Observation-1)
- [CareConnect-BodyTemperature-Observation-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-BodyTemperature-Observation-1)
- [CareConnect-RespiratoryRate-Observation-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-RespiratoryRate-Observation-1)
- [CareConnect-OxygenSaturation-Observation-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-OxygenSaturation-Observation-1)
- [CareConnect-DCH-NCMPWithdrawal-Observation-1](https://fhir.nhs.uk/STU3/StructureDefinition/CareConnect-DCH-NCMPWithdrawal-Observation-1)

### Observations Event data item mapping to FHIR profiles ###

This Mapping table defines the FHIR elements that SHALL be used to encode the Healthy Child Event Specification data items for each DCH Event Message payload.  
Some common data item mappings, such as patient, publisher or Date/Time of event information, are defined within the [Header mapping table](explore_event_header_design.html) and SHALL be considered in parallel with the payload mapping.

The Child Health Event data items are fulfilled by elements within the FHIR resources listed below.
                                                                                                   
| DCH Data Item            | FHIR resource element                                         | Mandatory/Required/Optional | Note                               |
|--------------------------|---------------------------------------------------------------|-----------------------------|------------------------------------|
| Date                     | CareConnect-DCH-Encounter-1.period.start                      | Mandatory                   |                                    |
| ODS Site Code            | CareConnect-Location-1.identifier (ODS Site Code)             | Mandatory                   |                                    |
| Professional Name        | CareConnect-DCH-Practitioner-1.name                           | Mandatory                   |                                    |
| SDS Job Role Name        | CareConnect-DCH-PractitionerRole-1.code (SDS Job Role Name)   | Mandatory                   |                                    |
| Encounter Type           | CareConnect-DCH-Encounter-1.type (childHealthEncounterType)   | Mandatory                   |                                    |

Observation measurement data items are fulfilled as Observation.valueQuantity elements within separate instances of a FHIR Observation resource.

All Observations are Required

Profiles used by each Observation type are listed below.

| DCH Data Item            | FHIR resource element                                         | Note                               |
|--------------------------|---------------------------------------------------------------|---------------------------------------------|
| Birth Weight             | CareConnect-DCH-Weight-Observation-1.valueQuantity                                     | Observation.code SHALL use 364589006 \| Birth weight \| |
| Birth Head Circumference | CareConnect-DCH-HeadCircumference-Observation-1.valueQuantity                          | Observation.code SHALL use 169876006 \| Birth head circumference \| |
| Head Circumference       | CareConnect-DCH-HeadCircumference-Observation-1.valueQuantity                          | Observation.code SHALL use 363812007 \| Head circumference \| |
| Weight                   | CareConnect-DCH-Weight-Observation-1.valueQuantity                                     | Observation.code SHALL use 27113001 \| Body weight \| |
| Body Height              | CareConnect-DCH-Height-Observation-1.valueQuantity                                     | Observation.code SHALL use 50373000 \| Body height \| |
| Body Length              | CareConnect-DCH-Length-Observation-1.valueQuantity                                     | Observation.code SHALL use 248334005 \| Body length \| |
| BMI Centile              | CareConnect-DCH-BMICentile-Observation-1.valueQuantity                                 | Observation.code SHALL use 896691000000102 \| Child body mass index centile \| |
| Systolic Blood Pressure  | CareConnect-BloodPressure-Observation-1.component[systolicComponent].valueQuantity     | * |
| Diastolic Blood Pressure | CareConnect-BloodPressure-Observation-1.component[diastolicComponent].valueQuantity    | * |
| Heart Rate               | CareConnect-HeartRate-Observation-1.valueQuantity                                      | |
| Temperature              | CareConnect-BodyTemperature-Observation-1.valueQuantity                                | For child health, a further Observation.code of 386725007 should be added, with userSelected set to true |
| Respiration Rate         | CareConnect-RespiratoryRate-Observation-1.valueQuantity                                | |
| O2 Saturation            | CareConnect-OxygenSaturation-Observation-1.valueQuantity                               | For child health, a further Observation.code of 431314004 should be added, with userSelected set to true |
| NCMP Withdrawal Reason   | CareConnect-DCH-NCMPWithdrawal-Observation-1.valueCodeableConcept.Coding.code          | ** |

\* Relevant blood pressure measurement SNOMED CT coding is fixed in the CareConnect-BloodPressure-Observation-1 profile.  
Additional Blood Pressure observations may be reported using further Observation.component elements. For which, Observation.component.code SHALL be coded with the relevant SNOMED CT concept << 75367002 \| Blood pressure \| {i.e. descendant of}

\** Observation.valueCodeableConcept SHALL be coded with the relevant SNOMED CT concept << 376251000000101 \| Excluded from national child measurement programme \| {i.e. descendant of}

### Reference Linkage Diagram ###

This Linkage diagram defines the required references that SHALL be made between resources within the DCH Event Message bundle. It includes both Header and Payload resources (but omits the DCH-Bundle-1 wrapper).

<img src="images/explore/Observations1.png">

Allowed Child Health Observations are: 

<img src="images/explore/Observations2.png">

### Examples ###

This example models a post-partum Observations panel comprising Observations for:  
- Birth weight  
- Length of body  
- Birth head circumference  
- Heart rate  
- Respiratory rate  
- Blood pressure  
- Body temperature  
- Hemoglobin saturation with oxygen  

<script src="https://gist.github.com/IOPS-DEV/a760403b74d2223308c0b515f27f54c2.js"></script>

<script src="https://gist.github.com/IOPS-DEV/0d2d01a41d19b18801bac2aed856408e.js"></script>
---
title: Admission Details Event Message Bundle
keywords:  messaging, bundles
tags: [fhir,messaging]
sidebar: foundations_sidebar
permalink: explore_admission_details.html
summary: "The FHIR profiles used for the Admission Details Event Message Bundle"
---

The following FHIR profiles are used to form the Admission Details Event Message Bundle:

- [DCH-Bundle-1](https://fhir.nhs.uk/STU3/StructureDefinition/DCH-Bundle-1)
- [DCH-MessageHeader-1](https://fhir.nhs.uk/STU3/StructureDefinition/DCH-MessageHeader-1) - where the coding and display for the event element is fixed to 'CH002 - Admission Details'
- [CareConnect-Organization-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Organization-1)
- [DCH-HealthcareService-1](https://fhir.nhs.uk/STU3/StructureDefinition/DCH-HealthcareService-1)
- [CareConnect-DCH-Patient-1](https://fhir.nhs.uk/STU3/StructureDefinition/CareConnect-DCH-Patient-1)
- [CareConnect-DCH-Encounter-1](https://fhir.nhs.uk/STU3/StructureDefinition/CareConnect-DCH-Encounter-1)
- [CareConnect-Location-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Location-1)
- [CareConnect-DCH-Practitioner-1](https://fhir.nhs.uk/STU3/StructureDefinition/CareConnect-DCH-Practitioner-1)
- [CareConnect-DCH-PractitionerRole-1](https://fhir.nhs.uk/STU3/StructureDefinition/CareConnect-DCH-PractitionerRole-1)
- [DCH-RelatedPerson-1](https://fhir.nhs.uk/STU3/StructureDefinition/DCH-RelatedPerson-1) 


### Admission Details Event data item mapping to FHIR profiles ###

The Child Health Event data items are fulfilled by elements within the FHIR resources listed below:

| DCH Data Item                    | FHIR resource element                                       | Mandatory/Required/Optional | Notes           |
|-----------------------------     |-------------------------------------------------------------|-----------------------------|-----------------|
| Date and Time of admission       | CareConnect-DCH-Encounter-1.period.start                    | Required                    |                 |
| ODS/ORD Site Code                | CareConnect-Location-1.identifier (ODS Site Code)           | Required                    |                 |
| Name of Location                 | CareConnect-Location-1.name                                 | Optional                    |                 |
| Responsible Clinician Name       | CareConnect-DCH-Practitioner-1.name                         | Required                    |                 |
| Responsible Clinician Identifier | CareConnect-DCH-Practitioner-1.identifier.value             | Required                    |                 |
| Identifier Issuer                | CareConnect-DCH-Practitioner-1.identifier.system            | Required                    | *               |
| Patient Location                 | CareConnect-Location-1.type.text                            | Optional                    |                 |
| Reason for Admission             | CareConnect-DCH-Encounter-1.reason                          | Required                    |                 |
| Admission Method                 | CareConnect-DCH-Encounter-1.hospitalization.admissionMethod | Required                    |                 |
| Specialty Admitted To            | DCH-HealthcareService-1.specialty                           | Required                    |                 |
| Source of Admission              | CareConnect-DCH-Encounter-1.hospitalization.admitSource     | Required                    |                 |
| Person Accompanying patient      | DCH-RelatedPerson-1                                         | Required                    |                 |

**\*** The Professional Registration Body identifier, e.g. the admitting Clinician's GMC number, is recorded as **Responsible Clinician Identifier** in element **CareConnect-DCH-Practitioner-1.identifier.value**.  
The identifier for the issuing Professional Registration Body is recorded as **Identifier Issuer** in element **CareConnect-DCH-Practitioner-1.identifier.system** as follows:

| Issuing Professional Registration Body         | Identifier                                |
|------------------------------------------------|-------------------------------------------|
| General Dental Council Identifier              | http://fhir.hl7.org.uk/Id/gdc-number  |
| General Medical Council Identifier             | http://fhir.hl7.org.uk/Id/gmc-number  |
| Health and Care Professions Council Identifier | http://fhir.hl7.org.uk/Id/hcpc-number |
| Nursing and Midwifery Council Identifier       | http://fhir.hl7.org.uk/Id/nmc-number  |

### Reference Linkage Diagram ###

This Linkage diagram defines the required references that SHALL be made between resources within the DCH Event Message bundle. It includes both Header and Payload resources (but omits the DCH-Bundle-1 wrapper).

<img src="images/explore/AdmissionDetails.png">

### Examples ###

<script src="https://gist.github.com/IOPS-DEV/42c721afa33d5a7ab6bbd0b5a38f2bef.js"></script>

<script src="https://gist.github.com/IOPS-DEV/756242938fe0f28526ebe6f1a4dbb7c6.js"></script>

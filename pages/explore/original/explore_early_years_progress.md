---
title: Early Years Progress Event Message Bundle
keywords:  messaging, bundles
tags: [fhir,messaging]
sidebar: foundations_sidebar
permalink: explore_early_years_progress.html
summary: "The FHIR profiles used for the Early Years Progress Event Message Bundle"
---

The following FHIR profiles are used to form the Early Years Progress Event Message Bundle:

- [DCH-Bundle-1](https://fhir.nhs.uk/STU3/StructureDefinition/DCH-Bundle-1)
- [DCH-MessageHeader-1](https://fhir.nhs.uk/STU3/StructureDefinition/DCH-MessageHeader-1) - where the coding and display for the event element is fixed to 'CH010 - Early Years Progress'
- [CareConnect-Organization-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Organization-1)
- [DCH-HealthcareService-1](https://fhir.nhs.uk/STU3/StructureDefinition/DCH-HealthcareService-1)
- [CareConnect-DCH-Patient-1](https://fhir.nhs.uk/STU3/StructureDefinition/CareConnect-DCH-Patient-1)
- [CareConnect-DCH-Encounter-1](https://fhir.nhs.uk/STU3/StructureDefinition/CareConnect-DCH-Encounter-1)
- [CareConnect-Location-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Location-1)
- [CareConnect-DCH-Practitioner-1](https://fhir.nhs.uk/STU3/StructureDefinition/CareConnect-DCH-Practitioner-1)
- [CareConnect-DCH-PractitionerRole-1](https://fhir.nhs.uk/STU3/StructureDefinition/CareConnect-DCH-PractitionerRole-1)
- [DCH-EarlyYearsProgress-QuestionnaireResponse-1](https://fhir.nhs.uk/STU3/StructureDefinition/DCH-EarlyYearsProgress-QuestionnaireResponse-1)

### Early Years Progress Event data item mapping to FHIR profiles ###

This Mapping table defines the FHIR elements that SHALL be used to encode the Healthy Child Event Specification data items for each DCH Event Message payload.  
Some common data item mappings, such as patient, publisher or Date/Time of event information, are defined within the [Header mapping table](explore_event_header_design.html) and SHALL be considered in parallel with the payload mapping.

The Child Health Event data items are fulfilled by elements within the FHIR resources listed below:

| DCH Data Item                              | FHIR Resource element                                               | Mandatory/Required/Optional |
|--------------------------------------------|---------------------------------------------------------------------|-----------------------------|
| Date/Time                                  | CareConnect-DCH-Encounter-1.period.start                            | Mandatory                   |
| Site Code                                  | CareConnect-Location-1.identifier                                   | Required                    |
| Performing Professional                    | CareConnect-DCH-Practitioner.name                                   | Required                    |
| Professional Type                          | CareConnect-DCH-PractitionerRole-1.code (SDS Job Role Name)         | Required                    |
| Parental Consent                           | DCH-EarlyYearsProgress-QuestionnaireResponse-1.parentalConsent                        | Required                    |
| Communication and Language                 | DCH-EarlyYearsProgress-QuestionnaireResponse-1.communicationAndLanguage                    | Required                    |
| Physical Development                       | DCH-EarlyYearsProgress-QuestionnaireResponse-1.physicalDevelopment                    | Required                    |
| Personal, Social and Emotional Development | DCH-EarlyYearsProgress-QuestionnaireResponse-1.personalSocialEmotionalDevelopment                    | Required                    |
| Any Areas of Concern                       | DCH-EarlyYearsProgress-QuestionnaireResponse-1.areasOfConcern                    | Required                    |
| Type of Support Requested/Provided         | DCH-EarlyYearsProgress-QuestionnaireResponse-1.supportedRequestedOrProvided                    | Required                    |


### Reference Linkage Diagram ###

This Linkage diagram defines the required references that SHALL be made between resources within the DCH Event Message bundle. It includes both Header and Payload resources (but omits the DCH-Bundle-1 wrapper).

<img src="images/explore/EarlyYearsProgress.png">

### Examples ###

<script src="https://gist.github.com/IOPS-DEV/6ece8304c418ddb441859020cbfed5b3.js"></script>

<script src="https://gist.github.com/IOPS-DEV/747b388edfb6235eae358a9bed994dca.js"></script>
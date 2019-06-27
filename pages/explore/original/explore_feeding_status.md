---
title: Feeding Status Event Message Bundle
keywords:  messaging, bundles
tags: [fhir,messaging]
sidebar: foundations_sidebar
permalink: explore_feeding_status.html
summary: "The FHIR profiles used for the Feeding Status Event Message Bundle"
---

The following FHIR profiles are used to form the Feeding Status Event Message Bundle:

- [DCH-Bundle-1](https://fhir.nhs.uk/STU3/StructureDefinition/DCH-Bundle-1)
- [DCH-MessageHeader-1](https://fhir.nhs.uk/STU3/StructureDefinition/DCH-MessageHeader-1) - where the coding and display for the event element is fixed to 'CH014 - Feeding Status'
- [CareConnect-Organization-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Organization-1)
- [DCH-HealthcareService-1](https://fhir.nhs.uk/STU3/StructureDefinition/DCH-HealthcareService-1)
- [CareConnect-DCH-Patient-1](https://fhir.nhs.uk/STU3/StructureDefinition/CareConnect-DCH-Patient-1)
- [CareConnect-DCH-Encounter-1](https://fhir.nhs.uk/STU3/StructureDefinition/CareConnect-DCH-Encounter-1)
- [CareConnect-Location-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Location-1)
- [DCH-FeedingStatus-QuestionnaireResponse-1](https://fhir.nhs.uk/STU3/StructureDefinition/DCH-FeedingStatus-QuestionnaireResponse-1)

### Feeding Status Event data item mapping to FHIR profiles ###

This Mapping table defines the FHIR elements that SHALL be used to encode the Healthy Child Event Specification data items for each DCH Event Message payload.  
Some common data item mappings, such as patient, publisher or Date/Time of event information, are defined within the [Header mapping table](explore_event_header_design.html) and SHALL be considered in parallel with the payload mapping.

The Child Health Event data items are fulfilled by elements within the FHIR resources listed below.
                                                                                                   
| DCH Data Item                                | FHIR resource element                                                                          | Mandatory/Required/Optional |
|----------------------------------------------|------------------------------------------------------------------------------------------------|-----------------------------|
| Date                                         | CareConnect-DCH-Encounter-1.period.start or DCH-FeedingStatus-QuestionnaireResponse-1.authored | Mandatory                   |
| First Milk Feed                              | DCH-FeedingStatus-QuestionnaireResponse-1.item.firstMilkFeed                | Required                   |
| Date and Time of First Milk Feed             | DCH-FeedingStatus-QuestionnaireResponse-1.item.firstMilkFeedDateTime                | Required                    |
| Feeding Status of the baby                   | DCH-FeedingStatus-QuestionnaireResponse-1.item.feedingStatus                | Required                   |
| Feeding method                               | DCH-FeedingStatus-QuestionnaireResponse-1.item.feedingMethod              | Required                    |
| Introduction of Solids                       | DCH-FeedingStatus-QuestionnaireResponse-1.item.introductionOfSolids        | Required                    |
| Approximate Date breastfeeding stopped       | DCH-FeedingStatus-QuestionnaireResponse-1.item.approximateDateBreastfeedingStopped        | Required                    |
| Feeding Concerns                             | DCH-FeedingStatus-QuestionnaireResponse-1.item.feedingConcerns        | Optional                   |

### Reference Linkage Diagram ###

This Linkage diagram defines the required references that SHALL be made between resources within the DCH Event Message bundle. It includes both Header and Payload resources (but omits the DCH-Bundle-1 wrapper).

<img src="images/explore/FeedingStatus.png">

### Examples ###

<script src="https://gist.github.com/IOPS-DEV/ab3efd71ea452f9dcbb1ba114af62572.js"></script>

<script src="https://gist.github.com/IOPS-DEV/51761312eb79458d72aa2b0c2efbb9df.js"></script>
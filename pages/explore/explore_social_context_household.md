---
title: Social Context Household Event Message Bundle
keywords:  messaging, bundles
tags: [fhir,messaging]
sidebar: foundations_sidebar
permalink: explore_social_context_household.html
summary: "The FHIR profiles used for the Social Context Household Event Message Bundle"
---

The following FHIR profiles are used to form the Social Context Household Event Message Bundle:

- [DCH-Bundle-1](https://fhir.nhs.uk/STU3/StructureDefinition/DCH-Bundle-1)
- [DCH-MessageHeader-1](https://fhir.nhs.uk/STU3/StructureDefinition/DCH-MessageHeader-1) - where the coding and display for the event element is fixed to 'CH030 - Social Context Household'
- [CareConnect-Organization-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Organization-1)
- [DCH-HealthcareService-1](https://fhir.nhs.uk/STU3/StructureDefinition/DCH-HealthcareService-1)
- [CareConnect-DCH-Patient-1](https://fhir.nhs.uk/STU3/StructureDefinition/CareConnect-DCH-Patient-1)
- [CareConnect-DCH-Encounter-1](https://fhir.nhs.uk/STU3/StructureDefinition/CareConnect-DCH-Encounter-1)
- [CareConnect-Location-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Location-1)
- [DCH-SocialContextHousehold-QuestionnaireResponse-1](https://fhir.nhs.uk/STU3/StructureDefinition/DCH-SocialContextHousehold-QuestionnaireResponse-1)

### Social Context Household Event data item mapping to FHIR profiles ###

This Mapping table defines the FHIR elements that SHALL be used to encode the Healthy Child Event Specification data items for each DCH Event Message payload.  
Some common data item mappings, such as patient, publisher or Date/Time of event information, are defined within the [Header mapping table](explore_event_header_design.html) and SHALL be considered in parallel with the payload mapping.

The Child Health Event data items are fulfilled by elements within the FHIR resources listed below:

| DCH Data Item                                        | FHIR Resource element                                                                        | Mandatory/Required/Optional |
|------------------------------------------------------|----------------------------------------------------------------------------------------------|-----------------------------|
| Mothers Education Level                              | DCH-SocialContextHousehold-QuestionnaireResponse-1.item.mothersEducationLevel          | Required                    |
| Household smoking status                             | DCH-SocialContextHousehold-QuestionnaireResponse-1.item.householdSmokingStatus         | Required                    |
| Household substance status                           | DCH-SocialContextHousehold-QuestionnaireResponse-1.item.householdSubstanceStatus       | Required                    |
| Household alcohol drinking status                    | DCH-SocialContextHousehold-QuestionnaireResponse-1.item.householdAlcoholDrinkingStatus | Required                    |
| Employment status (Mother                           | DCH-SocialContextHousehold-QuestionnaireResponse-1.item.employmentStatusMother         | Required                    |
| Mothers Occupation                                   | DCH-SocialContextHousehold-QuestionnaireResponse-1.item.occupationMother               | Required                    |
| Employment status (Father                           | DCH-SocialContextHousehold-QuestionnaireResponse-1.item.employmentStatusFather         | Required                    |
| Fathers Occupation                                   | DCH-SocialContextHousehold-QuestionnaireResponse-1.item.occupationFather               | Required                    |
| Any Household member has/had social services support | DCH-SocialContextHousehold-QuestionnaireResponse-1.item.socialServicesSupport          | Required                    |
| Accommodation status                                 | DCH-SocialContextHousehold-QuestionnaireResponse-1.item.accommodationStatus            | Mandatory                   |

### Reference Linkage Diagram ###

This Linkage diagram defines the required references that SHALL be made between resources within the DCH Event Message bundle. It includes both Header and Payload resources (but omits the DCH-Bundle-1 wrapper).

<img src="images/explore/SocialContextHousehold.png">

### Examples ###

<script src="https://gist.github.com/IOPS-DEV/d5ec50cc40302644b2a71c7e19d76fcb.js"></script>

<script src="https://gist.github.com/IOPS-DEV/c9967e11c63be5394659b2214ba1ff03.js"></script>


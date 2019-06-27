---
title: Social Context Event Message Bundle
keywords:  messaging, bundles
tags: [fhir,messaging]
sidebar: foundations_sidebar
permalink: explore_social_context.html
summary: "The FHIR profiles used for the Social Context Event Message Bundle"
---

The following FHIR profiles are used to form the Social Context Event Message Bundle:

- [DCH-Bundle-1](https://fhir.nhs.uk/STU3/StructureDefinition/DCH-Bundle-1)
- [DCH-MessageHeader-1](https://fhir.nhs.uk/STU3/StructureDefinition/DCH-MessageHeader-1) - where the coding and display for the event element is fixed to 'CH031 - Social Context'
- [CareConnect-Organization-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Organization-1)
- [DCH-HealthcareService-1](https://fhir.nhs.uk/STU3/StructureDefinition/DCH-HealthcareService-1)
- [CareConnect-DCH-Patient-1](https://fhir.nhs.uk/STU3/StructureDefinition/CareConnect-DCH-Patient-1)
- [CareConnect-DCH-Encounter-1](https://fhir.nhs.uk/STU3/StructureDefinition/CareConnect-DCH-Encounter-1)
- [CareConnect-Location-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Location-1)
- [DCH-SocialContextPerson-QuestionnaireResponse-1](https://fhir.nhs.uk/STU3/StructureDefinition/DCH-SocialContextPerson-QuestionnaireResponse-1)

### Social Context Event data item mapping to FHIR profiles ###

This Mapping table defines the FHIR elements that SHALL be used to encode the Healthy Child Event Specification data items for each DCH Event Message payload.  
Some common data item mappings, such as patient, publisher or Date/Time of event information, are defined within the [Header mapping table](explore_event_header_design.html) and SHALL be considered in parallel with the payload mapping.

The Child Health Event data items are fulfilled by elements within the FHIR resources listed below:
                                                                                                   
| DCH Data Item        | FHIR Resource element                                                       | Mandatory/<br/>Required/<br/>Optional  | Note                                     |
|----------------------|-----------------------------------------------------------------------------|----------------------------------------|------------------------------------------|
| Date/Time            | CareConnect-DCH-Encounter-1.period.start                                    | Mandatory                              | Format is YYYY-MM-DD”T”HH:MM:SS.         |
| Social Circumstances | DCH-SocialContextPerson-QuestionnaireResponse-1.item.socialCircumstances    | Required                               | Free text.                               |
| Lifestyle            | DCH-SocialContextPerson-QuestionnaireResponse-1.item.lifestyle              | Required                               | Free text.                               |
| Smoking Status       | DCH-SocialContextPerson-QuestionnaireResponse-1.item.smokingStatus          | Required                               | Allow SNOMED CT only.                  |
| Smoking Status- details| DCH-SocialContextPerson-QuestionnaireResponse-1.item:smokingStatusDetails | Optional                               | Free text.                               |
| Drug/substance use   | DCH-SocialContextPerson-QuestionnaireResponse-1.item:substanceStatus        | Required                               | Allow SNOMED CT only.                  |
| Drug/substance use - details   | DCH-SocialContextPerson-QuestionnaireResponse-11.item:alcoholUseDetails     | Optional                     | Free text.                               |
| Alcohol intake       | DCH-SocialContextPerson-QuestionnaireResponse-1.item:alchoholIntake         | Required                               | Allow SNOMED CT only.                  |
| Alcohol use - details | DCH-SocialContextPerson-QuestionnaireResponse-1.item:alcoholUseDetails     | Optional                               | Free text.                               |

### Reference Linkage Diagram ###

This Linkage diagram defines the required references that SHALL be made between resources within the DCH Event Message bundle. It includes both Header and Payload resources (but omits the DCH-Bundle-1 wrapper).

<img src="images/explore/SocialContext.png">

### Clinical Risk Factors XML Bundle Example ###

<script src="https://gist.github.com/IOPS-DEV/e1edec8139df6ee2147e2536f374b2a0.js"></script>

### Clinical Risk Factors JSON Bundle Example ###

<script src="https://gist.github.com/IOPS-DEV/828d20aeb19618cecf3b1bf550bc36e6.js"></script>
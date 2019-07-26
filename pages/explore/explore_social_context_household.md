---
title: Social Context Household Event Message Bundle
keywords:  messaging, bundles
tags: [fhir,messaging]
sidebar: foundations_sidebar
permalink: explore_social_context_household.html
summary: "The FHIR profiles used for the Social Context Household Event Message Bundle"
---
## FHIR Profiles ##

The following FHIR profiles are used to form the Social Context Household Event Message Bundle:

- [Bundle](http://hl7.org/fhir/STU3/StructureDefinition/Bundle)
- [Event-MessageHeader-1](https://fhir.nhs.uk/STU3/StructureDefinition/Event-MessageHeader-1) - where the coding and display for the event element is fixed to "​social-context-household-1 \| Social Context Household"
- [CareConnect-Organization-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Organization-1)
- [CareConnect-HealthcareService-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-HealthcareService-1)
- [CareConnect-Patient-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Patient-1)
- [CareConnect-Encounter-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Encounter-1)
- [CareConnect-Location-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Location-1)
- [CareConnect-QuestionnaireResponse-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-QuestionnaireResponse-1)


## Bundle Structure

Specifies referencing within the Event Message Bundle.


<div style="text-align:center; margin-bottom:20px" >
	<a href="images/explore/dch-socialcontexthousehold.png" target="_blank"><img src="images/explore/dch-socialcontexthousehold.png"></a><br/>
	Social Context Household <a href="images/explore/dch-dch-socialcontexthousehold.png" target="_blank">(open in new TAB)</a>
</div>

## Social Context Household Event data item mapping to FHIR profiles ##

This Mapping table defines the FHIR elements that SHALL be used to encode the Healthy Child Event Specification data items for each DCH Event Message payload.  
Some common data item mappings, such as patient, publisher or Date/Time of event information, are defined within the [Header mapping table](explore_event_header_design.html) and SHALL be considered in parallel with the payload mapping.

The Child Health Event data items are fulfilled by elements within the FHIR resources listed below:

| DCH Data Item                                        | FHIR Resource element                                                                  | Mandatory/<br/>Required/<br/>Optional  |  Note                           |
|------------------------------------------------------|----------------------------------------------------------------------------------------|----------------------------------------|---------------------------------|
| Date/Time                                            | CareConnect-Encounter-1.period.start                                               | Mandatory                              | Format is YYYY-MM-DD”T”HH:MM:SS |
| Mothers Education Level                              | CareConnect-QuestionnaireResponse-1.item:mothersEducationLevel          | Required                               | Free text                       |
| Smoking status within the house                      | CareConnect-QuestionnaireResponse-1.item:householdSmokingStatus         | Required                               | Allow SNOMED CT only            |
| Smoking Status- details                              | CareConnect-QuestionnaireResponse-1.item:householdSmokingStatus.answer.extension:smokingStatusDetails         | Required                               | Free text            |
| Substance misuse status within household             | CareConnect-QuestionnaireResponse-1.item:householdSubstanceStatus       | Required                               | Allow SNOMED CT only            |
| Drug/substance use - details                         | CareConnect-QuestionnaireResponse-1.item:householdSubstanceStatus.answer.extension:substanceStatusDetails         | Required                               | Free text            |
| Alcohol Use within households                        | CareConnect-QuestionnaireResponse-1.item:householdAlcoholDrinkingStatus | Required                               |Allow SNOMED CT only             |
| Alcohol use - details                                | CareConnect-QuestionnaireResponse-1.item:householdAlcoholDrinkingStatus.answer.extension:alcoholStatusDetails | Required                               | Free text            |
| Employment status  (care giver 1)                    | CareConnect-QuestionnaireResponse-1.item:employmentStatusCareGiver1     | Required                               |                                 |
| Care giver 1's occupation                            | CareConnect-QuestionnaireResponse-1.item:occupationCareGiver1           | Required                               | Free text field to be used if no coded text available                                |
| Employment status (care giver 2)                     | CareConnect-QuestionnaireResponse-1.item:employmentStatusCareGiver2     | Required                               |                                 |
| Care giver 2's occupation                            | CareConnect-QuestionnaireResponse-1.item:occupationCareGiver2           | Required                               | Free text field to be used if no coded text available                                |
| Any Household member has/had social services support | CareConnect-QuestionnaireResponse-1.item:socialServicesSupport          | Required                               | Boolean                         |
| Accommodation status                                 | CareConnect-QuestionnaireResponse-1.item:accommodationStatus            | Mandatory                              |                                 |

## Resource Population Requirements and Guidance ##

The following requirements and resource population guidance should be followed in addition to the requirements and guidance outlined in the data item mapping above and in the [Event Header](https://developer.nhs.uk/apis/ems-beta/explore_event_header_information.html) requirements page.

#### _list profiles used (and sustituted L3 variants)_ ####

## Social Context Household Example ##

<script src="https://gist.github.com/IOPS-DEV/21f7478e810d1185c94d7d202028afc4.js"></script>


## Profile Change Mappings for Social Context Household ##

Profiles used in [Demographics Update Event Messages 1.2.1-Release Candidate](https://developer.nhs.uk/apis/demographicupdates-120-rc/index.html) are replaced with:

| Demographic-Event-Messages | Demographic-Event-Messages-CareConnect |
|----------------------------|----------------------------------------|
| DCH-Bundle-1 | Bundle |
| DCH-MessageHeader-1 | Event-MessageHeader-1 |
| CareConnect-Organization-1 | CareConnect-Organization-1 |
| DCH-HealthcareService-1 | CareConnect-HealthcareService-1 |
| CareConnect-DCH-Patient-1 | CareConnect-Patient-1 |
| CareConnect-DCH-Encounter-1 | CareConnect-Encounter-1 |
| CareConnect-Location-1 | CareConnect-Location-1 |
| DCH-SocialContextHousehold-QuestionnaireResponse-1 | CareConnect-SocialContextHousehold-QuestionnaireResponse-1 |


<hr/>
<hr/>

## Old Stuff ##

#### retain until new content completed then remove ####
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

| DCH Data Item                                        | FHIR Resource element                                                                  | Mandatory/<br/>Required/<br/>Optional  |  Note                           |
|------------------------------------------------------|----------------------------------------------------------------------------------------|----------------------------------------|---------------------------------|
| Date/Time                                            | CareConnect-DCH-Encounter-1.period.start                                               | Mandatory                              | Format is YYYY-MM-DD”T”HH:MM:SS |
| Mothers Education Level                              | DCH-SocialContextHousehold-QuestionnaireResponse-1.item:mothersEducationLevel          | Required                               | Free text                       |
| Smoking status within the house                      | DCH-SocialContextHousehold-QuestionnaireResponse-1.item:householdSmokingStatus         | Required                               | Allow SNOMED CT only            |
| Smoking Status- details                              | DCH-SocialContextHousehold-QuestionnaireResponse-1.item:householdSmokingStatus.answer.extension:smokingStatusDetails         | Required                               | Free text            |
| Substance misuse status within household             | DCH-SocialContextHousehold-QuestionnaireResponse-1.item:householdSubstanceStatus       | Required                               | Allow SNOMED CT only            |
| Drug/substance use - details                         | DCH-SocialContextHousehold-QuestionnaireResponse-1.item:householdSubstanceStatus.answer.extension:substanceStatusDetails         | Required                               | Free text            |
| Alcohol Use within households                        | DCH-SocialContextHousehold-QuestionnaireResponse-1.item:householdAlcoholDrinkingStatus | Required                               |Allow SNOMED CT only             |
| Alcohol use - details                                | DCH-SocialContextHousehold-QuestionnaireResponse-1.item:householdAlcoholDrinkingStatus.answer.extension:alcoholStatusDetails | Required                               | Free text            |
| Employment status  (care giver 1)                    | DCH-SocialContextHousehold-QuestionnaireResponse-1.item:employmentStatusCareGiver1     | Required                               |                                 |
| Care giver 1's occupation                            | DCH-SocialContextHousehold-QuestionnaireResponse-1.item:occupationCareGiver1           | Required                               | Free text field to be used if no coded text available                                |
| Employment status (care giver 2)                     | DCH-SocialContextHousehold-QuestionnaireResponse-1.item:employmentStatusCareGiver2     | Required                               |                                 |
| Care giver 2's occupation                            | DCH-SocialContextHousehold-QuestionnaireResponse-1.item:occupationCareGiver2           | Required                               | Free text field to be used if no coded text available                                |
| Any Household member has/had social services support | DCH-SocialContextHousehold-QuestionnaireResponse-1.item:socialServicesSupport          | Required                               | Boolean                         |
| Accommodation status                                 | DCH-SocialContextHousehold-QuestionnaireResponse-1.item:accommodationStatus            | Mandatory                              |                                 |

### Reference Linkage Diagram ###

This Linkage diagram defines the required references that SHALL be made between resources within the DCH Event Message bundle. It includes both Header and Payload resources (but omits the DCH-Bundle-1 wrapper).

<img src="images/explore/SocialContextHousehold.png">

### Examples ###

<script src="https://gist.github.com/IOPS-DEV/d5ec50cc40302644b2a71c7e19d76fcb.js"></script>

<script src="https://gist.github.com/IOPS-DEV/c9967e11c63be5394659b2214ba1ff03.js"></script>


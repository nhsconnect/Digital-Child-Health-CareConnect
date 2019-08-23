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
| Mothers Education Level                              | CareConnect-QuestionnaireResponse-1.item(mothersEducationLevel)          | Required                               | Free text                       |
| Smoking status within the house                      | CareConnect-QuestionnaireResponse-1.item(householdSmokingStatus)         | Required                               | Allow SNOMED CT only            |
| Smoking Status- details                              | CareConnect-QuestionnaireResponse-1.item(householdSmokingStatus).answer.extension:smokingStatusDetails         | Required                               | Free text            |
| Substance misuse status within household             | CareConnect-QuestionnaireResponse-1.item(householdSubstanceStatus)       | Required                               | Allow SNOMED CT only            |
| Drug/substance use - details                         | CareConnect-QuestionnaireResponse-1.item(householdSubstanceStatus).answer.extension:substanceStatusDetails         | Required                               | Free text            |
| Alcohol Use within households                        | CareConnect-QuestionnaireResponse-1.item(householdAlcoholDrinkingStatus) | Required                               |Allow SNOMED CT only             |
| Alcohol use - details                                | CareConnect-QuestionnaireResponse-1.item(householdAlcoholDrinkingStatus).answer.extension:alcoholStatusDetails | Required                               | Free text            |
| Employment status  (care giver 1)                    | CareConnect-QuestionnaireResponse-1.item(employmentStatusCareGiver1)     | Required                               |                                 |
| Care giver 1's occupation                            | CareConnect-QuestionnaireResponse-1.item(occupationCareGiver1)           | Required                               | Free text field to be used if no coded text available                                |
| Employment status (care giver 2)                     | CareConnect-QuestionnaireResponse-1.item(employmentStatusCareGiver2)     | Required                               |                                 |
| Care giver 2's occupation                            | CareConnect-QuestionnaireResponse-1.item(occupationCareGiver2)           | Required                               | Free text field to be used if no coded text available                                |
| Any Household member has/had social services support | CareConnect-QuestionnaireResponse-1.item(socialServicesSupport)          | Required                               | Boolean                         |
| Accommodation status                                 | CareConnect-QuestionnaireResponse-1.item(accommodationStatus)            | Mandatory                              |                                 |

## Resource Population Requirements and Guidance ##

The following requirements and resource population guidance should be followed in addition to the requirements and guidance outlined in the data item mapping above and in the [Event Header](https://developer.nhs.uk/apis/ems-beta/explore_event_header_information.html) requirements page.

### [Bundle](http://hl7.org/fhir/STU3/StructureDefinition/Bundle)

| Resource Cardinality | 1..1 |

| Element | Cardinality | Additional Guidance |
| --- | --- | --- |
| type | 1..1 | Fixed value: message |

### [Event-MessageHeader-1](https://fhir.nhs.uk/STU3/StructureDefinition/Event-MessageHeader-1)

The Event-MessageHeader-1 resource included as part of the event message SHALL conform to the [Event-MessageHeader-1](https://fhir.nhs.uk/STU3/StructureDefinition/Event-MessageHeader-1) constrained FHIR profile and the additional population guidance as per the table below:

| Resource Cardinality | 1..1 |

| Element | Cardinality | Additional Guidance |
| --- | --- | --- |
| extension(messageEventType) | 1..1 |  |
| event | 1..1 | Fixed Value: "​developmental-skills-1 \| ​Developmental Skills" |
| responsible | 1..1 | This will reference the responsible Organization resource |
| focus | 1..1 | This will reference the CareConnect-Encounter-1 resource which contains information relating to the event message. |

### [CareConnect-Organization-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Organization-1)

The CareConnect-Organization-1 resource included as part of the event message SHALL conform to the [CareConnect-Organization-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Organization-1) constrained FHIR profile and the additional population guidance as per the table below:

| Resource Cardinality | 1..* |

| Element | Cardinality | Additional Guidance |
| --- | --- | --- |
| identifier.system | 1..1 | Fixed value: https://fhir.nhs.uk/Id/ods-organization-code |
| identifier.value | 1..1 | Organisation’s ODS Organization Code |
| name | 1..1 | Organisation’s Name |


### [CareConnect-HealthcareService-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-HealthcareService-1)

The CareConnect-HealthcareService-1 resource included as part of the event message SHALL conform to the [CareConnect-HealthcareService-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-HealthcareService-1) constrained FHIR profile and the additional population guidance as per the table below:

| Resource Cardinality | 1..1 |

| Element | Cardinality | Additional Guidance |
| --- | --- | --- |
| providedBy | 1..1 | This will reference the ‘sender’ organization of the event message. |
| type | 1..1 | This will represent the type of service responsible for the event message. This will have a fixed value from the ValueSet [CareConnect-CareSettingType-1](https://fhir.hl7.org.uk/STU3/ValueSet/CareConnect-CareSettingType-1) |
| specialty | 1..1 | HealthcareService.specialty SHALL use a value from https://fhir.nhs.uk/STU3/ValueSet/DCH-Specialty-1 |


### [CareConnect-Patient-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Patient-1)

The CareConnect-Patient-1 resource included as part of the event message SHALL conform to the [CareConnect-Patient-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Patient-1) constrained FHIR profile and the additional population guidance as per the table below:

| Resource Cardinality | 1..1 |

| Element | Cardinality | Additional Guidance |
| --- | --- | --- |
| meta.versionId | 1..1 | This element will contain the serial change number (SCN) of the patient record within Spine at the time this event was published. |
| identifier | 1..1 | Patient NHS Number SHALL be included within the nhsNumber identifier slice |
| name (official) | 1..1 | Patients name as registered on PDS, included within the resource as the official name element slice |
| birthDate | 1..1 | The patient birth date shall be included in the patient resource |


### [CareConnect-Encounter-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Encounter-1)

The CareConnect-Encounter-1 resource included as part of the event message SHALL conform to the [CareConnect-Encounter-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Encounter-1) constrained FHIR profile and the additional population guidance as per the table below:

| Resource Cardinality | 1..1 |

| Element | Cardinality | Additional Guidance |
| --- | --- | --- |
| Encounter.type.coding(childHealthEncounterType) | 1..1 | Encounter.type.coding(childHealthEncounterType) SHALL use a value from https://fhir.nhs.uk/STU3/ValueSet/DCH-ChildHealthEncounterType-1 |
| Encounter.reason.coding(snomedCT) | 1..1 | Encounter.reason.coding(snomedCT) SHALL use a value from https://fhir.nhs.uk/STU3/ValueSet/DCH-AdmissionReason-1 |
| serviceProvider | 1..1 | This will reference the Organisation resource hosting the Encounter |
| location | 1..1 | This will reference the Encounter's Location |
| subject | 1..1 | This will reference the patient resource representing the subject of this event |


### [CareConnect-Location-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Location-1)

The CareConnect-Location-1 resource included as part of the event message SHALL conform to the [CareConnect-Location-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Location-1) constrained FHIR profile and the additional population guidance as per the table below:

| Resource Cardinality | 0..1 |


### [CareConnect-QuestionnaireResponse-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-QuestionnaireResponse-1)

The CareConnect-QuestionnaireResponse-1 resource included as part of the event message SHALL conform to the [CareConnect-QuestionnaireResponse-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-QuestionnaireResponse-1) constrained FHIR profile and the additional population guidance as per the table below:

| Resource Cardinality | TBC |

| Element | Cardinality | Additional Guidance |
| --- | --- | --- |
| status | 1..1 | Fixed Value: completed |
| subject | 1..1 | This will reference the patient resource representing the subject of this event |
| context | 1..1 | This will reference the encounter resource representing the context of this event |

Individual Social Context items will be recorded as:

#### Mother's education level ####

| item (mothersEducationLevel)           | 0..1 | |
| item.linkId                            | 1..1 | Fixed Value: mothersEducationLevel |
| item.text                              | 1..1 | Fixed Value: Mother's education level |
| item.answer                            | 1..1 | item.answer SHALL populate either item.answer.extension.valueAnnotation.text or item.answer.valueCoding, not both |
| item.answer.valueCoding                | 0..1 | where used, item.answer.valueCoding SHALL take a value from https://fhir.nhs.uk/STU3/ValueSet/DCH-EducationLevel-1 |


#### Household smoking status ####

| item (householdSmokingStatus)          | 0..1 | |
| item.linkId                            | 1..1 | Fixed Value: householdSmokingStatus |
| item.text                              | 1..1 | Fixed Value: Household smoking status |
| item.answer                            | 1..1 | item.answer SHALL populate either item.answer.extension.valueAnnotation.text or item.answer.valueCoding, not both |
| item.answer.valueCoding                | 0..1 | where used, item.answer.valueCoding SHALL take a value from https://fhir.nhs.uk/STU3/ValueSet/DCH-HouseholdSmokingStatus-1 |


#### Household substance status ####

| item (householdSubstanceStatus)        | 0..1 | |
| item.linkId                            | 1..1 | Fixed Value: substanceStatus |
| item.text                              | 1..1 | Fixed Value: Household substance status |
| item.answer                            | 1..1 | item.answer SHALL populate either item.answer.extension.valueAnnotation.text or item.answer.valueCoding, not both |
| item.answer.valueCoding                | 0..1 | where used, item.answer.valueCoding SHALL take a value from https://fhir.nhs.uk/STU3/ValueSet/DCH-HouseholdSubstanceStatus-1 |


#### Household alcohol drinking status ####

| item (householdAlcoholDrinkingStatus)  | 0..1 | |
| item.linkId                            | 1..1 | Fixed Value: householdAlcoholDrinkingStatus |
| item.text                              | 1..1 | Fixed Value: Household alcohol drinking status |
| item.answer                            | 1..1 | item.answer SHALL populate either item.answer.extension.valueAnnotation.text or item.answer.valueCoding, not both |
| item.answer.valueCoding                | 0..1 | where used, item.answer.valueCoding SHALL take a value from https://fhir.nhs.uk/STU3/ValueSet/DCH-HouseholdAlcoholStatus-1 |


#### Employment status (care giver 1) ####

| item (employmentStatusCareGiver1)      | 0..1 | |
| item.linkId                            | 1..1 | Fixed Value: employmentStatusCareGiver1 |
| item.text                              | 1..1 | Fixed Value: Employment status (care giver 1) |
| item.answer.valueCoding                | 1..1 | item.answer.valueCoding SHALL take a value from https://fhir.nhs.uk/STU3/ValueSet/DCH-EmploymentStatus-1 |


#### Care giver 1's occupation ####

| item (occupationCareGiver1)            | 0..1 | |
| item.linkId                            | 1..1 | Fixed Value: occupationCareGiver1 |
| item.text                              | 1..1 | Fixed Value: Care giver 1's occupation |
| item.answer                            | 1..1 | item.answer SHALL populate either item.answer.extension.valueAnnotation.text or item.answer.valueCoding, not both |
| item.answer.valueCoding                | 0..1 | where used, item.answer.valueCoding SHOULD take a value https://fhir.nhs.uk/STU3/ValueSet/DCH-Occupation-1 |


#### Employment status (care giver 2) ####

| item (employmentStatusCareGiver2)      | 0..1 | |
| item.linkId                            | 1..1 | Fixed Value: employmentStatusCareGiver2 |
| item.text                              | 1..1 | Fixed Value: Employment status (care giver 2) |
| item.answer.valueCoding                | 1..1 | item.answer.valueCoding SHALL take a value from https://fhir.nhs.uk/STU3/ValueSet/DCH-EmploymentStatus-1 |


#### Care giver 2's occupation ####

| item (occupationCareGiver2)            | 0..1 | |
| item.linkId                            | 1..1 | Fixed Value: occupationCareGiver2 |
| item.text                              | 1..1 | Fixed Value: Care giver 2's occupation |
| item.answer                            | 1..1 | item.answer SHALL populate either item.answer.extension.valueAnnotation.text or item.answer.valueCoding, not both |
| item.answer.valueCoding                | 0..1 | where used, item.answer.valueCoding SHOULD take a value https://fhir.nhs.uk/STU3/ValueSet/DCH-Occupation-1 |


#### Any Household member has/had social services support ####

| item (socialServicesSupport)           | 0..1 | |
| item.linkId                            | 1..1 | Fixed Value: socialServicesSupport |
| item.text                              | 1..1 | Fixed Value: Any Household member has/had social services support |
| item.answer.valueBoolean               | 1..1 | |


#### Accommodation status ####

| item (accommodationStatus)             | 1..1 | |
| item.linkId                            | 1..1 | Fixed Value: accommodationStatus |
| item.text                              | 1..1 | Fixed Value: Accommodation status |
| item.answer.valueCoding                | 1..1 | item.answer.valueCoding SHALL take a value from https://fhir.nhs.uk/STU3/ValueSet/DCH-AccommodationStatus-1 |


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



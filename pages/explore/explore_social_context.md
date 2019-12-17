---
title: Social Context Event Message Bundle
keywords:  messaging, bundles
tags: [fhir,messaging]
sidebar: foundations_sidebar
permalink: explore_social_context.html
summary: "The FHIR profiles used for the Social Context Event Message Bundle"
---

## FHIR Profiles ##

The following FHIR profiles are used to form the Social Context Event Message Bundle:

- [Bundle](http://hl7.org/fhir/STU3/StructureDefinition/Bundle)
- [Event-MessageHeader-1](https://fhir.nhs.uk/STU3/StructureDefinition/Event-MessageHeader-1) - where the coding and display for the event element is fixed to ‘social-context-1 \| Social Context’
- [CareConnect-Organization-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Organization-1)
- [CareConnect-HealthcareService-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-HealthcareService-1)
- [CareConnect-Patient-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Patient-1)
- [CareConnect-Encounter-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Encounter-1)
- [CareConnect-Location-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Location-1)
- [CareConnect-QuestionnaireResponse-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-QuestionnaireResponse-1)

## Bundle Structure

Specifies referencing within the Event Message Bundle.

<div style="text-align:center; margin-bottom:20px" >
	<a href="images/explore/dch-socialcontext.png" target="_blank"><img src="images/explore/dch-socialcontext.png"></a><br/>
	Social Context <a href="images/explore/dch-socialcontext.png" target="_blank">(open in new TAB)</a>
</div>

## Social Context Event data item mapping to FHIR profiles ##

This Mapping table defines the FHIR elements that SHALL be used to encode the Healthy Child Event Specification data items for each DCH Event Message payload.  
Some common data item mappings, such as patient, publisher or Date/Time of event information, are defined within the [Header mapping table](explore_event_header_design.html) and SHALL be considered in parallel with the payload mapping.

The Child Health Event data items are fulfilled by elements within the FHIR resources listed below:

| DCH Data Item        | FHIR Resource element                                                       | Mandatory/<br/>Required/<br/>Optional  | Note                                     |
|----------------------|-----------------------------------------------------------------------------|----------------------------------------|------------------------------------------|
| Date/Time            | CareConnect-Encounter-1.period.start                                    | Mandatory                              | Format is YYYY-MM-DD”T”HH:MM:SS.         |
| Social Circumstances | CareConnect-QuestionnaireResponse-1.item(socialCircumstances)    | Required                               | Free text.                               |
| Lifestyle            | CareConnect-QuestionnaireResponse-1.item(lifestyle)              | Required                               | Free text.                               |
| Smoking Status       | CareConnect-QuestionnaireResponse-1.item(smokingStatus)          | Required                               | Allow SNOMED CT only.                  |
| Smoking Status- details| CareConnect-QuestionnaireResponse-1.item(smokingStatusDetails) | Optional                               | Free text.                               |
| Drug/substance use   | CareConnect-QuestionnaireResponse-1.item(substanceStatus)        | Required                               | Allow SNOMED CT only.                  |
| Drug/substance use - details   | CareConnect-QuestionnaireResponse-1.item(alcoholUseDetails)     | Optional                     | Free text.                               |
| Alcohol intake       | CareConnect-QuestionnaireResponse-1.item(alchoholIntake)         | Required                               | Allow SNOMED CT only.                  |
| Alcohol use - details | CareConnect-QuestionnaireResponse-1.item(alcoholUseDetails)     | Optional                               | Free text.                               |


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
| event | 1..1 | Fixed Value: ‘social-context-1 \| Social Context’ |
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

| Resource Cardinality | 1..1 |

| Element | Cardinality | Additional Guidance |
| --- | --- | --- |
| status | 1..1 | Fixed Value: completed |
| subject | 1..1 | This will reference the patient resource representing the subject of this event |
| context | 1..1 | This will reference the encounter resource representing the context of this event |

Individual Social Context items will be recorded as:


#### Social Circumstances

| item (socialCircumstances)           | 0..1 | |
| item.linkId                            | 1..1 | Fixed Value: socialCircumstances |
| item.text                              | 1..1 | Fixed Value: Social Circumstances |
| item.answer                            | 1..1 | |
| item.answer.valueString                | 1..1 | |

#### Lifestyle

| item (lifestyle)           | 0..1 | |
| item.linkId                            | 1..1 | Fixed Value: lifestyle |
| item.text                              | 1..1 | Fixed Value: Lifestyle |
| item.answer                            | 1..1 | |
| item.answer.valueString                | 1..1 | |

#### Smoking Status

| item (smokingStatus)           | 0..1 | |
| item.linkId                            | 1..1 | Fixed Value: smokingStatus |
| item.text                              | 1..1 | Fixed Value: Smoking Status |
| item.answer                            | 1..1 | |
| item.answer.valueCoding                | 1..1 | item.answer.valueCoding SHOULD take a value from https://fhir.nhs.uk/STU3/ValueSet/DCH-PersonSmokingStatus-1 |

#### Smoking Status - Details

| item (smokingStatusDetails)           | 0..1 | |
| item.linkId                            | 1..1 | Fixed Value: smokingStatusDetails |
| item.text                              | 1..1 | Fixed Value: Smoking Status - Details |
| item.answer                            | 1..1 | |
| item.answer.valueString                | 1..1 | |

#### Drug/substance Use

| item (drugSubstanceUse)           | 0..1 | |
| item.linkId                            | 1..1 | Fixed Value: drugSubstanceUse |
| item.text                              | 1..1 | Fixed Value: Drug/substance Use |
| item.answer                            | 1..1 | |
| item.answer.valueCoding                | 1..1 | item.answer.valueCoding SHALL take a value from https://fhir.nhs.uk/STU3/ValueSet/DCH-DrugOrSubstanceUse-1 |

#### Drug/substance use - Details

| item (drugSubstanceUseDetails)           | 0..1 | |
| item.linkId                            | 1..1 | Fixed Value: drugSubstanceUseDetails |
| item.text                              | 1..1 | Fixed Value: Drug/substance use - Details |
| item.answer                            | 1..1 | |
| item.answer.valueString                | 1..1 | |

#### Alcohol use

| item (alcoholUse)           | 0..1 | |
| item.linkId                            | 1..1 | Fixed Value: alcoholUse |
| item.text                              | 1..1 | Fixed Value: Alcohol use |
| item.answer                            | 1..1 | |
| item.answer.valueCoding                | 1..1 | item.answer.valueCoding SHALL take a value from https://fhir.nhs.uk/STU3/ValueSet/DCH-AlcoholUse-1 |

#### Alcohol use - Details

| item (alcoholUseDetails)           | 0..1 | |
| item.linkId                            | 1..1 | Fixed Value: alcoholUseDetails |
| item.text                              | 1..1 | Fixed Value: Alcohol use - Details |
| item.answer                            | 1..1 | |
| item.answer.valueString                | 1..1 | |


## Social Context Example ##

<script src="https://gist.github.com/IOPS-DEV/5cbba8e72f26e68df242424c589882a6.js"></script>


## Profile Change Mappings for Social Context ##

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
| DCH-SocialContextPerson-QuestionnaireResponse-1 | CareConnect-QuestionnaireResponse-1 |


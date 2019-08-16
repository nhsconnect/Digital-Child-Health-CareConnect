---
title: Educational History Event Message Bundle
keywords:  messaging, bundles
tags: [fhir,messaging]
sidebar: foundations_sidebar
permalink: explore_educational_history.html
summary: "The FHIR profiles used for the Educational History Event Message Bundle"
---

## FHIR Profiles ##

The following FHIR profiles are used to form the Educational History Event Message Bundle:

- [Bundle](http://hl7.org/fhir/STU3/StructureDefinition/Bundle)
- [Event-MessageHeader-1](https://fhir.nhs.uk/STU3/StructureDefinition/Event-MessageHeader-1) - where the coding and display for the event element is fixed to ‘educational-history-1 \| Educational History’
- [CareConnect-Organization-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Organization-1)
- [CareConnect-HealthcareService-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-HealthcareService-1)
- [CareConnect-Patient-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Patient-1)
- [CareConnect-Encounter-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Encounter-1)
- [CareConnect-Location-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Location-1)
- [CareConnect-QuestionnaireResponse-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-QuestionnaireResponse-1)
- [CareConnect-Communication-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Communication-1)
- [CareConnect-Practitioner-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Practitioner-1)
or
- [CareConnect-RelatedPerson-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-RelatedPerson-1)

## Bundle Structure

Specifies referencing within the Event Message Bundle.

<div style="text-align:center; margin-bottom:20px" >
	<a href="images/explore/dch-educationalhistory.png" target="_blank"><img src="images/explore/dch-educationalhistory.png"></a><br/>
	Educational History <a href="images/explore/dch-educationalhistory.png" target="_blank">(open in new TAB)</a>
</div>

## Educational History Event data item mapping to FHIR profiles ##

This Mapping table defines the FHIR elements that SHALL be used to encode the Healthy Child Event Specification data items for each DCH Event Message payload.  
Some common data item mappings, such as patient, publisher or Date/Time of event information, are defined within the [Header mapping table](explore_event_header_design.html) and SHALL be considered in parallel with the payload mapping.

The Child Health Event data items are fulfilled by elements within the FHIR resources listed below:

| DCH Data Item                                | FHIR Resource element                                                             | Mandatory/Required/Optional |             |
|----------------------------------------------|-----------------------------------------------------------------------------------|-----------------------------|-------------|
| Date/Time                                    | CareConnect-Encounter-1.period.start                                          | Mandatory                   |             |
| Educational Establishment                    | CareConnect-QuestionnaireResponse-1.item.educationalEstablishment      | Mandatory                   |             |
| Educational Establishment Name               | CareConnect-Organization-1.name                                                   | Mandatory                   |             |
| Educational Establishment ODS/ORD Site Code  | CareConnect-Organization-1.identifier                                             | Mandatory                   |             |
| Type of Educational Establishment  | CareConnect-QuestionnaireResponse-1.item.educationalEstablishmentType            | Mandatory                   |             |
| Year From                          | CareConnect-QuestionnaireResponse-1.item.educationalEstablishmentStart           | Mandatory                   | Only the Year part of the date is required  |
| Year To                            | CareConnect-QuestionnaireResponse-1.item.educationalEstablishmentEnd             | Mandatory                   | Only the Year part of the date is required  |
| Educational Assessment             | CareConnect-QuestionnaireResponse-1.item.educationalAssessmentOutcome            | Required                    |             |
| Type of Special Educational Need   | CareConnect-QuestionnaireResponse-1.item.specialEducationalNeedType              | Required                    |             |
| Special Educational Need Comment   | CareConnect-Communication-1                                                     | Optional                    |             |

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
| event | 1..1 | Fixed Value: ‘educational-history-1 \| Educational History’ |
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

| Resource Cardinality | 1..1 |

| Element | Cardinality | Additional Guidance |
| --- | --- | --- |
| status | 1..1 | Fixed Value: completed |
| subject | 1..1 | This will reference the patient resource representing the subject of this event |
| context | 1..1 | This will reference the encounter resource representing the context of this event |

Individual Educational History items will be recorded as:

#### Educational Establishment

| item (educationalEstablishment)        | 1..1 | |
| item.linkId                            | 1..1 | Fixed Value: educationalEstablishment |
| item.text                              | 1..1 | Fixed Value: Educational Establishment |
| item.answer                            | 1..1 | |
| item.answer.valueReference             | 1..1 | item.answer.valueReference SHALL reference a CareConnect-Organization-1 resource representing the Educational Establishment |

#### Type of Educational establishment

| item (itemName)                        | 1..1 | |
| item.linkId                            | 1..1 | Fixed Value: educationalEstablishmentType |
| item.text                              | 1..1 | Fixed Value: Type of Educational establishment |
| item.answer                            | 1..1 | |
| item.answer.valueCoding                | 1..1 | item.answer.valueCoding SHALL take a value from https://fhir.nhs.uk/STU3/ValueSet/DCH-EducationalEstablishmentType-1 |

#### Year From

| item (educationalEstablishmentStart)   | 1..1 | |
| item.linkId                            | 1..1 | Fixed Value: educationalEstablishmentStart |
| item.text                              | 1..1 | Fixed Value: Year From |
| item.answer                            | 1..1 | |
| item.answer.valueDate                | 1..1 | |

#### Year To

| item (educationalEstablishmentEnd)     | 1..1 | |
| item.linkId                            | 1..1 | Fixed Value: educationalEstablishmentEnd |
| item.text                              | 1..1 | Fixed Value: Year To |
| item.answer                            | 1..1 | |
| item.answer.valueDate                  | 1..1 | |

#### Educational Assessment

| item (educationalAssessmentOutcome)    | 0..1 | |
| item.linkId                            | 1..1 | Fixed Value: educationalAssessmentOutcome |
| item.text                              | 1..1 | Fixed Value: Educational Assessment |
| item.answer                            | 1..1 | |
| item.answer.valueCoding                | 1..1 | item.answer.valueCoding SHALL take a value from https://fhir.nhs.uk/STU3/ValueSet/DCH-EducationalAssessmentOutcome-1 |

#### Type of Special Educational Need

| item (specialEducationalNeedType)      | 0..1 | |
| item.linkId                            | 1..1 | Fixed Value: specialEducationalNeedType |
| item.text                              | 1..1 | Fixed Value: Type of Special Educational Need |
| item.answer                            | 1..1 | |
| item.answer.valueCoding                | 1..1 | item.answer.valueCoding SHALL take a value from https://fhir.nhs.uk/STU3/ValueSet/DCH-SpecialEducationalNeed-1 |


### [CareConnect-Communication-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Communication-1)

The CareConnect-Communication-1 resource included as part of the event message SHALL conform to the [CareConnect-Communication-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Communication-1) constrained FHIR profile and the additional population guidance as per the table below:

| Resource Cardinality | 0..1 |

| Element | Cardinality | Additional Guidance |
| --- | --- | --- |
| subject | 1..1 | This will reference the patient resource representing the subject of this event |
| context | 1..1 | This will reference the encounter resource representing the context of this event |
| sender | 1..1 | This will reference the practitioner or related person resource representing the source of this event |


### [CareConnect-Practitioner-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Practitioner-1)

The CareConnect-Practitioner-1 resource included as part of the event message SHALL conform to the [CareConnect-Practitioner-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Practitioner-1) constrained FHIR profile and the additional population guidance as per the table below:

| Resource Cardinality | 0..1 |

### [CareConnect-RelatedPerson-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-RelatedPerson-1)

The CareConnect-RelatedPerson-1 resource included as part of the event message SHALL conform to the [CareConnect-RelatedPerson-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-RelatedPerson-1) constrained FHIR profile and the additional population guidance as per the table below:

| Resource Cardinality | 0..1 |

| Element | Cardinality | Additional Guidance |
| --- | --- | --- |
| patient | 1..1 | This will reference the patient resource representing the subject of this event |


## Educational History Example ##

<script src="https://gist.github.com/IOPS-DEV/ccd736e8932c5106393999aebdd720e4.js"></script>

## Profile Change Mappings for Educational History ##

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
| DCH-EducationalHistory-QuestionnaireResponse-1 | CareConnect-QuestionnaireResponse-1 |
| DCH-ProfessionalComment-Communication-1 | CareConnect-Communication-1 |
| CareConnect-DCH-Practitioner-1 | CareConnect-Practitioner-1 |
| DCH-RelatedPerson-1 | CareConnect-RelatedPerson-1 |


---
title: Early Years Progress Event Message Bundle
keywords:  messaging, bundles
tags: [fhir,messaging]
sidebar: foundations_sidebar
permalink: explore_early_years_progress.html
summary: "The FHIR profiles used for the Early Years Progress Event Message Bundle"
---

## FHIR Profiles ##

The following FHIR profiles are used to form the Early Years Progress Event Message Bundle:

- [Bundle](http://hl7.org/fhir/STU3/StructureDefinition/Bundle)
- [Event-MessageHeader-1](https://fhir.nhs.uk/STU3/StructureDefinition/Event-MessageHeader-1) - where the coding and display for the event element is fixed to ‘early-years-progress-1 \| Early Years Progress’
- [CareConnect-Organization-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Organization-1)
- [CareConnect-HealthcareService-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-HealthcareService-1)
- [CareConnect-Patient-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Patient-1)
- [CareConnect-Encounter-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Encounter-1)
- [CareConnect-Location-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Location-1)
- [CareConnect-Practitioner-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Practitioner-1)
- [CareConnect-PractitionerRole-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-PractitionerRole-1)
- [CareConnect-QuestionnaireResponse-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-QuestionnaireResponse-1)

## Bundle Structure

Specifies referencing within the Event Message Bundle.


<div style="text-align:center; margin-bottom:20px" >
	<a href="images/explore/dch-earlyyearsprogress.png" target="_blank"><img src="images/explore/dch-earlyyearsprogress.png"></a><br/>
	Early Years Progress <a href="images/explore/dch-earlyyearsprogress.png" target="_blank">(open in new TAB)</a>
</div>

## Early Years Progress Event data item mapping to FHIR profiles ##

This Mapping table defines the FHIR elements that SHALL be used to encode the Healthy Child Event Specification data items for each DCH Event Message payload.  
Some common data item mappings, such as patient, publisher or Date/Time of event information, are defined within the [Header mapping table](explore_event_header_design.html) and SHALL be considered in parallel with the payload mapping.

The Child Health Event data items are fulfilled by elements within the FHIR resources listed below:

| DCH Data Item                              | FHIR Resource element                                               | Mandatory/Required/Optional |
|--------------------------------------------|---------------------------------------------------------------------|-----------------------------|
| Date/Time                                  | CareConnect-Encounter-1.period.start                            | Mandatory                   |
| Site Code                                  | CareConnect-Location-1.identifier                                   | Required                    |
| Performing Professional                    | CareConnect-Practitioner.name                                   | Required                    |
| Professional Type                          | CareConnect-PractitionerRole-1.code (SDS Job Role Name)         | Required                    |
| Parental Consent                           | CareConnect-QuestionnaireResponse-1.item(parentalConsent)                        | Required                    |
| Communication and Language                 | CareConnect-QuestionnaireResponse-1.item(communicationAndLanguage)                    | Required                    |
| Physical Development                       | CareConnect-QuestionnaireResponse-1.item(physicalDevelopment)                    | Required                    |
| Personal, Social and Emotional Development | CareConnect-QuestionnaireResponse-1.item(personalSocialEmotionalDevelopment)                    | Required                    |
| Any Areas of Concern                       | CareConnect-QuestionnaireResponse-1.item(areasOfConcern)                    | Required                    |
| Type of Support Requested/Provided         | CareConnect-QuestionnaireResponse-1.item(supportedRequestedOrProvided)                    | Required                    |

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
| event | 1..1 | Fixed Value: ‘early-years-progress-1 \| Early Years Progress’ |
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


### [CareConnect-Practitioner-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Practitioner-1)

The CareConnect-Practitioner-1 resource included as part of the event message SHALL conform to the [CareConnect-Practitioner-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Practitioner-1) constrained FHIR profile and the additional population guidance as per the table below:

| Resource Cardinality | 1..1 |


### [CareConnect-PractitionerRole-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-PractitionerRole-1)

The CareConnect-PractitionerRole-1 resource included as part of the event message SHALL conform to the [CareConnect-PractitionerRole-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-PractitionerRole-1) constrained FHIR profile and the additional population guidance as per the table below:

| Resource Cardinality | 1..1 |

| Element | Cardinality | Additional Guidance |
| --- | --- | --- |
| organization | 1..1 | This will reference the Organization resource responsible for the event |
| practitioner | 1..1 | This will reference the Practitioner resource responsible for the event |
| PractitionerRole.code(careProfessionalType) | 1..1 | PractitionerRole.code(careProfessionalType) SHALL use a value from https://fhir.nhs.uk/STU3/ValueSet/DCH-ProfessionalType-1 |
| PractitionerRole.code(keyWorkerStatus) | 0..1 | If Practitioner is a key worker, PractitionerRole.codekeyWorkerStatus SHALL use a value from https://fhir.nhs.uk/STU3/ValueSet/DCH-KeyWorkerStatus-1 |
| PractitionerRole.specialty | 1..1 | PractitionerRole.specialty SHALL use a value from https://fhir.nhs.uk/STU3/ValueSet/DCH-Specialty-1 |

### [CareConnect-QuestionnaireResponse-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-QuestionnaireResponse-1)

The CareConnect-QuestionnaireResponse-1 resource included as part of the event message SHALL conform to the [CareConnect-QuestionnaireResponse-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-QuestionnaireResponse-1) constrained FHIR profile and the additional population guidance as per the table below:

| Resource Cardinality | TBC |

| Element | Cardinality | Additional Guidance |
| --- | --- | --- |
| status | 1..1 | |
| subject | 1..1 | This will reference the patient resource representing the subject of this event |
| context | 1..1 | This will reference the encounter resource representing the context of this event |

Individual Early Years Progress items will be recorded as:

#### Parental Consent

| item (parentalConsent)           | 0..1 | |
| item.linkId                            | 1..1 | Fixed Value: parentalConsent |
| item.text                              | 1..1 | Fixed Value: Parental Consent |
| item.answer                            | 1..1 | |
| item.answer.valueCoding                | 1..1 | item.answer.valueCoding SHALL take a value from https://fhir.nhs.uk/STU3/ValueSet/DCH-ParentalConsentToShareInformation-1 |

#### Communication And Language

| item (communicationAndLanguage)           | 0..1 | |
| item.linkId                            | 1..1 | Fixed Value: communicationAndLanguage |
| item.text                              | 1..1 | Fixed Value: Communication And Language |
| item.answer                            | 1..1 | |
| item.answer.valueString                | 1..1 | |

#### Physical Development

| item (physicalDevelopment)           | 0..1 | |
| item.linkId                            | 1..1 | Fixed Value: physicalDevelopment |
| item.text                              | 1..1 | Fixed Value: Physical Development |
| item.answer                            | 1..1 | |
| item.answer.valueString                | 1..1 | |

#### Personal, Social and Emotional Development

| item (personalSocialEmotionalDevelopment)           | 0..1 | |
| item.linkId                            | 1..1 | Fixed Value: personalSocialEmotionalDevelopment |
| item.text                              | 1..1 | Fixed Value: Personal, Social and Emotional Development |
| item.answer                            | 1..1 | |
| item.answer.valueString                | 1..1 | |

#### Areas Of Concern

| item (areasOfConcern)           | 0..1 | |
| item.linkId                            | 1..1 | Fixed Value: areasOfConcern |
| item.text                              | 1..1 | Fixed Value: Any Areas Of Concern |
| item.answer                            | 1..1 | |
| item.answer.valueString                | 1..1 | |

#### Support Requested Or Provided

| item (supportRequestedOrProvided)           | 0..1 | |
| item.linkId                            | 1..1 | Fixed Value: supportRequestedOrProvided |
| item.text                              | 1..1 | Fixed Value: Type of Support Requested/Provided |
| item.answer                            | 1..1 | |
| item.answer.valueString                | 1..1 | |


## Early Years Progress Example ##

<script src="https://gist.github.com/IOPS-DEV/d640754dd73f2ab8b69a54d1e9b3a95b.js"></script>


## Profile Change Mappings for Early Years Progress ##

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
| CareConnect-DCH-Practitioner-1 | CareConnect-Practitioner-1 |
| CareConnect-DCH-PractitionerRole-1 | CareConnect-PractitionerRole-1 |
| DCH-EarlyYearsProgress-QuestionnaireResponse-1 | CareConnect-QuestionnaireResponse-1 |


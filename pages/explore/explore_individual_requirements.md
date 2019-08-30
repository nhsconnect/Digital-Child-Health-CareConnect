---
title: Individual Requirements Event Message Bundle
keywords:  messaging, bundles
tags: [fhir,messaging]
sidebar: foundations_sidebar
permalink: explore_individual_requirements.html
summary: "The FHIR profiles used for the Individual Requirements Event Message Bundle"
---

## FHIR Profiles ##

The following FHIR profiles are used to form the Individual Requirements Event Message Bundle:

- [Bundle](http://hl7.org/fhir/STU3/StructureDefinition/Bundle)
- [Event-MessageHeader-1](https://fhir.nhs.uk/STU3/StructureDefinition/Event-MessageHeader-1) - where the coding and display for the event element is fixed to ‘individual-requirements-1 \| Individual Requirements’
- [CareConnect-Organization-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Organization-1)
- [CareConnect-HealthcareService-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-HealthcareService-1)
- [CareConnect-Patient-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Patient-1)
- [CareConnect-Encounter-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Encounter-1)
- [CareConnect-Location-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Location-1)
- [CareConnect-QuestionnaireResponse-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-QuestionnaireResponse-1)
- [CareConnect-Practitioner-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Practitioner-1)
- [CareConnect-PractitionerRole-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-PractitionerRole-1)
- [CareConnect-Communication-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Communication-1)

## Bundle Structure

Specifies referencing within the Event Message Bundle.


<div style="text-align:center; margin-bottom:20px" >
	<a href="images/explore/dch-individualrequirements.png" target="_blank"><img src="images/explore/dch-individualrequirements.png"></a><br/>
	Individual Requirements <a href="images/explore/dch-individualrequirements.png" target="_blank">(open in new TAB)</a>
</div>

## Individual Requirements Event data item mapping to FHIR profiles ##

This Mapping table defines the FHIR elements that SHALL be used to encode the Healthy Child Event Specification data items for each DCH Event Message payload.  
Some common data item mappings, such as patient, publisher or Date/Time of event information, are defined within the [Header mapping table](explore_event_header_design.html) and SHALL be considered in parallel with the payload mapping.

The Child Health Event data items are fulfilled by elements within the FHIR resources listed below:

| DCH Data Item                                                 | FHIR Resource element                                                    | Mandatory/Required/Optional | Note                                                           |
|---------------------------------------------------------------|--------------------------------------------------------------------------|-----------------------------|---------------------------------------------------------------------|
| Date/Time                                  | CareConnect-Encounter-1.period.start                            | Mandatory                   |                                                                |
| GP Opt Out Indicator                                          | CareConnect-QuestionnaireResponse-1.item(gPOptOutIndicator)     | Required                    |                                                                |
| Individual Needs Person Indicator                             | CareConnect-QuestionnaireResponse-1.item(individualNeedsPersonIndicator) | Mandatory                   |                                                                |
| Accessible Information - Communication Support                | CareConnect-QuestionnaireResponse-1.item(communicationSupport)                    | Required                    |                                                                |
| Accessible Information - Requires Communication Professional  | CareConnect-QuestionnaireResponse-1.item(communicationProfessional)               | Required                    |                                                                |
| Accessible Information - Requires Specific Contact Method     | CareConnect-QuestionnaireResponse-1.item(specificContactMethod)                           | Required                    |                                                                |
| Accessible Information - Requires Specific Information Format | CareConnect-QuestionnaireResponse-1.item(specificInformationFormat)                       | Required                    |                                                                |
| Mobility Needs                                                | CareConnect-QuestionnaireResponse-1.item(mobilityNeeds)                         | Required                    |                                                                |
| Individual Requirement Narrative Comment                      | CareConnect-Communication-1.payload                                          | Optional                    | With Communication.category.coding.code and .display set to '015' and 'Individual Requirement' |


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
| event | 1..1 | Fixed Value: ‘individual-requirements-1 \| Individual Requirements’ |
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
| status | 1..1 | |
| subject | 1..1 | This will reference the patient resource representing the subject of this event |
| context | 1..1 | This will reference the encounter resource representing the context of this event |

Individual Requirements items will be recorded as:

#### GP Opt Out Indicator

| item (gPOptOutIndicator)           | 0..1 | |
| item.linkId                            | 1..1 | Fixed Value: gPOptOutIndicator |
| item.text                              | 1..1 | Fixed Value: GP Opt Out Indicator |
| item.answer                            | 1..1 | |
| item.answer.valueCoding                | 1..1 | item.answer.valueCoding SHALL take a value from https://fhir.nhs.uk/STU3/ValueSet/DCH-IndividualRequirement-GPOptOutIndicator-1 |

#### Individual Needs Person Indicator

| item (individualNeedsPersonIndicator)           | 0..1 | |
| item.linkId                            | 1..1 | Fixed Value: individualNeedsPersonIndicator |
| item.text                              | 1..1 | Fixed Value: Individual Needs Person Indicator |
| item.answer                            | 1..1 | |
| item.answer.valueCoding                | 1..1 | item.answer.valueCoding SHALL take a value from  https://fhir.nhs.uk/STU3/CodeSystem/DCH-IndividualRequirement-IndividualNeedsPersonIndicator-1 |

#### Communication Support

| item (communicationSupport)            | 0..1 | |
| item.linkId                            | 1..1 | Fixed Value: communicationSupport |
| item.text                              | 1..1 | Fixed Value: Accessible Information - Communication Support |
| item.answer                            | 1..1 | |
| item.answer.valueCoding                | 1..1 | item.answer.valueCoding SHOULD take a value from https://fhir.nhs.uk/STU3/ValueSet/DCH-IndividualRequirement-CommunicationSupport-1 |

#### Communication Professional

| item (communicationProfessional)           | 0..1 | |
| item.linkId                            | 1..1 | Fixed Value: communicationProfessional |
| item.text                              | 1..1 | Fixed Value: Accessible Information - Requires Communication Professional |
| item.answer                            | 1..1 | |
| item.answer.valueCoding                | 1..1 | item.answer.valueCoding SHOULD take a value from https://fhir.nhs.uk/STU3/ValueSet/DCH-IndividualRequirement-CommunicationProfessional-1 |

#### Specific Contact Method

| item (specificContactMethod)           | 0..1 | |
| item.linkId                            | 1..1 | Fixed Value: specificContactMethod |
| item.text                              | 1..1 | Fixed Value: Accessible Information - Requires Specific Contact Method |
| item.answer                            | 1..1 | |
| item.answer.valueCoding                | 1..1 | item.answer.valueCoding SHOULD take a value from https://fhir.nhs.uk/STU3/ValueSet/DCH-IndividualRequirement-ContactMethod-1 |

#### Specific Information Format

| item (specificInformationFormat)           | 0..1 | |
| item.linkId                            | 1..1 | Fixed Value: specificInformationFormat |
| item.text                              | 1..1 | Fixed Value: Accessible Information - Requires specific information format |
| item.answer                            | 1..1 | |
| item.answer.valueCoding                | 1..1 | item.answer.valueCoding SHOULD take a value from  https://fhir.nhs.uk/STU3/ValueSet/DCH-IndividualRequirement-InformationFormat-1 |

#### Mobility Needs

| item (mobilityNeeds)           | 0..1 | |
| item.linkId                            | 1..1 | Fixed Value: mobilityNeeds |
| item.text                              | 1..1 | Fixed Value: Mobility Needs |
| item.answer                            | 1..1 | |
| item.answer.valueCoding                | 1..1 | item.answer.valueCoding SHOULD take a value from https://fhir.nhs.uk/STU3/ValueSet/DCH-IndividualRequirement-MobilityNeed-1 |


### [CareConnect-Practitioner-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Practitioner-1)

The CareConnect-Practitioner-1 resource included as part of the event message SHALL conform to the [CareConnect-Practitioner-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Practitioner-1) constrained FHIR profile and the additional population guidance as per the table below:

| Resource Cardinality | 1..1 |


### [CareConnect-PractitionerRole-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-PractitionerRole-1)

The CareConnect-PractitionerRole-1 resource included as part of the event message SHALL conform to the [CareConnect-PractitionerRole-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-PractitionerRole-1) constrained FHIR profile and the additional population guidance as per the table below:

| Resource Cardinality | 1..1 | If Professional event |

| Element | Cardinality | Additional Guidance |
| --- | --- | --- |
| organization | 1..1 | This will reference the Organization resource responsible for the event |
| practitioner | 1..1 | This will reference the Practitioner resource responsible for the event |
| PractitionerRole.code(careProfessionalType) | 1..1 | PractitionerRole.code(careProfessionalType) SHALL use a value from https://fhir.nhs.uk/STU3/ValueSet/DCH-ProfessionalType-1 |
| PractitionerRole.code(keyWorkerStatus) | 0..1 | If Practitioner is a key worker, PractitionerRole.codekeyWorkerStatus SHALL use a value from https://fhir.nhs.uk/STU3/ValueSet/DCH-KeyWorkerStatus-1 |
| PractitionerRole.specialty | 1..1 | PractitionerRole.specialty SHALL use a value from https://fhir.nhs.uk/STU3/ValueSet/DCH-Specialty-1 |

### [CareConnect-Communication-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Communication-1)

The CareConnect-Communication-1 resource included as part of the event message SHALL conform to the [CareConnect-Communication-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Communication-1) constrained FHIR profile and the additional population guidance as per the table below:

| Resource Cardinality | 0..* |

| Element | Cardinality | Additional Guidance |
| --- | --- | --- |
| Communication.category.coding | 1..1 | Communication.category.coding SHOULD use a value from https://fhir.nhs.uk/STU3/CodeSystem/DCH-ProfessionalCommentType-1 |


## Individual Requirements Example ##

<script src="https://gist.github.com/IOPS-DEV/c61d4dc983f803d0b366a44d96b84bda.js"></script>


## Profile Change Mappings for Individual Requirements ##

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
| DCH-IndividualRequirements-QuestionnaireResponse-1 | CareConnect-QuestionnaireResponse-1 |
| CareConnect-DCH-Practitioner-1 | CareConnect-Practitioner-1 |
| CareConnect-DCH-PractitionerRole-1 | CareConnect-PractitionerRole-1 |
| DCH-ProfessionalComment-Communication-1 | CareConnect-Communication-1 |


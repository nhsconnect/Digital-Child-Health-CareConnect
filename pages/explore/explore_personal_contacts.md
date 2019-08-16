---
title: Personal Contacts Event Message Bundle
keywords:  messaging, bundles
tags: [fhir,messaging]
sidebar: foundations_sidebar
permalink: explore_personal_contacts.html
summary: "The FHIR profiles used for the Personal Contacts Event Message Bundle"
---

## FHIR Profiles ##

The following FHIR profiles are used to form the Personal Contacts Event Message Bundle:

- [Bundle](http://hl7.org/fhir/STU3/StructureDefinition/Bundle)
- [Event-MessageHeader-1](https://fhir.nhs.uk/STU3/StructureDefinition/Event-MessageHeader-1) - where the coding and display elements for the ‘event’ type are fixed to ‘personal-contacts-1 \| Personal Contacts’
- [CareConnect-Organization-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Organization-1)
- [CareConnect-HealthcareService-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-HealthcareService-1)
- [CareConnect-Patient-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Patient-1)
- [CareConnect-Encounter-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Encounter-1)
- [CareConnect-Location-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Location-1)
- [CareConnect-RelatedPerson-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-RelatedPerson-1)

## Bundle Structure

Specifies referencing within the Event Message Bundle.


<div style="text-align:center; margin-bottom:20px" >
	<a href="images/explore/dch-personalcontacts.png" target="_blank"><img src="images/explore/dch-personalcontacts.png"></a><br/>
	Personal Contacts <a href="images/explore/dch-personalcontacts.png" target="_blank">(open in new TAB)</a>
</div>

## Personal Contacts Event data item mapping to FHIR profiles ##

This Mapping table defines the FHIR elements that SHALL be used to encode the Healthy Child Event Specification data items for each DCH Event Message payload.  
Some common data item mappings, such as patient, publisher or Date/Time of event information, are defined within the [Header mapping table](explore_event_header_design.html) and SHALL be considered in parallel with the payload mapping.

The Child Health Event data items are fulfilled by elements within the FHIR resources listed below:

| DCH Data Item           | FHIR resource element                                          | Mandatory/<br/>Required/<br/>Optional  | Note                                          |
|-------------------------|----------------------------------------------------------------|----------------------------------------|-----------------------------------------------|
| Date/Time               | CareConnect-Encounter-1.period.start                       | Mandatory                              | Date/Time the personal contact was recorded.<br/>  Format: YYYY-MM-DD”T”HH:MM:SS   |
| First Given Name        | CareConnect-RelatedPerson-1.name.given                                 | Mandatory                   | The first forename or given name of the related or significant person. |
| Family Name             | CareConnect-RelatedPerson-1.name.family                                | Mandatory                   | That part of a person's name which is used to describe family, clan, tribal group, or marital association of the related or significant person.   |
| Contact Details         | CareConnect-RelatedPerson-1.address and/or CareConnect-RelatedPerson-1.telecom | Required                    | Contact details of the person (e.g. telephone number, email address etc.). |
| Relationship Type       | CareConnect-RelatedPerson-1.relationship                               | Mandatory                   | For Personal Contacts, the relationship type must be drawn from the given valueSet. |
| Household member        | CareConnect-RelatedPerson-1.householdMember - extension                | Required                    | For Personal Contacts, do not send the Household Member Description.*  |
| Parental Responsibility | CareConnect-RelatedPerson-1.parentalResponsibility - extension         | Required                    | Flag to indicate whether the related or significant person has parental responsibility.*  |
| Significant Individual  | CareConnect-RelatedPerson-1.significantIndividual - extension          | Required                    | Flag as to whether the people are deemed as key by family or Health Care Professional in the child's life that do not live in the home (s).*  |

*Only send these data items where the answer is "true" 
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
| event | 1..1 | Fixed Value: ‘personal-contacts-1 \| Personal Contacts’ |
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

### [CareConnect-RelatedPerson-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-RelatedPerson-1)

The CareConnect-RelatedPerson-1 resource included as part of the event message SHALL conform to the [CareConnect-RelatedPerson-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-RelatedPerson-1) constrained FHIR profile and the additional population guidance as per the table below:

| Resource Cardinality | 1..1 |

| Element | Cardinality | Additional Guidance |
| --- | --- | --- |
| patient | 1..1 | This will reference the patient resource representing the subject of this event |

#### Extension guidance
In line with the forthcoming Core approach, systems SHALL record relevant information using library extensions that extend the CareConnect profile:

Extension elements SHALL be added to the resource instance in this specified order, before any identifier element (if present) or patient reference.

##### **Extension:** [Household Member](https://fhir.nhs.uk/STU3/StructureDefinition/Extension-DCH-HouseholdMember-1)

Is the RelatedPerson a member of the same household as the Child?

| Resource Cardinality | 0..1 | Required |

| Element | Cardinality | Additional Guidance |
| --- | --- | --- |
| extension.url | 1..1 | Fixed Value: https://fhir.nhs.uk/STU3/StructureDefinition/Extension-DCH-HouseholdMember-1 |
| extension.extension.url | 1..1 | Fixed Value: householdMember |
| extension.extension.valueBoolean | 1..1 | true \| false |
| extension.extension.url | 0..1 | Fixed Value: householdMemberDescription |
| extension.extension.valueString | 0..1 | Description of household membership |


##### **Extension:** [Parental Responsibility](https://fhir.nhs.uk/STU3/StructureDefinition/Extension-DCH-ParentalResponsibility-1)

Does the RelatedPerson have parental responsibility for the Child?

| Resource Cardinality | 0..1 | Required |

| Element | Cardinality | Additional Guidance |
| --- | --- | --- |
| extension.url | 1..1 | Fixed Value: https://fhir.nhs.uk/STU3/StructureDefinition/Extension-DCH-ParentalResponsibility-1 |
| extension.valueBoolean | 1..1 | true \| false |

##### **Extension:** [Significant Individual](https://fhir.nhs.uk/STU3/StructureDefinition/Extension-DCH-SignificantIndividual-1)

Is the RelatedPerson deemed as a significant individual in the child's life by family or Health Care Professional, but not living in the same household.

| Resource Cardinality | 0..1 | Required |

| Element | Cardinality | Additional Guidance |
| --- | --- | --- |
| extension.url | 1..1 | Fixed Value: https://fhir.nhs.uk/STU3/StructureDefinition/Extension-DCH-SignificantIndividual-1 |
| extension.valueBoolean | 1..1 | true \| false |

## Personal Contacts Example ##

<script src="https://gist.github.com/IOPS-DEV/9f36511b8e3928a9be996c1ae8145213.js"></script>


## Profile Change Mappings for Personal Contacts ##

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
| DCH-RelatedPerson-1 | CareConnect-RelatedPerson-1 |


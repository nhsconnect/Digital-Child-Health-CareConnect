---
title: Feeding Status Event Message Bundle
keywords:  messaging, bundles
tags: [fhir,messaging]
sidebar: foundations_sidebar
permalink: explore_feeding_status.html
summary: "The FHIR profiles used for the Feeding Status Event Message Bundle"
---

## FHIR Profiles ##

The following FHIR profiles are used to form the Feeding Status Event Message Bundle:

- [Bundle](http://hl7.org/fhir/STU3/StructureDefinition/Bundle)
- [Event-MessageHeader-1](https://fhir.nhs.uk/STU3/StructureDefinition/Event-MessageHeader-1) - where the coding and display for the event element is fixed to '​feeding-status-1 \| ​Feeding Status  '
- [CareConnect-Organization-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Organization-1)
- [CareConnect-HealthcareService-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-HealthcareService-1)
- [CareConnect-Patient-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Patient-1)
- [CareConnect-Encounter-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Encounter-1)
- [CareConnect-Location-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Location-1)
- [CareConnect-QuestionnaireResponse-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-QuestionnaireResponse-1)

## Bundle Structure

Specifies referencing within the Event Message Bundle.

<div style="text-align:center; margin-bottom:20px" >
	<a href="images/explore/dch-feedingstatus.png" target="_blank"><img src="images/explore/dch-feedingstatus.png"></a><br/>
	Feeding Status <a href="images/explore/dch-feedingstatus.png" target="_blank">(open in new TAB)</a>
</div>

## Feeding Status Event data item mapping to FHIR profiles ##

This Mapping table defines the FHIR elements that SHALL be used to encode the Healthy Child Event Specification data items for each DCH Event Message payload.  
Some common data item mappings, such as patient, publisher or Date/Time of event information, are defined within the [Header mapping table](explore_event_header_design.html) and SHALL be considered in parallel with the payload mapping.

The Child Health Event data items are fulfilled by elements within the FHIR resources listed below:

| DCH Data Item            | FHIR resource element                                 | Mandatory/Required/Optional |
|--------------------------|-------------------------------------------------------|-----------------------------|
| Date                                         | CareConnect-Encounter-1.period.start or DCH-FeedingStatus-QuestionnaireResponse-1.authored | Mandatory                   |
| First Milk Feed                              | CareConnect-QuestionnaireResponse-1.item        | Required                    |
| Date and Time of First Milk Feed             | CareConnect-QuestionnaireResponse-1.item        | Required                    |
| Feeding Status of the baby                   | CareConnect-QuestionnaireResponse-1.item        | Required                    |
| Feeding method                               | CareConnect-QuestionnaireResponse-1.item        | Required                    |
| Introduction of Solids                       | CareConnect-QuestionnaireResponse-1.item        | Required                    |
| Approximate Date breastfeeding stopped       | CareConnect-QuestionnaireResponse-1.item        | Required                    |
| Feeding Concerns                             | CareConnect-QuestionnaireResponse-1.item        | Optional                    |


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
| event | 1..1 | Fixed Value: "​feeding-status-1 \| ​Feeding Status" |
| responsible | 1..1 | This will reference the responsible Organization resource |
| focus | 1..1 | This will reference the CareConnect-Encounter-1 resource which contains information relating to the event message. |

### [CareConnect-Organization-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Organization-1)

The CareConnect-Organization-1 resource included as part of the event message SHALL conform to the [CareConnect-Organization-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Organization-1) constrained FHIR profile and the additional population guidance as per the table below:

| Resource Cardinality | 1..* |

| Element | Cardinality | Additional Guidance |
| --- | --- | --- |
| identifier.system | 1..1 | Fixed value: https://fhir.nhs.uk/Id/ods-organization-code |
| identifier.system | 1..1 | Organisation’s ODS Organization Code |
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
| QuestionnaireResponse.subject | 1..1 | QuestionnaireResponse.subject SHALL reference the subject Patient resource |
| QuestionnaireResponse.context | 1..1 | QuestionnaireResponse.context SHALL reference the Encounter resource |
| QuestionnaireResponse.author | 1..1 | QuestionnaireResponse.author SHALL reference the authoring Practitioner resource |
| item (firstMilkFeed) |
| QuestionnaireResponse.item (firstMilkFeed) | 0..1 | |
| QuestionnaireResponse.item (firstMilkFeed).linkId | 1..1 | Fixed Value: firstMilkFeed |
| QuestionnaireResponse.item (firstMilkFeed).text | 1..1 | Fixed Value: First Milk Feed |
| QuestionnaireResponse.item (firstMilkFeed).answer | 1..1 | |
| QuestionnaireResponse.item (firstMilkFeed).answer.valueCoding | 1..1 | QuestionnaireResponse.item (firstMilkFeed).answer.valueCoding SHALL use a value from https://fhir.nhs.uk/STU3/ValueSet/DCH-FirstMilkFeed-1 |
| item (firstMilkFeedDateTime) |
| QuestionnaireResponse.item (firstMilkFeedDateTime) | 0..1 | |
| QuestionnaireResponse.item (firstMilkFeedDateTime).linkId | 1..1 | Fixed Value: firstMilkFeedDateTime |
| QuestionnaireResponse.item (firstMilkFeedDateTime).text | 1..1 | Fixed Value: Date and Time of First Milk Feed |
| QuestionnaireResponse.item (firstMilkFeedDateTime).answer | 1..1 | |
| QuestionnaireResponse.item (firstMilkFeedDateTime).answer.valueDateTime | 1..1 | |
| item (feedingStatus) |
| QuestionnaireResponse.item (feedingStatus) | 0..1 | |
| QuestionnaireResponse.item (feedingStatus).linkId | 1..1 | Fixed Value: feedingStatus |
| QuestionnaireResponse.item (feedingStatus).text | 1..1 | Fixed Value: Feeding Status of the baby |
| QuestionnaireResponse.item (feedingStatus).answer | 1..1 | |
| QuestionnaireResponse.item (feedingStatus).answer.valueCoding | 1..1 | QuestionnaireResponse.item (feedingStatus).answer.valueCoding SHALL use a value from ttps://fhir.nhs.uk/STU3/ValueSet/DCH-FeedingStatus-1 |
| item (feedingMethod) |
| QuestionnaireResponse.item (feedingMethod) | 0..1 | |
| QuestionnaireResponse.item (feedingMethod).linkId | 1..1 | Fixed Value: feedingMethod |
| QuestionnaireResponse.item (feedingMethod).text | 1..1 | Fixed Value: Feeding Method |
| QuestionnaireResponse.item (feedingMethod).answer | 1..1 | |
| QuestionnaireResponse.item (feedingMethod).answer.valueCoding | 1..1 | QuestionnaireResponse.item (feedingMethod).answer.valueCoding SHOULD use a value from https://fhir.nhs.uk/STU3/ValueSet/DCH-FeedingMethod-1 |
| item (introductionOfSolids) |
| QuestionnaireResponse.item (introductionOfSolids) | 0..1 | |
| QuestionnaireResponse.item (introductionOfSolids).linkId | 1..1 | Fixed Value: introductionOfSolids |
| QuestionnaireResponse.item (introductionOfSolids).text | 1..1 | Fixed Value: Introduction of Solids |
| QuestionnaireResponse.item (introductionOfSolids).answer | 1..1 | |
| QuestionnaireResponse.item (introductionOfSolids).answer.valueDateTime | 1..1 | |
| item (approximateDateBreastfeedingStopped) |
| QuestionnaireResponse.item (approximateDateBreastfeedingStopped) | 0..1 | |
| QuestionnaireResponse.item (approximateDateBreastfeedingStopped).linkId | 1..1 | Fixed Value: approximateDateBreastfeedingStopped |
| QuestionnaireResponse.item (approximateDateBreastfeedingStopped).text | 1..1 | Fixed Value: Date of last breast milk feed to the nearest month and year |
| QuestionnaireResponse.item (approximateDateBreastfeedingStopped).answer | 1..1 | |
| QuestionnaireResponse.item (approximateDateBreastfeedingStopped).answer.valueDateTime | 1..1 | |
| item (feedingConcerns) |
| QuestionnaireResponse.item (feedingConcerns) | 0..1 | |
| QuestionnaireResponse.item (feedingConcerns).linkId | 1..1 | Fixed Value: feedingConcerns |
| QuestionnaireResponse.item (feedingConcerns).text | 1..1 | Fixed Value: Feeding Concerns |
| QuestionnaireResponse.item (feedingConcerns).answer | 1..1 | |
| QuestionnaireResponse.item (feedingConcerns).answer.valueString | 1..1 | |



## Feeding Status Example ##

<script src="https://gist.github.com/IOPS-DEV/69575e294644491509b2c244926e9966.js"></script>


## Profile Change Mappings for Feeding Status ##

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
| DCH-FeedingStatus-QuestionnaireResponse-1 | CareConnect-QuestionnaireResponse-1 |


---
title: Referral Event Message Bundle
keywords:  messaging, bundles
tags: [fhir,messaging]
sidebar: foundations_sidebar
permalink: explore_referral.html
summary: "The FHIR profiles used for the Referral Event Message Bundle"
---

## FHIR Profiles ##

The following FHIR profiles are used to form the Referral Event Message Bundle:

- [Bundle](http://hl7.org/fhir/STU3/StructureDefinition/Bundle)
- [Event-MessageHeader-1](https://fhir.nhs.uk/STU3/StructureDefinition/Event-MessageHeader-1) - where the coding and display elements for the ‘event’ type are fixed to ‘​referral-1 \| Referral’
- [CareConnect-Organization-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Organization-1)
- [CareConnect-HealthcareService-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-HealthcareService-1)
- [CareConnect-Patient-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Patient-1)
- [CareConnect-Encounter-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Encounter-1)
- [CareConnect-Location-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Location-1)
- [CareConnect-Practitioner-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Practitioner-1)
- [CareConnect-PractitionerRole-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-PractitionerRole-1)
- [CareConnect-ReferralRequest-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-ReferralRequest-1)

## Bundle Structure

Specifies referencing within the Event Message Bundle.


<div style="text-align:center; margin-bottom:20px" >
	<a href="images/explore/dch-referral.png" target="_blank"><img src="images/explore/dch-referral.png"></a><br/>
	Referral <a href="images/explore/dch-referral.png" target="_blank">(open in new TAB)</a>
</div>

## Referral Event data item mapping to FHIR profiles ##

This Mapping table defines the FHIR elements that SHALL be used to encode the Healthy Child Event Specification data items for each DCH Event Message payload.  
Some common data item mappings, such as patient, publisher or Date/Time of event information, are defined within the [Header mapping table](explore_event_header_design.html) and SHALL be considered in parallel with the payload mapping.

The Child Health Event data items are fulfilled by elements within the FHIR resources listed below:

| DCH Data Item                | FHIR resource element                                               | Mandatory/Required/Optional | Note     |
|------------------------------|---------------------------------------------------------------------|-----------------------------|----------|
| Date/Time of Referral        | CareConnect-ReferralRequest-1.authoredOn                                    | Mandatory                   |          |
| ODS/ORD Site Code            | CareConnect-Location-1.identifier (ODS/ORD Site Code)               | Required                    |          |
| Performing Professional      | CareConnect-Practitioner-1.name                                 | Required                    |          |
| SDS Job Role Name            | CareConnect-PractitionerRole-1.code (SDS Job Role Name)         | Required                    |          |
| Service Referred to          | CareConnect-ReferralRequest-1.serviceRequested                              | Mandatory                   |          |
| Source of Referral           | CareConnect-ReferralRequest-1.sourceOfReferral (extension)                  | Required                    |          |
| Urgency                      | CareConnect-ReferralRequest-1.priority                                      | Required                    | **\***   |
| Reason for Referral          | CareConnect-ReferralRequest-1.reasonCode                                    | Mandatory                   |          |
| Comment                      | CareConnect-ReferralRequest-1.note                                          | Optional                    |          |

**\*** Note that there is a mandatory FHIR valueSet for ReferralRequest.priority. The NHS Data Dictionary Priority Type valueSet has been mapped on to the mandated FHIR valueSet in the following way:

| FHIR request-priority          | NHS Data Dictionary Priority Type           |
|--------------------------------|---------------------------------------------|
| routine - Routine              | 1 - Routine                                 |
| urgent - Urgent                | 2 - Urgent                                  |
| asap - ASAP                    | 3 - Two Week Wait                           |



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
| event | 1..1 | Fixed Value: ‘​referral-1 \| Referral’ |
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
| PractitionerRole.code(keyWorkerStatus) | 1..1 | PractitionerRole.code(keyWorkerStatus) SHALL use a value from https://fhir.nhs.uk/STU3/ValueSet/DCH-KeyWorkerStatus-1 |
| PractitionerRole.specialty | 1..1 | PractitionerRole.specialty SHALL use a value from https://fhir.nhs.uk/STU3/ValueSet/DCH-Specialty-1 |


### [CareConnect-ReferralRequest-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-ReferralRequest-1)

The CareConnect-ReferralRequest-1 resource included as part of the event message SHALL conform to the [CareConnect-ReferralRequest-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-ReferralRequest-1) constrained FHIR profile and the additional population guidance as per the table below:

| Resource Cardinality | 1..1 |

| Element | Cardinality | Additional Guidance |
| --- | --- | --- |
| intent | 1..1 | Fixed Value: proposal |
| serviceRequested | 1..1 | ReferralRequest.serviceRequested SHOULD use a value from https://fhir.nhs.uk/STU3/ValueSet/DCH-ServiceReferredTo-1 |
| subject | 1..1 | This will reference the patient resource representing the subject of this event |
| context | 1..1 | This will reference the encounter resource representing the context of this event |
| authoredOn | 1..1 | |
| requester | 0..1 | Required |
| requester.agent | 1..1 | This will reference the referring practitioner resource |
| requester.onBehalfOf | 1..1 | This will reference the organization resource the agent is acting for |
| reasonCode | 1..1 | ReferralRequest.reasonCode SHOULD use a value from  https://fhir.nhs.uk/STU3/ValueSet/DCH-ReasonForReferral-1 |


#### Extension guidance
In line with the forthcoming Core approach, systems SHALL record relevant information using library extensions that extend the CareConnect profile:


##### **Extension:** [Referral Request Method](https://fhir.nhs.uk/STU3/StructureDefinition/Extension-DCH-ReferralRequestMethod-1)

By what channel is the referral received?

| Resource Cardinality | 0..1 | Required |

| Element | Cardinality | Additional Guidance |
| --- | --- | --- |
| extension.url | 1..1 | Fixed Value: https://fhir.nhs.uk/STU3/StructureDefinition/Extension-DCH-ReferralRequestMethod-1 |
| extension.valueCodeableConcept | 1..1 | extension.valueCodeableConcept SHALL take a value from https://fhir.nhs.uk/STU3/ValueSet/DCH-ReferralRequestMethod-1  |

##### **Extension:** [Source Of Referral](https://fhir.nhs.uk/STU3/StructureDefinition/Extension-DCH-SourceOfReferral-1)

What is the referral source?

| Resource Cardinality | 0..1 | Required |

| Element | Cardinality | Additional Guidance |
| --- | --- | --- |
| extension.url | 1..1 | Fixed Value: https://fhir.nhs.uk/STU3/StructureDefinition/Extension-DCH-SourceOfReferral-1 |
| extension.valueCodeableConcept | 1..1 | extension.valueCodeableConcept SHALL take a value from https://fhir.nhs.uk/STU3/ValueSet/DCH-SourceOfReferral-1 |

## Referral Example ##

<script src="https://gist.github.com/IOPS-DEV/3a7f3bd433e15ce699c066981c3fe195.js"></script>


## Profile Change Mappings for Referral ##

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
| DCH-ReferralRequest-1 | CareConnect-ReferralRequest-1 |

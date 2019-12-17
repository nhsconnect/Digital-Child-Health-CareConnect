---
title: Professional Contacts Event Message Bundle
keywords:  messaging, bundles
tags: [fhir,messaging]
sidebar: foundations_sidebar
permalink: explore_professional_contacts.html
summary: "The FHIR profiles used for the Professional Contacts Event Message Bundle"
---
## FHIR Profiles ##

The following FHIR profiles are used to form the Professional Contacts Event Message Bundle:

- [Bundle](http://hl7.org/fhir/STU3/StructureDefinition/Bundle)
- [Event-MessageHeader-1](https://fhir.nhs.uk/STU3/StructureDefinition/Event-MessageHeader-1) - where the coding and display elements for the ‘event’ type are fixed to "​professional-contacts-1 \| ​Professional Contacts"
- [CareConnect-Organization-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Organization-1)
- [CareConnect-HealthcareService-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-HealthcareService-1)
- [CareConnect-Patient-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Patient-1)
- [CareConnect-Encounter-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Encounter-1)
- [CareConnect-Location-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Location-1)
- [CareConnect-EpisodeOfCare-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-EpisodeOfCare-1)
Then for Professional Contacts (Team) Event
- [CareConnect-CareTeam-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-CareTeam-1)
Or for Professional Contacts (Professional) Event
- [CareConnect-Practitioner-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Practitioner-1)
- [CareConnect-PractitionerRole-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-PractitionerRole-1)

## Bundle Structure


Specifies referencing within the Event Message Bundle.

<div style="text-align:center; margin-bottom:20px" >
	<a href="images/explore/dch-professionalcontacts2professional.png" target="_blank"><img src="images/explore/dch-professionalcontacts2professional.png"></a><br/>
	Professional Contacts (Professional)<a href="images/explore/dch-professionalcontacts2professional.png" target="_blank">(open in new TAB)</a>
</div>

<div style="text-align:center; margin-bottom:20px" >
	<a href="images/explore/dch-professionalcontacts1team.png" target="_blank"><img src="images/explore/dch-professionalcontacts1team.png"></a><br/>
	Professional Contacts (Team)<a href="images/explore/dch-professionalcontacts1team.png" target="_blank">(open in new TAB)</a>
</div>

## Professional Contacts Event data item mapping to FHIR profiles ##

This Mapping table defines the FHIR elements that SHALL be used to encode the Healthy Child Event Specification data items for each DCH Event Message payload.  
Some common data item mappings, such as patient, publisher or Date/Time of event information, are defined within the [Header mapping table](explore_event_header_design.html) and SHALL be considered in parallel with the payload mapping.

The Child Health Event data items are fulfilled by elements within the FHIR resources listed below:

| DCH Data Item                 | FHIR resource element                                                                            | Mandatory/Required/Optional |
|-------------------------------|--------------------------------------------------------------------------------------------------|-----------------------------|
| Organisation                  | CareConnect-Organization-1.identifier (ODS Code or ODS Site Code)                       | Mandatory                    |
| Team                          | CareConnect-CareTeam-1.name                                                         | Required                   |
| Role                          | CareConnect-CareTeam-1.participant.role                                      | Required                   |
| Name                          | CareConnect-Practitioner-1.name                                                     | Optional                    |
| Role                          | CareConnect-PractitionerRole-1.code (careProfessionalType)                          | Optional                  |
| Specialty                     | CareConnect-PractitionerRole-1.specialty                                            | Optional |
| Key Worker                    | CareConnect-PractitionerRole-1.code (keyWorker)                                     | Optional |
| Care Professional Association | CareConnect-EpisodeOfCare-1.type                                                                         | Mandatory                   |
| Contact details               | CareConnect-Organization-1.telecom                                                              | Required                    |
| Start date                    | CareConnect-EpisodeOfCare-1.period.start                                                                 | Required                   |
| End date                      | CareConnect-EpisodeOfCare-1.period.end                                                                   | Required                   |
| Reason                        | CareConnect-EpisodeOfCare-1.type.text                                                                   | Optional                   |


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


### [CareConnect-EpisodeOfCare-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-EpisodeOfCare-1)

The CareConnect-EpisodeOfCare-1 resource included as part of the event message SHALL conform to the [CareConnect-EpisodeOfCare-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-EpisodeOfCare-1) constrained FHIR profile and the additional population guidance as per the table below:

| Resource Cardinality | 1..1 |

| Element | Cardinality | Additional Guidance |
| --- | --- | --- |
| type | 1..1 | type SHALL use a value from https://fhir.nhs.uk/STU3/ValueSet/DCH-AssociationType-1 |
| type.text | 0..1 | type.text MAY record the reason for relationship |
| patient | 1..1 | This will reference the Patient resource representing the subject of the event |
| careManager | 0/1..1 | If Professional event, this SHALL reference the Practitioner resource |
| team        | 0/1..1 | If Team event, this SHALL reference the CareTeam resource |
| managingOrganization | 1..1 | This will reference the managing Organization resource |

### [CareConnect-CareTeam-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-CareTeam-1)

The CareConnect-CareTeam-1 resource included as part of the event message SHALL conform to the [CareConnect-CareTeam-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-CareTeam-1) constrained FHIR profile and the additional population guidance as per the table below:

| Resource Cardinality | 1..1 | If Team event |

| Element | Cardinality | Additional Guidance |
| --- | --- | --- |
| subject | 1..1 | This will reference the Patient resource representing the subject of the event |
| context | 1..1 | This will reference the Encounter resource representing the contect |
| participant.role | 1..1 | participant.role SHOULD take a value from https://fhir.nhs.uk/STU3/ValueSet/DCH-ProfessionalType-1
| managingOrganization | 1..1 | This will reference the managing Organization resource |


### [CareConnect-Practitioner-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Practitioner-1)

The CareConnect-Practitioner-1 resource included as part of the event message SHALL conform to the [CareConnect-Practitioner-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Practitioner-1) constrained FHIR profile and the additional population guidance as per the table below:

| Resource Cardinality | 1..1 | If Professional event |


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



## Professional Contacts Professional Example ##

<script src="https://gist.github.com/IOPS-DEV/92016f8c3f7c882112a4850e3d109c34.js"></script>

## Professional Contacts Team Example ##

<script src="https://gist.github.com/IOPS-DEV/e81780340604f6f383c965f2b98210b4.js"></script>


## Profile Change Mappings for Professional Contacts ##

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
| DCH-ProfessionalContact-EpisodeOfCare-1 | CareConnect-EpisodeOfCare-1 |
| **for Professional Contacts (Team) Event** |
| DCH-CareTeam-1 | CareConnect-CareTeam-1 |
| **for Professional Contacts (Professional) Event** |
| CareConnect-DCH-Practitioner-1 | CareConnect-Practitioner-1 |
| CareConnect-DCH-PractitionerRole-1 | CareConnect-PractitionerRole-1 |


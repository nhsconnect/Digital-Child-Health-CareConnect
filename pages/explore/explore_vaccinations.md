---
title: Vaccinations Event Message Bundle
keywords:  messaging, bundles
tags: [fhir,messaging]
sidebar: foundations_sidebar
permalink: explore_vaccination_administration.html
summary: "The FHIR profiles used for the Vaccinations Event Message Bundle"
---

## FHIR Profiles ##

The following FHIR profiles are used to form the Vaccinations Event Message Bundle:

- [Bundle](http://hl7.org/fhir/STU3/StructureDefinition/Bundle)
- [Event-MessageHeader-1](https://fhir.nhs.uk/STU3/StructureDefinition/Event-MessageHeader-1) - where the coding and display for the event element is fixed to '​vaccinations-1 \| Vaccinations  '
- [CareConnect-Organization-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Organization-1)
- [CareConnect-HealthcareService-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-HealthcareService-1)
- [CareConnect-Patient-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Patient-1)
- [CareConnect-Encounter-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Encounter-1)
- [CareConnect-Location-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Location-1)
- [CareConnect-Practitioner-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Practitioner-1)
- [CareConnect-PractitionerRole-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-PractitionerRole-1)
- [CareConnect-Immunization-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Immunization-1)

## Bundle Structure

Specifies referencing within the Event Message Bundle.

<div style="text-align:center; margin-bottom:20px" >
	<a href="images/explore/dch-vaccinations.png" target="_blank"><img src="images/explore/dch-vaccinations.png"></a><br/>
	Vaccinations <a href="images/explore/dch-vaccinations.png" target="_blank">(open in new TAB)</a>
</div>

## Vaccinations Event data item mapping to FHIR profiles ##

This Mapping table defines the FHIR elements that SHALL be used to encode the Healthy Child Event Specification data items for each DCH Event Message payload.  
Some common data item mappings, such as patient, publisher or Date/Time of event information, are defined within the [Header mapping table](explore_event_header_design.html) and SHALL be considered in parallel with the payload mapping.

The Child Health Event data items are fulfilled by elements within the FHIR resources listed below:

| DCH Data Item            | FHIR resource element                                 | Mandatory/Required/Optional |
|--------------------------|-------------------------------------------------------|-----------------------------|
| Date/Time                   | CareConnect-Encounter-1.period.start                            | Mandatory                              | The date on which the vaccination intervention was carried out or was meant to be administered or was reported to a health professional.  Format is YYYY-MM-DD”T”HH:MM:SS                    |
| ODS/ORD Site code           | CareConnect-Location-1.identifier (ODS Site Code)                   | Required                               |                         |
| Performing Professional     | CareConnect-Practitioner-1.name                                 | Required                               |                         |
| SDS Job Role Name           | CareConnect-PractitionerRole-1.code (SDS Job Role Name)         | Required                               |                         |
| Reported Date            	  | CareConnect-Immunization-1.date                                 | Required                               | The date or partial date that the vaccine was administered, or reported vaccination was given in the opinion of the child and/or parent carer                        | 
| Primary Source              | CareConnect-Immunization-1.primarySource                        | Mandatory                              | Boolean (FALSE (if reported)/True                        |
| Report Origin               | CareConnect-Immunization-1.reportOrigin                         | Required                               |                         |
| Vaccination Procedure       | CareConnect-Immunization-1.extension:vaccinationProcedure       | Required                               | Free text field to be used if no coded text available using vaccinationProcedure.coding.text                        |
| Vaccination Situation (Not Given Outcome)       | CareConnect-Immunization-1.explanation.reasonNotGiven | Required                     |                         |
| Not Given flag              | CareConnect-Immunization-1.notGiven                             | Mandatory                              | Boolean (FALSE (given or reported as given)/TRUE (not given)                 |
| Dose sequence               | CareConnect-Immunization-1.vaccinationProtocol.doseSequence     | Required                               | Note, if the vaccination protocol is not present, then the dose sequence is not present either.|
| Vaccine Product             | CareConnect-Immunization-1.vaccineCode.coding.code              | Required                               | DM+D [SNOMED UK drug extension](https://www.nhsbsa.nhs.uk/pharmacies-gp-practices-and-appliance-contractors/dictionary-medicines-and-devices-dmd)                         |
| Vaccine Manufacturer        | CareConnect-Immunization-1.manufacturer                         | Required                               |                         |
| Batch Number                | CareConnect-Immunization-1.lotNumber                            | Optional                               | Derived from FMD code   |
| Site of Vaccination         | CareConnect-Immunization-1.site                                 | Required                               |                         |
| Route of Vaccination        | CareConnect-Immunization-1.route                                | Required                               |                         |
| Dose Amount                 | CareConnect-Immunization-1.doseQuantity                         | Optional                               |                         |
| Indication                  | CareConnect-Immunization-1.explanation.reason                   | Optional                               | Free text field to be used if no coded text available using reason.coding.text    |

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
| event | 1..1 | Fixed Value: "​vaccinations-1 \| Vaccinations" |
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

### [CareConnect-Practitioner-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Practitioner-1)

The CareConnect-Practitioner-1 resource included as part of the event message SHALL conform to the [CareConnect-Practitioner-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Practitioner-1) constrained FHIR profile and the additional population guidance as per the table below:

| Resource Cardinality | TBC |


### [CareConnect-PractitionerRole-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-PractitionerRole-1)

The CareConnect-PractitionerRole-1 resource included as part of the event message SHALL conform to the [CareConnect-PractitionerRole-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-PractitionerRole-1) constrained FHIR profile and the additional population guidance as per the table below:

| Resource Cardinality | TBC |

| Element | Cardinality | Additional Guidance |
| --- | --- | --- |
| organization | 1..1 | This will reference the Organization resource responsible for the event |
| practitioner | 1..1 | This will reference the Practitioner resource responsible for the event |
| PractitionerRole.code(careProfessionalType) | 1..1 | PractitionerRole.code(careProfessionalType) SHALL use a value from https://fhir.nhs.uk/STU3/ValueSet/DCH-ProfessionalType-1 |
| PractitionerRole.code(keyWorkerStatus) | 1..1 | PractitionerRole.code(keyWorkerStatus) SHALL use a value from https://fhir.nhs.uk/STU3/ValueSet/DCH-KeyWorkerStatus-1 |
| PractitionerRole.specialty | 1..1 | PractitionerRole.specialty SHALL use a value from https://fhir.nhs.uk/STU3/ValueSet/DCH-Specialty-1 |


### [CareConnect-Immunization-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Immunization-1)

The CareConnect-Immunization-1 resource included as part of the event message SHALL conform to the [CareConnect-Immunization-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Immunization-1) constrained FHIR profile and the additional population guidance as per the table below:

| Resource Cardinality | TBC |

| Element | Cardinality | Additional Guidance |
| --- | --- | --- |
| Immunization.extension(vaccinationProcedure) | 1..1 |  |
| Immunization.extension(vaccinationProcedure).valueCodeableConcept | 1..1 | Immunization.extension(vaccinationProcedure).valueCodeableConcept SHALL use a value from https://fhir.hl7.org.uk/STU3/ValueSet/CareConnect-VaccinationProcedure-1 |
| Immunization.status | 1..1 | Fixed Value: completed |
| Immunization.notGiven | 1..1 | Fixed Value: false |
| Immunization.vaccineCode | 1..1 | Immunization.vaccineCode SHALL use a value from  https://fhir.hl7.org.uk/STU3/ValueSet/CareConnect-VaccineCode-1 |



## Vaccinations Example ##

<script src="https://gist.github.com/IOPS-DEV/e9631f36c9a6585f00c78464a6defc0a.js"></script>


## Profile Change Mappings for Vaccinations ##

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
| CareConnect-DCH-Immunization-1 | CareConnect-Immunization-1 |

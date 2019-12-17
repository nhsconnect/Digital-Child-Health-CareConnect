---
title: Birth Details Event Message Bundle
keywords:  messaging, bundles
tags: [fhir,messaging]
sidebar: foundations_sidebar
permalink: explore_birth_details.html
summary: "The FHIR profiles used for the Birth Details Event Message Bundle"
---

## FHIR Profiles ##

The following FHIR profiles are used to form the Birth Details Event Message Bundle:

- [Bundle](http://hl7.org/fhir/STU3/StructureDefinition/Bundle)
- [Event-MessageHeader-1](https://fhir.nhs.uk/STU3/StructureDefinition/Event-MessageHeader-1) - where the coding and display for the event element is fixed to '​birth-details-1 \| ​Birth Details  '
- [CareConnect-Organization-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Organization-1)
- [CareConnect-HealthcareService-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-HealthcareService-1)
- [CareConnect-Patient-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Patient-1)
- [CareConnect-Encounter-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Encounter-1)
- [CareConnect-Location-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Location-1)
- [CareConnect-Condition-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Condition-1)
- [CareConnect-Observation-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Observation-1)
- [CareConnect-Procedure-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Procedure-1)

## Bundle Structure

Specifies referencing within the Event Message Bundle.

<div style="text-align:center; margin-bottom:20px" >
	<a href="images/explore/dch-birthdetails1.png" target="_blank"><img src="images/explore/dch-birthdetails1.png"></a><br/>
	Birth Details <a href="images/explore/dch-birthdetails1.png" target="_blank">(open in new TAB)</a>
	<a href="images/explore/dch-birthdetails2.png" target="_blank"><img src="images/explore/dch-birthdetails2.png"></a><br/>
	Birth Details <a href="images/explore/dch-birthdetails2.png" target="_blank">(open in new TAB)</a>
</div>

## Birth Details Event data item mapping to FHIR profiles ##

This Mapping table defines the FHIR elements that SHALL be used to encode the Healthy Child Event Specification data items for each DCH Event Message payload.  
Some common data item mappings, such as patient, publisher or Date/Time of event information, are defined within the [Header mapping table](explore_event_header_design.html) and SHALL be considered in parallel with the payload mapping.

The Child Health Event data items are fulfilled by elements within the FHIR resources listed below:

| DCH Data Item            | FHIR resource element                                 | Mandatory/Required/Optional |
|--------------------------|-------------------------------------------------------|-----------------------------|
| Location of Birth                   | CareConnect-Location-1.identifier (ODS Site Code)           | Mandatory                   |
| Delivery Place Type Code            | CareConnect-Location-1.identifier (ODS Site Code)          | Mandatory                   |
| Birth Order                         | CareConnect-Patient-1.multipleBirthInteger                     | Mandatory                   |
| Length of Gestation at Birth        | CareConnect-Observation-1.valueQuantity           | Mandatory                   |
| Number of Births in confinement     | CareConnect-Observation-1.valueQuantity                  | Mandatory                    |
| Problems during Delivery            | CareConnect-Condition-1.code                          | Required                    |
| Physical Problems detected at Birth | CareConnect-Condition-1.code            | Required                    |
| Neonatal Resuscitation Method       | CareConnect-Procedure-1.code                           | Required                 |
| Date and Time of Birth              | CareConnect-Patient-1.birthDate (with patient-BirthTime extension)                           | Mandatory                 |
| Type of Delivery                    | CareConnect-1.code   | Mandatory                    |
| Attempted Type of Delivery          | CareConnect-Condition-1.code   | Required                    |
| Onset of Spontaneous Respiration    | CareConnect-Observation-1.component  | Required                    |
| APGAR Score (1 Minute)              | CareConnect-Observation-1.valueQuantity                 | Mandatory                   |
| APGAR Score (5 Minute)              | CareConnect-Observation-1.valueQuantity                  | Mandatory                   |
| APGAR Score (10 Minute)             | CareConnect-Observation-1.valueQuantity                | Required                    |
| Put To Breast                       | CareConnect-Observation-1.code                  | Required                    |


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
| event | 1..1 | Fixed Value: "​birth-details-1 \| ​Birth Details" |
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

| Resource Cardinality | TBC |


### [CareConnect-PractitionerRole-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-PractitionerRole-1)

The CareConnect-PractitionerRole-1 resource included as part of the event message SHALL conform to the [CareConnect-PractitionerRole-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-PractitionerRole-1) constrained FHIR profile and the additional population guidance as per the table below:

| Resource Cardinality | TBC |

| Element | Cardinality | Additional Guidance |
| --- | --- | --- |
| organization | 1..1 | This will reference the Organization resource responsible for the event |
| practitioner | 1..1 | This will reference the Practitioner resource responsible for the event |
| PractitionerRole.code(careProfessionalType) | 1..1 | PractitionerRole.code(careProfessionalType) SHALL use a value from https://fhir.nhs.uk/STU3/ValueSet/DCH-ProfessionalType-1 |
| PractitionerRole.code(keyWorkerStatus) | 0..1 | If Practitioner is a key worker, PractitionerRole.codekeyWorkerStatus SHALL use a value from https://fhir.nhs.uk/STU3/ValueSet/DCH-KeyWorkerStatus-1 |
| PractitionerRole.specialty | 1..1 | PractitionerRole.specialty SHALL use a value from https://fhir.nhs.uk/STU3/ValueSet/DCH-Specialty-1 |



### [CareConnect-Condition-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Condition-1)

The CareConnect-Condition-1 resource included as part of the event message SHALL conform to the [CareConnect-Condition-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Condition-1) constrained FHIR profile and the additional population guidance as per the table below:

| Resource Cardinality | TBC |

| Element | Cardinality | Additional Guidance |
| --- | --- | --- |
| subject | 1..1 | This will reference the patient resource representing the subject of this event |
| context | 1..1 | This will reference the encounter resource representing the context of this event |

For each of the Condition resources representing Birth Detail conditions:

#### CareConnect-Condition-1 (PhysicalProblemAtBirth)

| Element | Cardinality | Additional Guidance |
| --- | --- | --- |
| Condition.category | 1..1 | Condition.category SHOULD use a value from https://fhir.hl7.org.uk/STU3/ValueSet/CareConnect-ConditionCategory-1 |
| Condition.code | 1..1 | Condition.code SHOULD use a value from https://fhir.nhs.uk/STU3/ValueSet/DCH-PhysicalProblemAtBirth-1 |


#### CareConnect-Condition-1 (ProblemDuringDelivery)

| Element | Cardinality | Additional Guidance |
| --- | --- | --- |
| Condition.category | 1..1 | Condition.category SHOULD use a value from https://fhir.hl7.org.uk/STU3/ValueSet/CareConnect-ConditionCategory-1 |
| Condition.code | 1..1 | Condition.code SHOULD use a value from https://fhir.nhs.uk/STU3/ValueSet/DCH-ProblemDuringDelivery-1 |


#### CareConnect-Condition-1 (AttemptedDeliveryType)

| Element | Cardinality | Additional Guidance |
| --- | --- | --- |
| Condition.category | 1..1 | Condition.category SHOULD use a value from https://fhir.hl7.org.uk/STU3/ValueSet/CareConnect-ConditionCategory-1 |
| Condition.code | 1..1 | Condition.code SHOULD use a value from https://fhir.nhs.uk/STU3/ValueSet/DCH-AttemptedDeliveryType-1 |


### [CareConnect-Observation-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Observation-1)

The CareConnect-Observation-1 resource included as part of the event message SHALL conform to the [CareConnect-Observation-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Observation-1) constrained FHIR profile and the additional population guidance as per the table below:

| Resource Cardinality | TBC |

| Element | Cardinality | Additional Guidance |
| --- | --- | --- |
| subject | 1..1 | This will reference the patient resource representing the subject of this event |
| context | 1..1 | This will reference the encounter resource representing the context of this event |

For each of the Observation resources representing Birth Detail observations:

#### CareConnect-Observation-1 (APGARScore)

| Element | Cardinality | Additional Guidance |
| --- | --- | --- |
| Observation.code | 1..1 | Observation.code SHALL use a value from https://fhir.nhs.uk/STU3/ValueSet/DCH-APGARScoreObservation-1 |
| Observation.valueQuantity | 1..1 | Numeric value for APGAR Score |


#### CareConnect-Observation-1 (LengthOfGestation)

| Element | Cardinality | Additional Guidance |
| --- | --- | --- |
| Observation.code | 1..1 |  |
| Observation.code.coding .system | 1..1 | Fixed Value: http://snomed.info/sct |
| Observation.code.coding.code | 1..1 | Fixed Value: 412726003 |
| Observation.code.coding.display | 1..1 | Fixed Value: Length of gestation at birth |
| Observation.component | 2..2 |  |
| Observation.component.code.coding .system | 1..1 | Fixed Value: http://snomed.info/sct |
| Observation.component.code.coding.code | 1..1 | Fixed Value: 258705008 |
| Observation.component.code.coding.display | 1..1 | Fixed Value: weeks |
| Observation.component.valueQuantity | 1..1 | Number of weeks applicable to the length of gestation observation, expressed in n2 format |
| Observation.component.code.coding .system | 1..1 | Fixed Value: http://snomed.info/sct |
| Observation.component.code.coding.code | 1..1 | Fixed Value: 258703001 |
| Observation.component.code.coding.display | 1..1 | Fixed Value: days |
| Observation.component.valueQuantity | 1..1 | Number of days applicable to the length of gestation observation, expressed in n1 format |


#### CareConnect-Observation-1 (NumberOfBirths)

| Element | Cardinality | Additional Guidance |
| --- | --- | --- |
| Observation.code | 1..1 |  |
| Observation.code.coding .system | 1..1 | Fixed Value: http://snomed.info/sct |
| Observation.code.coding.code | 1..1 | Fixed Value: 382341000000101 |
| Observation.code.coding.display | 1..1 | Fixed Value: Total number of registerable births at delivery |
| Observation.valueQuantity | 1..1 | Numerical value |


#### CareConnect-Observation-1 (SpontaneousRespirationOnset)

| Element | Cardinality | Additional Guidance |
| --- | --- | --- |
| Observation.code | 1..1 |  |
| Observation.code.coding .system | 1..1 | Fixed Value: http://snomed.info/sct |
| Observation.code.coding.code | 1..1 | Fixed Value: 1092741000000102 |
| Observation.code.coding.display | 1..1 | Fixed Value: Time from delivery to commencement of spontaneous respiration |
| Observation.component | 2..2 |  |
| Observation.component.code.coding .system | 1..1 | Fixed Value: http://snomed.info/sct |
| Observation.component.code.coding.code | 1..1 | Fixed Value: 258701004 |
| Observation.component.code.coding.display | 1..1 | Fixed Value: minutes |
| Observation.component.valueQuantity | 1..1 | Number of minutes applicable to the spontaneous respiration onset observation, expressed in n2 format |
| Observation.component.code.coding .system | 1..1 | Fixed Value: http://snomed.info/sct |
| Observation.component.code.coding.code | 1..1 | Fixed Value: 257997001 |
| Observation.component.code.coding.display | 1..1 | Fixed Value: seconds |
| Observation.component.valueQuantity | 1..1 | Number of seconds applicable to the spontaneous respiration onset observation, expressed in n2 format |

#### CareConnect-Observation-1 (PutToBreastIndicator)

| Element | Cardinality | Additional Guidance |
| --- | --- | --- |
| Observation.code | 1..1 | Observation.code SHALL use a value from https://fhir.nhs.uk/STU3/ValueSet/DCH-PutToBreastIndicator-1 |


### [CareConnect-Procedure-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Procedure-1)

The CareConnect-Procedure-1 resource included as part of the event message SHALL conform to the [CareConnect-Procedure-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Procedure-1) constrained FHIR profile and the additional population guidance as per the table below:

| Resource Cardinality | TBC |

| Element | Cardinality | Additional Guidance |
| --- | --- | --- |
| subject | 1..1 | This will reference the patient resource representing the subject of this event |
| context | 1..1 | This will reference the encounter resource representing the context of this event |

For each of the Procedure resources representing Birth Detail procedures :

#### CareConnect-Procedure-1 (NeonatalResuscitationMethod)

| Element | Cardinality | Additional Guidance |
| --- | --- | --- |
| Procedure.code | 1..1 | Procedure.code SHALL use a value from https://fhir.nhs.uk/STU3/ValueSet/DCH-NeonatalResuscitationMethod-1 |

#### CareConnect-Procedure-1 (FinalDeliveryType)

| Element | Cardinality | Additional Guidance |
| --- | --- | --- |
| Procedure.code | 1..1 | Procedure.code SHALL use a value from https://fhir.nhs.uk/STU3/ValueSet/DCH-FinalDeliveryType-1 |


## Birth Details Example ##

<script src="https://gist.github.com/IOPS-DEV/0066a98ca1ead84af8d895c939feea26.js"></script>


## Profile Change Mappings for Birth Details ##

Profiles used in [Demographics Update Event Messages 1.2.1-Release Candidate](https://developer.nhs.uk/apis/demographicupdates-120-rc/index.html) are replaced with:

| Demographic-Event-Messages | Demographic-Event-Messages-CareConnect |
|----------------------------|----------------------------------------|
| DCH-Bundle-1 | Bundle |
| DCH-MessageHeader-1 | Event-MessageHeader-1 |
| CareConnect-Organization-1 | CareConnect-Organization-1 |
| DCH-HealthcareService-1 | CareConnect-HealthcareService-1 |
| CareConnect-DCH-Patient-1 | CareConnect-Patient-1 |
| CareConnect-DCH-Encounter-1 | CareConnect-Encounter-1 |
| CareConnect-DCH-PhysicalProblemAtBirth-Condition-1 | CareConnect-Condition-1 |
| CareConnect-DCH-ProblemDuringDelivery-Condition-1 | CareConnect-Condition-1 |
| CareConnect-DCH-APGARScore-Observation-1 | CareConnect-Observation-1 |
| CareConnect-DCH-LengthOfGestation-Observation-1 | CareConnect-Observation-1 |
| CareConnect-DCH-NumberOfBirths-Observation-1 | CareConnect-Observation-1 |
| CareConnect-DCH-SpontaneousRespirationOnset-Observation-1 | CareConnect-Observation-1 |
| CareConnect-DCH-NeonatalResuscitationMethod-Procedure-1 | CareConnect-Procedure-1 |
| CareConnect-DCH-FinalDeliveryType-Procedure-1 | CareConnect-Procedure-1 |
| CareConnect-DCH-AttemptedDeliveryType-Condition-1 | CareConnect-Condition-1 |
| CareConnect-DCH-PutToBreastIndicator-Observation-1 | CareConnect-Observation-1 |
| CareConnect-DCH-Delivery-Location-1 | CareConnect-Location-1 |


---
title: Observations Event Message Bundle
keywords:  messaging, bundles
tags: [fhir,messaging]
sidebar: foundations_sidebar
permalink: explore_observations.html
summary: "The FHIR profiles used for the Observations Event Message Bundle"
---

## FHIR Profiles ##

The following FHIR profiles are used to form the Observations Event Message Bundle:

- [Bundle](http://hl7.org/fhir/STU3/StructureDefinition/Bundle)
- [Event-MessageHeader-1](https://fhir.nhs.uk/STU3/StructureDefinition/Event-MessageHeader-1) - where the coding and display for the event element is fixed to '​observations-1 \| Observations  '
- [CareConnect-Organization-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Organization-1)
- [CareConnect-HealthcareService-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-HealthcareService-1)
- [CareConnect-Patient-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Patient-1)
- [CareConnect-Encounter-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Encounter-1)
- [CareConnect-Location-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Location-1)
- [CareConnect-Practitioner-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Practitioner-1)
- [CareConnect-PractitionerRole-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-PractitionerRole-1)
- [CareConnect-Observation-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Observation-1)
- [CareConnect-BloodPressure-Observation-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-BloodPressure-Observation-1)
- [CareConnect-HeartRate-Observation-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-HeartRate-Observation-1)
- [CareConnect-BodyTemperature-Observation-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-BodyTemperature-Observation-1)
- [CareConnect-RespiratoryRate-Observation-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-RespiratoryRate-Observation-1)
- [CareConnect-OxygenSaturation-Observation-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-OxygenSaturation-Observation-1)


## Bundle Structure

Specifies referencing within the Event Message Bundle.

<div style="text-align:center; margin-bottom:20px" >
	<a href="images/explore/dch-observations.png" target="_blank"><img src="images/explore/dch-observations.png"></a><br/>
	Observations <a href="images/explore/dch-observations.png" target="_blank">(open in new TAB)</a>
</div>

## Observations Event data item mapping to FHIR profiles ##

This Mapping table defines the FHIR elements that SHALL be used to encode the Healthy Child Event Specification data items for each DCH Event Message payload.  
Some common data item mappings, such as patient, publisher or Date/Time of event information, are defined within the [Header mapping table](explore_event_header_design.html) and SHALL be considered in parallel with the payload mapping.

The Child Health Event data items are fulfilled by elements within the FHIR resources listed below:

| DCH Data Item            | FHIR resource element                                 | Mandatory/Required/Optional |
|--------------------------|-------------------------------------------------------|-----------------------------|
| Date                     | CareConnect-Encounter-1.period.start                      | Mandatory                   |                                    |
| ODS Site Code            | CareConnect-Location-1.identifier (ODS Site Code)             | Mandatory                   |                                    |
| Professional Name        | CareConnect-Practitioner-1.name                           | Mandatory                   |                                    |
| SDS Job Role Name        | CareConnect-PractitionerRole-1.code (SDS Job Role Name)   | Mandatory                   |                                    |
| Encounter Type           | CareConnect-Encounter-1.type (childHealthEncounterType)   | Mandatory                   |                                    |

Observation measurement data items are fulfilled as Observation.valueQuantity elements within separate instances of a FHIR Observation resource.

All Observations are Required

| DCH Data Item            | FHIR resource element                                         | Note                               |
|--------------------------|---------------------------------------------------------------|---------------------------------------------|
| Birth Weight             | CareConnect-Observation-1.valueQuantity                                     | Observation.code SHALL use 364589006 \| Birth weight \| |
| Birth Head Circumference | CareConnect-Observation-1.valueQuantity                          | Observation.code SHALL use 169876006 \| Birth head circumference \| |
| Head circumference       | CareConnect-Observation-1.valueQuantity                          | Observation.code SHALL use 363812007 \| Head circumference \| |
| Weight                   | CareConnect-Observation-1.valueQuantity                                     | Observation.code SHALL use 27113001 \| Body weight \| |
| Body Height              | CareConnect-Observation-1.valueQuantity                                     | Observation.code SHALL use 50373000 \| Body height \| |
| Body Length              | CareConnect-Observation-1.valueQuantity                                     | Observation.code SHALL use 248334005 \| Length of body \| |
| BMI Centile              | CareConnect-Observation-1.valueQuantity                                 | Observation.code SHALL use 896691000000102 \| Child body mass index centile \| |
| Systolic Blood Pressure  | CareConnect-BloodPressure-Observation-1.component[systolicComponent].valueQuantity     | * |
| Diastolic Blood Pressure | CareConnect-BloodPressure-Observation-1.component[diastolicComponent].valueQuantity    | * |
| Heart Rate               | CareConnect-HeartRate-Observation-1.valueQuantity                                      | |
| Temperature              | CareConnect-BodyTemperature-Observation-1.valueQuantity                                | For child health, a further Observation.code of 386725007 \| Body temperature \| should be added, with userSelected set to true |
| Respiration Rate         | CareConnect-RespiratoryRate-Observation-1.valueQuantity                                | |
| O2 Saturation            | CareConnect-OxygenSaturation-Observation-1.valueQuantity                               | For child health, a further Observation.code of 431314004 \| Peripheral oxygen saturation \| should be added, with userSelected set to true |
| NCMP Withdrawal Reason   | CareConnect-Observation-1.valueCodeableConcept.Coding.code          | ** |

\* Relevant blood pressure measurement SNOMED CT coding is fixed in the CareConnect-BloodPressure-Observation-1 profile.  
Additional Blood Pressure observations may be reported using further Observation.component elements. For which, Observation.component.code SHALL be coded with the relevant SNOMED CT concept << 75367002 \| Blood pressure \| {i.e. descendant of}

\** Observation.valueCodeableConcept SHALL be coded with the relevant SNOMED CT concept << 376251000000101 \| Excluded from national child measurement programme \| {i.e. descendant of}

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
| event | 1..1 | Fixed Value: "​observations-1 \| Observations" |
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
| PractitionerRole.code(keyWorkerStatus) | 0..1 | If Practitioner is a key worker, PractitionerRole.codekeyWorkerStatus SHALL use a value from https://fhir.nhs.uk/STU3/ValueSet/DCH-KeyWorkerStatus-1 |
| PractitionerRole.specialty | 1..1 | PractitionerRole.specialty SHALL use a value from https://fhir.nhs.uk/STU3/ValueSet/DCH-Specialty-1 |


### [CareConnect-Observation-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Observation-1)

The CareConnect-Observation-1 resource included as part of the event message SHALL conform to the [CareConnect-Observation-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Observation-1) constrained FHIR profile and the additional population guidance as per the table below:

| Resource Cardinality | TBC |

| Element | Cardinality | Additional Guidance |
| --- | --- | --- |
| subject | 1..1 | This will reference the patient resource representing the subject of this event |
| context | 1..1 | This will reference the encounter resource representing the context of this event |
| performer | 1..1 | This will reference the practitioner resource representing the performer of this observation |

For each of the Observation resources representing Observations observations:

#### CareConnect-Observation-1 (Weight)

| Element | Cardinality | Additional Guidance |
| --- | --- | --- |
| Observation.category | 1..1 | |
| Observation.category.coding | 1..* | 1 vital-signs category, optional SNOMED category |
| Observation.category.coding .system | 1..1 | Fixed Value: http://hl7.org/fhir/observation-category |
| Observation.category.coding.code | 1..1 | Fixed Value: vital-signs |
| Observation.category.coding.display | 0..1 | Fixed Value: Vital Signs |
| Observation.code | 1..1 | |
| Observation.code.coding | 2..2 | 1 loinc coded observation and 1 SNOMED equivalent |
| Observation.code.coding .system | 1..1 | Fixed Value: http://loinc.org |
| Observation.code.coding.code | 1..1 | Fixed Value: 29463-7 |
| Observation.code | 1..1 | Observation.code SHALL use a value from https://fhir.nhs.uk/STU3/ValueSet/DCH-Weight-1 |
| Observation.valueQuantity | 1..1 | |
| Observation.valueQuantity.value | 1..1 | Numerical value (to 3 decimal places) |
| Observation.valueQuantity.unit | 1..1 | Unit representation |
| Observation.valueQuantity.system | 1..1 | Fixed Value: http://unitsofmeasure.org |
| Observation.valueQuantity.code | 1..1 | Observation.valueQuantity.code SHALL use a value from http://hl7.org/fhir/stu3/valueset-ucum-bodyweight.html |


#### CareConnect-Observation-1 (Height)

| Element | Cardinality | Additional Guidance |
| --- | --- | --- |
| Observation.category | 1..1 | |
| Observation.category.coding | 1..* | 1 vital-signs category, optional SNOMED category |
| Observation.category.coding .system | 1..1 | Fixed Value: http://hl7.org/fhir/observation-category |
| Observation.category.coding.code | 1..1 | Fixed Value: vital-signs |
| Observation.category.coding.display | 0..1 | Fixed Value: Vital Signs |
| Observation.code | 1..1 | |
| Observation.code.coding | 2..2 | 1 loinc coded observation and 1 SNOMED equivalent |
| Observation.code.coding .system | 1..1 | Fixed Value: http://loinc.org |
| Observation.code.coding.code | 1..1 | Fixed Value: 8302-2 |
| Observation.code.coding .system | 1..1 | Fixed Value: http://snomed.info/sct |
| Observation.code.coding.code | 1..1 | Fixed Value: 50373000 |
| Observation.code.coding.display | 1..1 | Fixed Value: Body height |
| Observation.valueQuantity | 1..1 | |
| Observation.valueQuantity.value | 1..1 | Numerical value (to 1 decimal place) |
| Observation.valueQuantity.unit | 1..1 | Unit representation |
| Observation.valueQuantity.system | 1..1 | Fixed Value: http://unitsofmeasure.org |
| Observation.valueQuantity.code | 1..1 | Observation.valueQuantity.code SHALL use a value from http://hl7.org/fhir/stu3/valueset-ucum-bodylength.html |



#### CareConnect-Observation-1 (Length)

| Element | Cardinality | Additional Guidance |
| --- | --- | --- |
| Observation.category | 1..1 | |
| Observation.category.coding | 1..* | 1 vital-signs category, optional SNOMED category |
| Observation.category.coding .system | 1..1 | Fixed Value: http://hl7.org/fhir/observation-category |
| Observation.category.coding.code | 1..1 | Fixed Value: vital-signs |
| Observation.category.coding.display | 0..1 | Fixed Value: Vital Signs |
| Observation.code | 1..1 | |
| Observation.code.coding | 2..2 | 1 loinc coded observation and 1 SNOMED equivalent |
| Observation.code.coding .system | 1..1 | Fixed Value: http://loinc.org |
| Observation.code.coding.code | 1..1 | Fixed Value: 8306-3 |
| Observation.code.coding .system | 1..1 | Fixed Value: http://snomed.info/sct |
| Observation.code.coding.code | 1..1 | Fixed Value: 248334005 |
| Observation.code.coding.display | 1..1 | Fixed Value: Length of body |
| Observation.valueQuantity | 1..1 | |
| Observation.valueQuantity.value | 1..1 | Numerical value (to 1 decimal place) |
| Observation.valueQuantity.unit | 1..1 | Unit representation |
| Observation.valueQuantity.system | 1..1 | Fixed Value: http://unitsofmeasure.org |
| Observation.valueQuantity.code | 1..1 | Observation.valueQuantity.code SHALL use a value from http://hl7.org/fhir/stu3/valueset-ucum-bodylength.html |


#### CareConnect-Observation-1 (HeadCircumference)

| Element | Cardinality | Additional Guidance |
| --- | --- | --- |
| Observation.category | 1..1 | |
| Observation.category.coding | 1..* | 1 vital-signs category, optional SNOMED category |
| Observation.category.coding .system | 1..1 | Fixed Value: http://hl7.org/fhir/observation-category |
| Observation.category.coding.code | 1..1 | Fixed Value: vital-signs |
| Observation.category.coding.display | 0..1 | Fixed Value: Vital Signs |
| Observation.code | 1..1 | |
| Observation.code.coding | 2..2 | 1 loinc coded observation and 1 SNOMED equivalent |
| Observation.code.coding .system | 1..1 | Fixed Value: http://loinc.org |
| Observation.code.coding.code | 1..1 | Fixed Value: 8287-5 |
 Observation.code | 1..1 | Observation.code SHALL use a value from  https://fhir.nhs.uk/STU3/ValueSet/DCH-HeadCircumferenceSnCT-1 |
 | Observation.valueQuantity | 1..1 | |
| Observation.valueQuantity.value | 1..1 | Numerical value (to 1 decimal place) |
| Observation.valueQuantity.unit | 1..1 | Unit representation |
| Observation.valueQuantity.system | 1..1 | Fixed Value: http://unitsofmeasure.org |
| Observation.valueQuantity.code | 1..1 | Observation.valueQuantity.code SHALL use a value from http://hl7.org/fhir/stu3/valueset-ucum-bodylength.html |


#### CareConnect-Observation-1 (BMICentile)

| Element | Cardinality | Additional Guidance |
| --- | --- | --- |
| Observation.code | 1..1 | |
| Observation.code.coding .system | 1..1 | Fixed Value: http://snomed.info/sct |
| Observation.code.coding.code | 1..1 | Fixed Value: 896691000000102 |
| Observation.code.coding.display | 1..1 | Fixed Value: Child body mass index centile |
| Observation.valueQuantity | 1..1 | |
| Observation.valueQuantity.value | 1..1 | Numerical value (with implicit precision) |
| Observation.valueQuantity.unit | 1..1 | Fixed Value: percentage |
| Observation.valueQuantity.system | 1..1 | Fixed Value: http://unitsofmeasure.org |
| Observation.valueQuantity.code | 1..1 | Fixed Value: %|


#### CareConnect-Observation-1 (NCMPWithdrawal)

| Element | Cardinality | Additional Guidance |
| --- | --- | --- |
| Observation.code | 1..1 | |
| Observation.code.coding .system | 1..1 | Fixed Value: http://snomed.info/sct |
| Observation.code.coding.code | 1..1 | Fixed Value: 376251000000101 |
| Observation.code.coding.display | 1..1 | Fixed Value: Excluded from national child measurement programme |
| Observation.valueCodeableConcept | 1..1 | Observation.valueCodeableConcept.code SHALL use a value from https://fhir.nhs.uk/STU3/ValueSet/DCH-NCMPWithdrawalReason-1 |



### [CareConnect-BloodPressure-Observation-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-BloodPressure-Observation-1)

The CareConnect-BloodPressure-Observation-1 resource included as part of the event message SHALL conform to the [CareConnect-BloodPressure-Observation-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-BloodPressure-Observation-1) constrained FHIR profile and the additional population guidance as per the table below:

| Resource Cardinality | TBC |


### [CareConnect-HeartRate-Observation-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-HeartRate-Observation-1)

The CareConnect-HeartRate-Observation-1 resource included as part of the event message SHALL conform to the [CareConnect-HeartRate-Observation-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-HeartRate-Observation-1) constrained FHIR profile and the additional population guidance as per the table below:

| Resource Cardinality | TBC |



### [CareConnect-BodyTemperature-Observation-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-BodyTemperature-Observation-1)

The CareConnect-BodyTemperature-Observation-1 resource included as part of the event message SHALL conform to the [CareConnect-BodyTemperature-Observation-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-BodyTemperature-Observation-1) constrained FHIR profile and the additional population guidance as per the table below:

| Resource Cardinality | TBC |



### [CareConnect-RespiratoryRate-Observation-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-RespiratoryRate-Observation-1)

The CareConnect-RespiratoryRate-Observation-1 resource included as part of the event message SHALL conform to the [CareConnect-RespiratoryRate-Observation-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-RespiratoryRate-Observation-1) constrained FHIR profile and the additional population guidance as per the table below:

| Resource Cardinality | TBC |



### [CareConnect-OxygenSaturation-Observation-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-OxygenSaturation-Observation-1)

The CareConnect-OxygenSaturation-Observation-1 resource included as part of the event message SHALL conform to the [CareConnect-OxygenSaturation-Observation-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-OxygenSaturation-Observation-1) constrained FHIR profile and the additional population guidance as per the table below:

| Resource Cardinality | TBC |



## Observations Example ##

This example models a post-partum Observations panel comprising Observations for:  
- Birth weight  
- Length of body  
- Birth head circumference  
- Heart rate  
- Respiratory rate  
- Blood pressure  
- Body temperature  
- Hemoglobin saturation with oxygen  

<script src="https://gist.github.com/IOPS-DEV/b6a25d626c75a08768f5e96ed56c1888.js"></script>


## Profile Change Mappings for Observations ##

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
| CareConnect-DCH-Weight-Observation-1 | CareConnect-Observation-1 |
| CareConnect-DCH-Height-Observation-1 | CareConnect-Observation-1 |
| CareConnect-DCH-Length-Observation-1 | CareConnect-Observation-1 |
| CareConnect-DCH-HeadCircumference-Observation-1 | CareConnect-Observation-1 |
| CareConnect-DCH-BMICentile-Observation-1 | CareConnect-Observation-1 |
| CareConnect-BloodPressure-Observation-1 | CareConnect-BloodPressure-Observation-1 |
| CareConnect-HeartRate-Observation-1 | CareConnect-HeartRate-Observation-1 |
| CareConnect-BodyTemperature-Observation-1 | CareConnect-BodyTemperature-Observation-1 |
| CareConnect-RespiratoryRate-Observation-1 | CareConnect-RespiratoryRate-Observation-1 |
| CareConnect-OxygenSaturation-Observation-1 | CareConnect-OxygenSaturation-Observation-1 |
| CareConnect-DCH-NCMPWithdrawal-Observation-1 | CareConnect-Observation-1 |


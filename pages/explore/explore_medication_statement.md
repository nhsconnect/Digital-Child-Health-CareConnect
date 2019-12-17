---
title: Medication Statement Event Message Bundle
keywords:  messaging, bundles
tags: [fhir,messaging]
sidebar: foundations_sidebar
permalink: explore_medication_statement.html
summary: "The FHIR profiles used for the Medication Statement Event Message Bundle"
---

## FHIR Profiles ##

The following FHIR profiles are used to form the Medication Statement Event Message Bundle:

- [Bundle](http://hl7.org/fhir/STU3/StructureDefinition/Bundle)
- [Event-MessageHeader-1](https://fhir.nhs.uk/STU3/StructureDefinition/Event-MessageHeader-1) - where the coding and display elements for the ‘event’ type are fixed to '​medication-statement-1 \| ​Medication Statement  '
- [CareConnect-Organization-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Organization-1)
- [CareConnect-HealthcareService-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-HealthcareService-1)
- [CareConnect-Patient-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Patient-1)
- [CareConnect-Encounter-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Encounter-1)
- [CareConnect-Location-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Location-1)
- [CareConnect-Practitioner-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Practitioner-1)
- [CareConnect-PractitionerRole-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-PractitionerRole-1)
- [CareConnect-Medication-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Medication-1)
- [CareConnect-MedicationStatement-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-MedicationStatement-1)
- [CareConnect-List-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-List-1)

## Bundle Structure

Specifies referencing within the Event Message Bundle.

<div style="text-align:center; margin-bottom:20px" >
	<a href="images/explore/dch-medicationstatement.png" target="_blank"><img src="images/explore/dch-medicationstatement.png"></a><br/>
	Medication Statement <a href="images/explore/dch-medicationstatement.png" target="_blank">(open in new TAB)</a>
</div>

## Medication Statement data item mapping to FHIR profiles ##
The Medication Statement follows the same pattern as Medication Statement in Transfer of Care. As such there are 2 distinct lists - one for the active medications, and one for the discontinued medications. Following the Transfer of Care pattern, each list uses a FHIR List resource.

The Mapping tables shown below defines the FHIR elements that SHALL be used to encode the Healthy Child Event Specification data items for each DCH Event Message payload.  Some common data item mappings, such as patient, publisher or Date/Time of event information, are defined within the [Header mapping table](explore_event_header_design.html) and SHALL be considered in parallel with the payload mapping.

### Medication Statement for Active Medications ###
Active medications uses a List resource to bound all the active medications. Active medications include those that the patient is known to be actively taking. Active medications include medications that have been changed within this episode of care. Changed medication details appear in the MedicationChangeSummary extension of the MedicationStatement resource.

The Child Health Event data items are fulfilled by elements within the FHIR resources listed below:

### Medication Statement List (Active Medications) ###

Note that CareConnect-List-1.entry.flag & CareConnect-List-1.entry.emptyReason must not be used.


| DCH Data Item | FHIR Resource element | Mandatory/<br/>Required/<br/>Optional | Notes |
|---|---|---|---|
| List.code | CareConnect-List-1.code | Mandatory | Fixed value code="1102411000000102" display="Active medications" system="http://snomed.info/sct" |
| List.status | CareConnect-List-1.status | Mandatory | Fixed value="current" |
| List.mode | CareConnect-List-1.mode | Mandatory | Fixed value="snapshot" |
| List.title | CareConnect-List-1.title | Mandatory | Fixed value="Medication Active List" |
| List.subject | CareConnect-List-1.subject | Mandatory |  |
| List.encounter | CareConnect-List-1.encounter | Mandatory |  |
| List.date | CareConnect-List-1.date | Mandatory | The date the List was created |
| List.source | CareConnect-List-1.source | Mandatory | The practitioner who created the List |
| List.entry.item | CareConnect-List-1.entry.item | Mandatory | Link to the active MedicationStatement |


### Medication Statement (Active Medications) ###


| DCH Data Item | FHIR Resource element | Mandatory/<br/>Required/<br/>Optional | Notes |
|---|---|---|---|
| Date/Time | CareConnect-MedicationStatement-1.effectivePeriod.start | Mandatory |  |
| Medication Name | CareConnect-Medication-1.code | Required | Where medication code is not known, the name of the medication should be sent as text in Medication.code.text |
| Form | CareConnect-Medication-1.form | Optional |  |
| Route | CareConnect-MedicationStatement-1.dosage.route | Optional |  |
| Site | CareConnect-MedicationStatement-1.dosage.site | Optional |  |
| Method | CareConnect-MedicationStatement-1.dosage.method | Optional |  |
| Dose directions description | CareConnect-MedicationStatement-1.dosage.text | Optional |  |
| Dose amount description | CareConnect-MedicationStatement-1.dosage.text | Optional | Dose amount should be concatenated with the dose description text |
| Dose timing description | CareConnect-MedicationStatement-1.dosage.text | Optional | Dose timing should be concatenated with the dose description text |
| Structured dose direction cluster | CareConnect-MedicationStatement-1.dosage.additionalInstruction | Optional | MedicationStatement.additionalInstruction to be used as a string element for "Continue Indefinitely"; "Do not discontinue" and "Stop when course complete". |
| Dose direction duration | CareConnect-MedicationStatement-1.dosage.additionalInstruction | Optional | Structured duration instructions may use the FHIR element MedicationStatement.effective[x].effectivePeriod otherwise FHIR element MedicationStatement.note as a degrade to text. |
| Additional instruction | CareConnect-MedicationStatement-1.note | Optional |  |


### Medication Statement for Changed Medications ###

If a medication is changed, the changeSummary extension for the [new] medication should be completed as follows:


| DCH Data Item | FHIR Resource element | Mandatory/<br/>Required/<br/>Optional | Notes |
|---|---|---|---|
| status | CareConnect-MedicationStatement-1.Extension-CareConnect-MedicationChangeSummary-1.status | Optional |  |
| Indication | CareConnect-MedicationStatement-1.Extension-CareConnect-MedicationChangeSummary-1.indication | Optional |  |
| Date of Change | CareConnect-MedicationStatement-1.Extension-CareConnect-MedicationChangeSummary-1.dateChanged | Optional |  |
| Description of Amendment | CareConnect-MedicationStatement-1.Extension-CareConnect-MedicationChangeSummary-1.detailsOfAmendment | Optional |  |


### Medication Statement for Medical Devices (not coded in dm+d) ###

Some medical devices, trial drugs, non-UK sourced drugs etc. are not coded in dm+d. In these cases, the same pattern as for Medication Statement (Active Medications) should be following, using Medication.code.text, rather than Medication.code.

| DCH Data Item | FHIR Resource element | Mandatory/<br/>Required/<br/>Optional | Notes |
|---|---|---|---|
| Medication Device Entry (not in dm+d) | CareConnect-Medication-1.code.text | Optional | Medication and medical devices not in dm+d should use Medication.code.text, and follow the same pattern as Medication Statement (Active Medications) |



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
| event | 1..1 | Fixed Value: "​medication-statement-1 \| ​Medication Statement" |
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



### [CareConnect-Medication-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Medication-1)

The CareConnect-Medication-1 resource included as part of the event message SHALL conform to the [CareConnect-Medication-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Medication-1) constrained FHIR profile and the additional population guidance as per the table below:

| Resource Cardinality | TBC |

| Element | Cardinality | Additional Guidance |
| --- | --- | --- |
| Medication.code | 1..1 | Medication.code SHOULD use a value from https://fhir.hl7.org.uk/STU3/ValueSet/CareConnect-MedicationCode-1 |



### [CareConnect-MedicationStatement-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-MedicationStatement-1)

The CareConnect-MedicationStatement-1 resource included as part of the event message SHALL conform to the [CareConnect-MedicationStatement-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-MedicationStatement-1) constrained FHIR profile and the additional population guidance as per the table below:

| Resource Cardinality | TBC |

| Element | Cardinality | Additional Guidance |
| --- | --- | --- |
| subject | 1..1 | This will reference the patient resource representing the subject of this event |
| context | 1..1 | This will reference the encounter resource representing the context of this event | |
| medicationReference | 1..1 | This will reference the medication resource representing what medication was taken |
| taken | 1..1 | MedicatioStatement.taken SHALL use a value from http://hl7.org/fhir/stu3/valueset-medication-statement-taken.html |


### [CareConnect-List-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-List-1)

The CareConnect-List-1 resource included as part of the event message SHALL conform to the [CareConnect-List-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-List-1) constrained FHIR profile and the additional population guidance as per the table below:

| Resource Cardinality | TBC |

| Element | Cardinality | Additional Guidance |
| --- | --- | --- |
| mode | 1..1 | Fixed Value: snapshot |
| code | 1.1 | code SHALL take a value from https://fhir.hl7.org.uk/STU3/ValueSet/CareConnect-ListCode-1 |
| subject | 1..1 | This will reference the patient resource representing the subject of this event |
| encounter | 0..1 | This MAY reference the encounter resource representing the context of this event |
| source | 0..1 | This MAY reference the practitioner resource representing who defined the list |
| entry.item | 1..* | This SHALL reference individual medication statement resources |



## Medication Statement Example ##

<script src="https://gist.github.com/IOPS-DEV/3524210a5860ee48919e82f87986a0f7.js"></script>


## Profile Change Mappings for Medication Statement ##

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
| CareConnect-DCH-Medication-1 | CareConnect-Medication-1 |
| CareConnect-DCH-MedicationStatement-1 | CareConnect-MedicationStatement-1 |
| CareConnect-ITK-Medication-List-1 | CareConnect-List-1 |


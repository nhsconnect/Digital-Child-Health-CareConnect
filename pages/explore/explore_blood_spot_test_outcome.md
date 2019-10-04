---
title: Blood Spot Test Outcome Event Message Bundle
keywords:  messaging, bundles
tags: [fhir,messaging]
sidebar: foundations_sidebar
permalink: explore_blood_spot_test_outcome.html
summary: "The FHIR profiles used for the Blood Spot Test Outcome Event Message Bundle"
---

## FHIR Profiles ##

The following FHIR profiles are used to form the Blood Spot Test Outcome Event Message Bundle:

- [Bundle](http://hl7.org/fhir/STU3/StructureDefinition/Bundle)
- [Event-MessageHeader-1](https://fhir.nhs.uk/STU3/StructureDefinition/Event-MessageHeader-1) - where the coding and display elements for the 'event' type are fixed to '​​blood-spot-test-outcome-1 \| ​Blood Spot Test Outcome'
- [CareConnect-Organization-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Organization-1)
- [CareConnect-HealthcareService-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-HealthcareService-1)
- [CareConnect-Patient-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Patient-1)
- [CareConnect-Encounter-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Encounter-1)
- [CareConnect-Location-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Location-1)
- [CareConnect-DiagnosticReport-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-DiagnosticReport-1)
- [CareConnect-Procedure-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Procedure-1)
- [CareConnect-Communication-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Communication-1)

## Bundle Structure

Specifies mandatory referencing within the Event Message Bundle.

<div style="text-align:center; margin-bottom:20px" >
	<a href="images/explore/dch-bloodspottestoutcome.png" target="_blank"><img src="images/explore/dch-bloodspottestoutcome.png"></a><br/>
	Blood Spot Test Outcome Bundle <a href="images/explore/dch-bloodspottestoutcome.png" target="_blank">(open in new TAB)</a>
</div>


## Blood Spot Test Outcome Event data item mapping to FHIR profiles ##

The Child Health Event data items are fulfilled by elements within the FHIR resources listed below.

| DCH Data Item                                            | FHIR resource element             | Mandatory/Required/Optional |
|----------------------------------------------------------|-----------------------------------|-----------------------------|
| Date of Blood Test Outcome Received                      | CareConnect-DiagnosticReport-1.issued     | Mandatory                   |
| Procedure Outcome <br/> for each Procedure                              | CareConnect-Procedure-1.outcome | Mandatory                   |
| Comment        											| CareConnect-Communication-1   						| Optional                    | 


## Resource Population Requirements and Guidance ##

The following requirements and resource population guidance should be followed in addition to the requirements and guidance outlined in the data item mapping above and in the [Event Header](https://developer.nhs.uk/apis/ems-beta/explore_event_header_information.html) requirements page.


### [Bundle](http://hl7.org/fhir/STU3/StructureDefinition/Bundle)

The Bundle resource included as part of the event message SHALL conform to the [Bundle](http://hl7.org/fhir/STU3/StructureDefinition/Bundle) constrained FHIR profile and the additional population guidance as per the table below:

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
| event | 1..1 | Fixed Value: blood-spot-test-outcome-1 (Blood Spot Test Outcome) |
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


### [CareConnect-DiagnosticReport-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-DiagnosticReport-1)

The CareConnect-DiagnosticReport-1 resource included as part of the event message SHALL conform to the [CareConnect-DiagnosticReport-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-DiagnosticReport-1) constrained FHIR profile and the additional population guidance as per the table below:

| Resource Cardinality | 1..1 |

| Element | Cardinality | Additional Guidance |
| --- | --- | --- |
| subject | 1..1 | This will reference the patient resource representing the subject of this event |
| issued | 1..1 | This will hold Date/Time the Blood Spot Test Outcome is received |


### [CareConnect-Procedure-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Procedure-1)

The CareConnect-Procedure-1 resource included as part of the event message SHALL conform to the [CareConnect-Procedure-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Procedure-1) constrained FHIR profile and the additional population guidance as per the table below:

| Resource Cardinality | TBC |

| Element | Cardinality | Additional Guidance |
| --- | --- | --- |
| subject | 1..1 | This will reference the patient resource representing the subject of this event |

For each of the Procedure resources representing a Test Outcome:

### CareConnect-Procedure-1 (Blood Spot Screening, Phenylketonuria)

| Element | Cardinality | Additional Guidance |
| --- | --- | --- |
| Procedure.code.coding.system | 1..1 | Fixed Value: http://snomed.info/sct |
| Procedure.code.coding.code | 1..1 | Fixed Value: 314081000 |
| Procedure.code.coding.display | 1..1 | Fixed Value: Phenylketonuria screening test |
| Procedure.outcome.coding(snomedCT) | 1..1 | Procedure.outcome.coding(snomedCT) SHALL use a value from https://fhir.nhs.uk/STU3/ValueSet/DCH-BloodSpotOutcome-1 |

### CareConnect-Procedure-1 (Blood Spot Screening, Sickle Cell Disease)

| Element | Cardinality | Additional Guidance |
| --- | --- | --- |
| Procedure.code.coding.system | 1..1 | Fixed Value: http://snomed.info/sct |
| Procedure.code.coding.code | 1..1 | Fixed Value: 314090007 |
| Procedure.code.coding.display | 1..1 | Fixed Value: Sickle cell disease screening test |
| Procedure.outcome.coding(snomedCT) | 1..1 | Procedure.outcome.coding(snomedCT) SHALL use a value from https://fhir.nhs.uk/STU3/ValueSet/DCH-BloodSpotOutcome-1 |

### CareConnect-Procedure-1 (Blood Spot Screening, Cystic Fibrosis)

| Element | Cardinality | Additional Guidance |
| --- | --- | --- |
| Procedure.code.coding.system | 1..1 | Fixed Value: http://snomed.info/sct |
| Procedure.code.coding.code | 1..1 | Fixed Value: 314080004 |
| Procedure.code.coding.display | 1..1 | Fixed Value: Cystic fibrosis screening test |
| Procedure.outcome.coding(snomedCT) | 1..1 | Procedure.outcome.coding(snomedCT) SHALL use a value from https://fhir.nhs.uk/STU3/ValueSet/DCH-BloodSpotOutcome-1 |

### CareConnect-Procedure-1 (Blood Spot Screening, Congenital Hypothyroidism)

| Element | Cardinality | Additional Guidance |
| --- | --- | --- |
| Procedure.code.coding.system | 1..1 | Fixed Value: http://snomed.info/sct |
| Procedure.code.coding.code | 1..1 | Fixed Value: 400984005 |
| Procedure.code.coding.display | 1..1 | Fixed Value: Congenital hypothyroidism screening test |
| Procedure.outcome.coding(snomedCT) | 1..1 | Procedure.outcome.coding(snomedCT) SHALL use a value from https://fhir.nhs.uk/STU3/ValueSet/DCH-BloodSpotOutcome-1 |

### CareConnect-Procedure-1 (Blood Spot Screening, Medium-chain Acyl-Coenzyme A Dehydrogenase Deficiency)

| Element | Cardinality | Additional Guidance |
| --- | --- | --- |
| Procedure.code.coding.system | 1..1 | Fixed Value: http://snomed.info/sct |
| Procedure.code.coding.code | 1..1 | Fixed Value: 428056008 |
| Procedure.code.coding.display | 1..1 | Fixed Value: Medium-chain acyl-coenzyme A dehydrogenase deficiency screening test |
| Procedure.outcome.coding(snomedCT) | 1..1 | Procedure.outcome.coding(snomedCT) SHALL use a value from https://fhir.nhs.uk/STU3/ValueSet/DCH-BloodSpotOutcome-1 |

### CareConnect-Procedure-1 (Blood Spot Screening, Homocystinuria)

| Element | Cardinality | Additional Guidance |
| --- | --- | --- |
| Procedure.code.coding.system | 1..1 | Fixed Value: http://snomed.info/sct |
| Procedure.code.coding.code | 1..1 | Fixed Value: 940201000000107 |
| Procedure.code.coding.display | 1..1 | Fixed Value: Blood spot homocystinuria screening test |
| Procedure.outcome.coding(snomedCT) | 1..1 | Procedure.outcome.coding(snomedCT) SHALL use a value from https://fhir.nhs.uk/STU3/ValueSet/DCH-BloodSpotOutcome-1 |

### CareConnect-Procedure-1 (Blood Spot Screening, Maple Syrup Urine Disease)

| Element | Cardinality | Additional Guidance |
| --- | --- | --- |
| Procedure.code.coding.system | 1..1 | Fixed Value: http://snomed.info/sct |
| Procedure.code.coding.code | 1..1 | Fixed Value: 940221000000103 |
| Procedure.code.coding.display | 1..1 | Fixed Value: Blood spot MSUD (maple syrup urine disease) screening test |
| Procedure.outcome.coding(snomedCT) | 1..1 | Procedure.outcome.coding(snomedCT) SHALL use a value from https://fhir.nhs.uk/STU3/ValueSet/DCH-BloodSpotOutcome-1 |

### CareConnect-Procedure-1 (Blood Spot Screening, Glutaric Aciduria Type 1)

| Element | Cardinality | Additional Guidance |
| --- | --- | --- |
| Procedure.code.coding.system | 1..1 | Fixed Value: http://snomed.info/sct |
| Procedure.code.coding.code | 1..1 | Fixed Value: 940131000000109 |
| Procedure.code.coding.display | 1..1 | Fixed Value: Blood spot glutaric aciduria type 1 screening test |
| Procedure.outcome.coding(snomedCT) | 1..1 | Procedure.outcome.coding(snomedCT) SHALL use a value from https://fhir.nhs.uk/STU3/ValueSet/DCH-BloodSpotOutcome-1 |

### CareConnect-Procedure-1 (Blood Spot Screening, Isovaleric Acidaemia)

| Element | Cardinality | Additional Guidance |
| --- | --- | --- |
| Procedure.code.coding.system | 1..1 | Fixed Value: http://snomed.info/sct |
| Procedure.code.coding.code | 1..1 | Fixed Value: 940151000000102 |
| Procedure.code.coding.display | 1..1 | Fixed Value: Blood spot isovaleric acidaemia screening test |
| Procedure.outcome.coding(snomedCT) | 1..1 | Procedure.outcome.coding(snomedCT) SHALL use a value from https://fhir.nhs.uk/STU3/ValueSet/DCH-BloodSpotOutcome-1 |



### [CareConnect-Communication-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Communication-1)

The CareConnect-Communication-1 resource included as part of the event message SHALL conform to the [CareConnect-Communication-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Communication-1) constrained FHIR profile and the additional population guidance as per the table below:

| Resource Cardinality | TBC |

| Element | Cardinality | Additional Guidance |
| --- | --- | --- |
| status | 1..1 | Fixed value: completed |
| sender | 1..1 | This will reference the sending organization of the event message. |
| subject | 1..1 | This will reference the patient resource representing the patient who is the subject of this event. |
| Communication.category.coding.system | 1..1 | Fixed Value: https://fhir.nhs.uk/STU3/CodeSystem/DCH-ProfessionalCommentType-1 |
| Communication.category.coding.code | 1..1 | Fixed Value: 007 |
| Communication.category.coding.display | 1..1 | Fixed Value: Newborn Blood Spot Screening |

## DCH Blood Spot Test Outcome Example ##

<script src="https://gist.github.com/IOPS-DEV/4bb135a9d55f59bbffe54d2301bcbcb6.js"></script>

## Profile Change Mappings for Blood Spot Test Outcome ##

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
| DCH-NewbornBloodSpotScreening-DiagnosticReport-1 | CareConnect-DiagnosticReport-1 |
| CareConnect-DCH-NewbornBloodSpotScreeningPKU-Procedure-1 | CareConnect-Procedure-1 |
| CareConnect-DCH-NewbornBloodSpotScreeningSCD-Procedure-1 | CareConnect-Procedure-1 |
| CareConnect-DCH-NewbornBloodSpotScreeningCF-Procedure-1 | CareConnect-Procedure-1 |
| CareConnect-DCH-NewbornBloodSpotScreeningCHT-Procedure-1 | CareConnect-Procedure-1 |
| CareConnect-DCH-NewbornBloodSpotScreeningMCADD-Procedure-1 | CareConnect-Procedure-1 |
| CareConnect-DCH-NewbornBloodSpotScreeningHCU-Procedure-1 | CareConnect-Procedure-1 |
| CareConnect-DCH-NewbornBloodSpotScreeningMSUD-Procedure-1 | CareConnect-Procedure-1 |
| CareConnect-DCH-NewbornBloodSpotScreeningGA1-Procedure-1 | CareConnect-Procedure-1 |
| CareConnect-DCH-NewbornBloodSpotScreeningIVA-Procedure-1 | CareConnect-Procedure-1 |
| DCH-ProfessionalComment-Communication-1 | CareConnect-Communication-1 |


<hr/>


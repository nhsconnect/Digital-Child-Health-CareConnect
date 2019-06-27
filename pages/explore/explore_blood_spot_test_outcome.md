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

## Bundle structure

Specifies mandatory referencing within the Event Message Bundle.

<div style="text-align:center; margin-bottom:20px" >
	<a href="images/explore/dch-bloodspottestoutcome.png" target="_blank"><img src="images/explore/dch-bloodspottestoutcome.png"></a><br/>
	Blood Spot Test Outcome Bundle <a href="images/explore/dch-bloodspottestoutcome.png" target="_blank">(open in new TAB)</a>
</div>


## Resource population requirements and guidance ##

The following requirements and resource population guidance should be followed in addition to the requirements and guidance outlined in the [Event Header](https://developer.nhs.uk/apis/ems-beta/explore_event_header_information.html) requirements page.


### [Bundle](http://hl7.org/fhir/STU3/StructureDefinition/Bundle)

The Bundle resource included as part of the event message SHALL conform to the [Bundle](http://hl7.org/fhir/STU3/StructureDefinition/Bundle) constrained FHIR profile and the additional population guidance as per the table below:

| Resource Cardinality | TBC |

| Element | Cardinality | Additional Guidance |
| --- | --- | --- |
|  |  |  |



### [Event-MessageHeader-1](https://fhir.nhs.uk/STU3/StructureDefinition/Event-MessageHeader-1)

The Event-MessageHeader-1 resource included as part of the event message SHALL conform to the [Event-MessageHeader-1](https://fhir.nhs.uk/STU3/StructureDefinition/Event-MessageHeader-1) constrained FHIR profile and the additional population guidance as per the table below:

| Resource Cardinality | TBC |

| Element | Cardinality | Additional Guidance |
| --- | --- | --- |
|  |  |  |



### [CareConnect-Organization-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Organization-1)

The CareConnect-Organization-1 resource included as part of the event message SHALL conform to the [CareConnect-Organization-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Organization-1) constrained FHIR profile and the additional population guidance as per the table below:

| Resource Cardinality | TBC |

| Element | Cardinality | Additional Guidance |
| --- | --- | --- |
|  |  |  |



### [CareConnect-HealthcareService-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-HealthcareService-1)

The CareConnect-HealthcareService-1 resource included as part of the event message SHALL conform to the [CareConnect-HealthcareService-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-HealthcareService-1) constrained FHIR profile and the additional population guidance as per the table below:

| Resource Cardinality | TBC |

| Element | Cardinality | Additional Guidance |
| --- | --- | --- |
|  |  |  |



### [CareConnect-Patient-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Patient-1)

The CareConnect-Patient-1 resource included as part of the event message SHALL conform to the [CareConnect-Patient-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Patient-1) constrained FHIR profile and the additional population guidance as per the table below:

| Resource Cardinality | TBC |

| Element | Cardinality | Additional Guidance |
| --- | --- | --- |
|  |  |  |



### [CareConnect-Encounter-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Encounter-1)

The CareConnect-Encounter-1 resource included as part of the event message SHALL conform to the [CareConnect-Encounter-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Encounter-1) constrained FHIR profile and the additional population guidance as per the table below:

| Resource Cardinality | TBC |

| Element | Cardinality | Additional Guidance |
| --- | --- | --- |
|  |  |  |



### [CareConnect-Location-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Location-1)

The CareConnect-Location-1 resource included as part of the event message SHALL conform to the [CareConnect-Location-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Location-1) constrained FHIR profile and the additional population guidance as per the table below:

| Resource Cardinality | TBC |

| Element | Cardinality | Additional Guidance |
| --- | --- | --- |
|  |  |  |



### [CareConnect-DiagnosticReport-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-DiagnosticReport-1)

The CareConnect-DiagnosticReport-1 resource included as part of the event message SHALL conform to the [CareConnect-DiagnosticReport-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-DiagnosticReport-1) constrained FHIR profile and the additional population guidance as per the table below:

| Resource Cardinality | TBC |

| Element | Cardinality | Additional Guidance |
| --- | --- | --- |
|  |  |  |



### [CareConnect-Procedure-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Procedure-1)

The CareConnect-Procedure-1 resource included as part of the event message SHALL conform to the [CareConnect-Procedure-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Procedure-1) constrained FHIR profile and the additional population guidance as per the table below:

| Resource Cardinality | TBC |

| Element | Cardinality | Additional Guidance |
| --- | --- | --- |
|  |  |  |



### [CareConnect-Communication-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Communication-1)

The CareConnect-Communication-1 resource included as part of the event message SHALL conform to the [CareConnect-Communication-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Communication-1) constrained FHIR profile and the additional population guidance as per the table below:

| Resource Cardinality | TBC |

| Element | Cardinality | Additional Guidance |
| --- | --- | --- |
|  |  |  |


## PDS Change of Address Example ##
Placeholder Blood Spot Test Outcome example - like it says, it's CoA
<script src="https://gist.github.com/IOPS-DEV/828562b2e3edaec1ed43f48645f5376a.js"></script>


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
<hr/>

## Blood Spot Test Outcome Event data item mapping to FHIR profiles ##

The Child Health Event data items are fulfilled by elements within the FHIR resources listed below.

| DCH Data Item                                            | FHIR resource element             | Mandatory/Required/Optional |
|----------------------------------------------------------|-----------------------------------|-----------------------------|
| Date of Blood Test Outcome Received                      | DCH-NewbornBloodSpotScreening-DiagnosticReport-1.issued     | Mandatory                   |
| Outcome - PHENYLKETONURIA                                | CareConnect-DCH-NewbornBloodSpotScreeningPKU-Procedure-1.outcome | Mandatory                   |
| Outcome - SICKLE CELL DISEASE                            | CareConnect-DCH-NewbornBloodSpotScreeningSCD-Procedure-1.outcome | Mandatory                   |
| Outcome - CYSTIC FIBROSIS                                | CareConnect-DCH-NewbornBloodSpotScreeningCF-Procedure-1.outcome | Mandatory                   |
| Outcome - CONGENITAL HYPOTHYROIDISM                      | CareConnect-DCH-NewbornBloodSpotScreeningCHT-Procedure-1.outcome | Mandatory                   |
| Outcome - MEDIUM CHAIN ACYL-COA DEHYDROGENASE DEFICIENCY | CareConnect-DCH-NewbornBloodSpotScreeningMCADD-Procedure-1.outcome | Mandatory                   |
| Outcome - HOMOCYSTINURIA                                 | CareConnect-DCH-NewbornBloodSpotScreeningHCU-Procedure-1.outcome | Mandatory                   |
| Outcome - MAPLE SYRUP URINE DISEASE                      | CareConnect-DCH-NewbornBloodSpotScreeningMSUD-Procedure-1.outcome | Mandatory                   |
| Outcome - GLUTARIC ACIDURIA TYPE 1                       | CareConnect-DCH-NewbornBloodSpotScreeningGA1-Procedure-1.outcome | Mandatory                   |
| Outcome - ISOVALERIC ACIDAEMIA                            | CareConnect-DCH-NewbornBloodSpotScreeningIVA-Procedure-1.outcome | Mandatory                   |
| Comment        											| DCH-ProfessionalComment-Communication-1   						| Optional                    | 

### Reference Linkage Diagram ###

<img src="images/explore/BloodSpotTestOutcome.png">

### Examples ###

<script src="https://gist.github.com/IOPS-DEV/13bbcd909c9a5e5cae2034e1f27f5854.js"></script>

<script src="https://gist.github.com/IOPS-DEV/9e242c003652cfb3f221117504798327.js"></script>


---
title: Blood Spot Card Received Event Message Bundle
keywords:  messaging, bundles
tags: [fhir,messaging]
sidebar: foundations_sidebar
permalink: explore_blood_spot_card_received.html
summary: "The FHIR profiles used for the Blood Spot Card Received Event Message Bundle"
---

## FHIR Profiles ##

The following FHIR profiles are used to form the Blood Spot Card Received Event Message Bundle:

- [Bundle](http://hl7.org/fhir/STU3/StructureDefinition/Bundle)
- [Event-MessageHeader-1](https://fhir.nhs.uk/STU3/StructureDefinition/Event-MessageHeader-1) - where the coding and display elements for the 'event' type are fixed to '​blood-spot-card-received-1 \| ​Blood Spot Card Received'
- [CareConnect-Organization-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Organization-1)
- [CareConnect-HealthcareService-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-HealthcareService-1)
- [CareConnect-Patient-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Patient-1)
- [CareConnect-Encounter-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Encounter-1)
- [CareConnect-Location-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Location-1)
- [CareConnect-Specimen-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Specimen-1)


## Bundle structure

Specifies mandatory referencing within the Event Message Bundle.

<div style="text-align:center; margin-bottom:20px" >
	<a href="images/explore/dch-bloodspotcardreceived.png" target="_blank"><img src="images/explore/dch-bloodspotcardreceived.png"></a><br/>
	Blood Spot Card Received Bundle <a href="images/explore/dch-bloodspotcardreceived.png" target="_blank">(open in new TAB)</a>
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



### [CareConnect-Specimen-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Specimen-1)

The CareConnect-Specimen-1 resource included as part of the event message SHALL conform to the [CareConnect-Specimen-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Specimen-1) constrained FHIR profile and the additional population guidance as per the table below:

| Resource Cardinality | TBC |

| Element | Cardinality | Additional Guidance |
| --- | --- | --- |
|  |  |  |


## PDS Change of Address Example ##
Placeholder for Blood Spot Card Received example - like it says, it's CoA
<script src="https://gist.github.com/IOPS-DEV/828562b2e3edaec1ed43f48645f5376a.js"></script>


## Profile Change Mappings for Blood Spot Card Received ##

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
| DCH-NewbornBloodSpotScreening-Specimen-1 | CareConnect-Specimen-1 |


<hr/>
<hr/>

## Blood Spot Card Received Event data item mapping to FHIR profiles ##

The Child Health Event data items are fulfilled by elements within the FHIR resources listed below.

<table>
<tr>
<th>DCH Data Item</th><th>FHIR resource element</th><th>Mandatory/<br/>Required/<br/>Optional</th><th>Notes</th>
</tr>
<tr>
<td>Date/Time Sample Received</td><td>DCH-NewbornBloodSpotScreening-Specimen-1.receivedTime</td><td>Required</td><td></td>
</tr>
<tr>
<td>Laboratory Identifier</td><td>CareConnect-Organization-1.identifier</td><td>Required</td><td></td>
</tr>
</table>

### Linkage Diagram ###

<img src="images/explore/BloodSpotCardReceived.png">

### Blood Spot Card Received Event XML Example ###

<script src="https://gist.github.com/IOPS-DEV/0b8caa42ac0f9397b9ef6d7a540498f0.js"></script>

### Blood Spot Card Received Event JSON Example ###

<script src="https://gist.github.com/IOPS-DEV/a3d266f0be2449a59ccfbc56abbf17c9.js"></script>
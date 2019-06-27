---
title: NIPE Outcome Event Message Bundle
keywords:  messaging, bundles
tags: [fhir,messaging]
sidebar: foundations_sidebar
permalink: explore_nipe_outcome.html
summary: "The FHIR profiles used for the NIPE Outcome Event Message Bundle"
---

## FHIR Profiles ##

The following FHIR profiles are used to form the NIPE Outcome Event Message Bundle:

- [Bundle](http://hl7.org/fhir/STU3/StructureDefinition/Bundle)
- [Event-MessageHeader-1](https://fhir.nhs.uk/STU3/StructureDefinition/Event-MessageHeader-1) - where the coding and display elements for the 'event' type are fixed to '​​nipe-outcome-1 \| ​NIPE outcome'
- [CareConnect-Organization-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Organization-1)
- [CareConnect-HealthcareService-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-HealthcareService-1)
- [CareConnect-Patient-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Patient-1)
- [CareConnect-Encounter-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Encounter-1)
- [CareConnect-Location-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Location-1)
- [CareConnect-Practitioner-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Practitioner-1)
- [CareConnect-PractitionerRole-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-PractitionerRole-1)
- [CareConnect-Procedure-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Procedure-1)
- [CareConnect-Communication-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Communication-1)


## Bundle structure

Specifies mandatory referencing within the Event Message Bundle.

<div style="text-align:center; margin-bottom:20px" >
	<a href="images/explore/dch-nipe-outcome.png" target="_blank"><img src="images/explore/dch-nipe-outcome.png"></a><br/>
	NIPE Outcome Bundle <a href="images/explore/dch-nipe-outcome.png" target="_blank">(open in new TAB)</a>
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



### [CareConnect-Practitioner-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Practitioner-1)

The CareConnect-Practitioner-1 resource included as part of the event message SHALL conform to the [CareConnect-Practitioner-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Practitioner-1) constrained FHIR profile and the additional population guidance as per the table below:

| Resource Cardinality | TBC |

| Element | Cardinality | Additional Guidance |
| --- | --- | --- |
|  |  |  |



### [CareConnect-PractitionerRole-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-PractitionerRole-1)

The CareConnect-PractitionerRole-1 resource included as part of the event message SHALL conform to the [CareConnect-PractitionerRole-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-PractitionerRole-1) constrained FHIR profile and the additional population guidance as per the table below:

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
Placeholder for NIPE Outcome example - like it says, it's CoA
<script src="https://gist.github.com/IOPS-DEV/828562b2e3edaec1ed43f48645f5376a.js"></script>


## Profile Change Mappings for NIPE Outcome ##

Profiles used in [Demographics Update Event Messages 1.2.1-Release Candidate](https://developer.nhs.uk/apis/demographicupdates-120-rc/index.html) are replaced with:

| Demographic-Event-Messages | Demographic-Event-Messages-CareConnect |
|----------------------------|----------------------------------------|
| DCH-Bundle-1                                                   | Bundle |
| DCH-MessageHeader-1                                            | Event-MessageHeader-1 |
| CareConnect-Organization-1                                     | CareConnect-Organization-1 |
| DCH-HealthcareService-1                                        | CareConnect-HealthcareService-1 |
| CareConnect-DCH-Patient-1                                      | CareConnect-Patient-1 |
| CareConnect-DCH-Encounter-1                                    | CareConnect-Encounter-1 |
| CareConnect-Location-1                                         | CareConnect-Location-1 |
| CareConnect-DCH-Practitioner-1                                 | CareConnect-Practitioner-1 |
| CareConnect-DCH-PractitionerRole-1                             | CareConnect-PractitionerRole-1 |
| CareConnect-DCH-PhysicalExaminationHips-Procedure-1            | CareConnect-Procedure-1 |
| CareConnect-DCH-PhysicalExaminationEyes-Procedure-1            | CareConnect-Procedure-1 |
| CareConnect-DCH-PhysicalExaminationTestes-Procedure-1          | CareConnect-Procedure-1 |
| CareConnect-DCH-PhysicalExaminationHeart-Procedure-1           | CareConnect-Procedure-1 |
| DCH-ProfessionalComment-Communication-1                        | CareConnect-Communication-1 |

<hr/>
<hr/>


### NIPE Outcome Details Event data item mapping to FHIR profiles ###

The Child Health Event data items are fulfilled by elements within the FHIR resources listed below:
                                                                                                   
<table>
<tr>
<th>DCH Data Item</th><th>FHIR resource element</th><th>Mandatory/<br/>Required/<br/>Optional</th><th>Note</th>
</tr>
<tr>
<td>Date/Time</td><td>CareConnect-DCH-Encounter-1.period.start</td><td>Required</td><td></td>
</tr>
<tr>
<td>ODS Site Code</td><td>CareConnect-Location-1.identifier (ODS Site Code)</td><td>Required</td><td></td>
</tr>
<tr>
<td>Professional Name</td><td>CareConnect-DCH-Practitioner-1.name</td><td>Required</td><td></td>
</tr>
<tr>
<td>SDS Job Role Name</td><td>CareConnect-DCH-PractitionerRole-1.code (SDS Job Role Name)</td><td>Required</td><td></td>
</tr>
<tr>
<td>Outcome Status Hips</td><td>CareConnect-DCH-PhysicalExaminationHips-Procedure-1.outcome</td><td>Mandatory</td><td></td>
</tr>
<tr>
<td>Outcome Status Eyes</td><td>CareConnect-DCH-PhysicalExaminationEyes-Procedure-1.outcome</td><td>Mandatory</td><td></td>
</tr>
<tr>
<td>Outcome Status Testes</td><td>CareConnect-DCH-PhysicalExaminationTestes-Procedure-1.outcome</td><td>Mandatory</td><td></td>
</tr>
<tr>
<td>Outcome Status Heart</td><td>CareConnect-DCH-PhysicalExaminationHeart-Procedure-1.outcome</td><td>Mandatory</td><td></td>
</tr>
<tr>
<td>Comment</td><td>DCH-ProfessionalComment-Communication-1</td><td>Optional</td><td></td>
</tr>
</table>

### Linkage Diagram ###

<img src="images/explore/NIPE-Outcome.png">

### NIPE Outcome XML Example ###

<script src="https://gist.github.com/IOPS-DEV/646e6275b390034a5a1fbf7948b8375b.js"></script>

### NIPE Outcome JSON Example ###

<script src="https://gist.github.com/IOPS-DEV/6463522f305a65b01af174283acc21f4.js"></script>
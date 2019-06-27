---
title: Additional Demographics Event Message Bundle
keywords:  messaging, bundles
tags: [fhir,messaging]
sidebar: foundations_sidebar
permalink: explore_additional_demographics.html
summary: "The FHIR profiles used for the Additional Demographics Event Message Bundle"
---

## FHIR Profiles ##

The following FHIR profiles are used to form the Additional Demographics Event Message Bundle:

- [Bundle](http://hl7.org/fhir/STU3/StructureDefinition/Bundle)
- [Event-MessageHeader-1](https://fhir.nhs.uk/STU3/StructureDefinition/Event-MessageHeader-1) - where the coding and display elements for the 'event' type are fixed to 'additional-demographics-1 \| ​Additional Demographics'
- [CareConnect-Organization-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Organization-1)
- [CareConnect-HealthcareService-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-HealthcareService-1)
- [CareConnect-Patient-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Patient-1)
- [CareConnect-Encounter-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Encounter-1)
- [CareConnect-Location-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Location-1)


## Bundle structure

Specifies mandatory referencing within the Event Message Bundle.

<div style="text-align:center; margin-bottom:20px" >
	<a href="images/explore/dch-additionaldemographics.png" target="_blank"><img src="images/explore/dch-additionaldemographics.png"></a><br/>
	Additional Demographics <a href="images/explore/dch-additionaldemographics.png" target="_blank">(open in new TAB)</a>
</div>



## Resource population requirements and guidance ##

The following requirements and resource population guidance should be followed in addition to the requirements and guidance outlined in the [Event Header](https://developer.nhs.uk/apis/ems-beta/explore_event_header_information.html) requirements page.


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


## PDS Change of Address Example ##
Placeholder for Additional Demographics example - like it says, it's CoA
<script src="https://gist.github.com/IOPS-DEV/828562b2e3edaec1ed43f48645f5376a.js"></script>


## Profile Change Mappings for Additional Demographics ##

Profiles used in [Demographics Update Event Messages 1.2.1-Release Candidate](https://developer.nhs.uk/apis/demographicupdates-120-rc/index.html) are replaced with:

| Demographic-Event-Messages | Demographic-Event-Messages-CareConnect |
|----------------------------|----------------------------------------|
| DCH-Bundle-1  | Bundle |
| DCH-MessageHeader-1  | Event-MessageHeader-1 |
| CareConnect-Organization-1 | CareConnect-Organization-1 |
| DCH-HealthcareService-1 | CareConnect-HealthcareService-1 |
| CareConnect-DCH-Patient-1 | CareConnect-Patient-1 |
| CareConnect-DCH-Encounter-1 | CareConnect-Encounter-1 |
| CareConnect-Location-1 | CareConnect-Location-1 |



<hr/>
<hr/>

## Additional Demographics Event data item mapping to FHIR profiles ##

This Mapping table defines the FHIR elements that SHALL be used to encode the Healthy Child Event Specification data items for each DCH Event Message payload.  
Some common data item mappings, such as patient, publisher or Date/Time of event information, are defined within the [Header mapping table](explore_event_header_design.html) and SHALL be considered in parallel with the payload mapping.

The Child Health Event data items are fulfilled by elements within the FHIR resources listed below:

| DCH Data Item            | FHIR resource element                                 | Mandatory/Required/Optional |
|--------------------------|-------------------------------------------------------|-----------------------------|
| Local Patient Identifier | CareConnect-DCH-Patient-1.identifier (localIdentifier) | Mandatory                   |
| Local Patient Identifier assigning Organisation| CareConnect-DCH-Patient-1.identifier(localIdentifier).assigner | Required                   |
| Town of Birth            | CareConnect-DCH-Patient-1.birthPlace                  | Required                    |
| Date and Time            | CareConnect-DCH-Encounter-1.period.start              | Required                    |
| Country of Birth         | CareConnect-DCH-Patient-1.birthPlace                  | Required                    |
| Patient email address    | CareConnect-DCH-Patient-1.telecom.value               | Required                    |
| Ethnicity <br> see table below             | CareConnect-DCH-Patient-1.ethnicCategory              | Required                    |
| Religion                 | CareConnect-DCH-Patient-1.religiousAffiliation        | Required                    |


### Ethnic categories mapping table ###

Ethnicity recording in Digital Child Health is requested to use the reduced 16+1 Ethnic Category list.
However, CareConnect-Patient-1 has a required binding to the [CareConnect-EthnicCategory-1 valueset](https://fhir.hl7.org.uk/STU3/ValueSet/CareConnect-EthnicCategory-1).  
The following mapping SHOULD be used to map the ethnicCategory value to the reduced valueset.

<table>
<tr><th>16+1 valueSet</th><th>Mapping to PDS valueSet</th></tr>
<tr><td>A - British, Mixed British</td><td>A - British, Mixed British</td></tr>
<tr><td>B - Irish</td><td>B - Irish</td></tr>
<tr><td>C - Any Other White Background</td><td>C - Any other White background<br/>C2 - Northern Irish<br/>C3 - Other white, white unspecified<br/>CA - English<br/>CB - Scottish<br/>CC - Welsh<br/>CD - Cornish<br/>CE - Cypriot(part not stated)<br/>CF - Greek<br/>CG - Greek Cypriot<br/>CH - Turkish<br/>CJ - Turkish Cypriot<br/>CK - Italian<br/>CL - Irish Traveller<br/>CM - Traveller<br/>CN - Gypsy/Romany<br/>CP -Polish<br/>CQ - All republics which made up the former USSR<br/>CR - Kosovan<br/>CS - Albanian<br/>CT - Bosnian<br/>CU - Croatian<br/>CV - Serbian<br/>CW - Other republics which madeup the former Yugoslavia<br/>CX - Mixed white<br/>CY - Other white European, European unspecified, European mixed<br/></td></tr>
<tr><td>D - White & Black Caribbean</td><td>D - White & Black Caribbean</td></tr>
<tr><td>E - White & Black African</td><td>E - White & Black African</td></tr>
<tr><td>F - White & Asian</td><td>F - White & Asian</td></tr>
<tr><td>G - Any Other Mixed Background</td><td>G - Any other mixed background<br/>GA - Black and Asian<br/>GB - Black and Chinese<br/>GC - Black and White<br/>GD - Chinese and White<br/>GE - Asian and Chinese<br/>GF - Other Mixed, Mixed Unspecified</td></tr>
<tr><td>H - Indian</td><td>H - Indian</td></tr>
<tr><td>J - Pakistani</td><td>J - Pakistani</td></tr>
<tr><td>K - Bangladeshi</td><td>K - Bangladeshi</td></tr>
<tr><td>L - Any Other Asian Background</td><td>LA - Mixed Asian<br/>LB - Punjabi<br/>LC - Kashmiri<br/>LD - East African Asian<br/>LE - Sri Lanka<br/>LF - Tamil<br/>LG - Sinhalese<br/>LH - British Asian<br/>LJ - Caribbean Asian<br/>LK - Other Asian, Asian unspecified</td></tr>
<tr><td>M - Caribbean</td><td>M - Caribbean</td></tr>
<tr><td>N - African</td><td>N - African</td></tr>
<tr><td>P - Any Other Black Background</td><td>P - Any other Black background<br/>PA - Somali<br/>PB - Mixed Black<br/>PC - Nigerian<br/>PD - Black British<br/>PE - Other Black, Black unspecified</td></tr>
<tr><td>R - Chinese</td><td>R - Chinese</td></tr>
<tr><td>S - Any Other Ethnic Group</td><td>S - Any other ethnic group<br/>SA - Vietnamese<br/>SB - Japanese<br/>SC - Filipino<br/>SD - Malaysian<br/>SE - Any Other Group</td></tr>
<tr><td>Z - Not Stated</td><td>Z - Not Stated</td></tr>
</table>

### Linkage Diagram ###

This Linkage diagram defines the required references that SHALL be made between resources within the DCH Event Message bundle. It includes both Header and Payload resources (but omits the DCH-Bundle-1 wrapper).

<img src="images/explore/AdditionalDemographics.png">

### Additional Demographics XML Example ###

<script src="https://gist.github.com/IOPS-DEV/22e06b06e7d5382f12f51869fb459f49.js"></script>

### Additional Demographics JSON Example ###

<script src="https://gist.github.com/IOPS-DEV/0e3175b7d83561e307c356c6341d3c2e.js"></script>

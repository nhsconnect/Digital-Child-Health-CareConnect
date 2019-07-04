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


## Bundle Structure

Specifies mandatory referencing within the Event Message Bundle.

<div style="text-align:center; margin-bottom:20px" >
	<a href="images/explore/dch-additionaldemographics.png" target="_blank"><img src="images/explore/dch-additionaldemographics.png"></a><br/>
	Additional Demographics <a href="images/explore/dch-additionaldemographics.png" target="_blank">(open in new TAB)</a>
</div>

## Additional Demographics Event data item mapping to FHIR profiles ##

This Mapping table defines the FHIR elements that SHALL be used to encode the Healthy Child Event Specification data items for each DCH Event Message payload.  
Some common data item mappings, such as patient, publisher or Date/Time of event information, are defined within the [Header mapping table](explore_event_header_design.html) and SHALL be considered in parallel with the payload mapping.

The Child Health Event data items are fulfilled by elements within the FHIR resources listed below:

| DCH Data Item            | FHIR resource element                                 | Mandatory/Required/Optional |
|--------------------------|-------------------------------------------------------|-----------------------------|
| Local Patient Identifier | CareConnect-Patient-1.identifier (localIdentifier) | Mandatory                   |
| Local Patient Identifier assigning Organisation| CareConnect-Patient-1.identifier(localIdentifier).assigner | Required                   |
| Town of Birth            | CareConnect-Patient-1.birthPlace                  | Required                    |
| Country of Birth         | CareConnect-Patient-1.birthPlace                  | Required                    |
| Patient email address    | CareConnect-Patient-1.telecom.value               | Required                    |
| Ethnicity <br> see table below             | CareConnect-Patient-1.ethnicCategory              | Required                    |
| Religion                 | CareConnect-Patient-1.religiousAffiliation        | Required                    |
| Date and Time            | CareConnect-Encounter-1.period.start              | Required                    |


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
| event | 1..1 | Fixed Value: additional-demographics-1 (Additional Demographics) |
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
| identifier(localIdentifier) | 1..1 | Local Patient Identifier SHALL be included within the localIdentifier identifier slice |
| identifier(localIdentifier),assigner | 1..1 | This will reference the Local Patient Identifier assigning Organisation |
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


## DCH Additional Demographics Example ##

<script src="https://gist.github.com/IOPS-DEV/646f784bcb1db6e7aa3d924aaaf423d1.js"></script>


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

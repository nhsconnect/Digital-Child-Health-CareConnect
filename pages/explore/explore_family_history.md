---
title: Family History Event Message Bundle
keywords:  messaging, bundles
tags: [fhir,messaging]
sidebar: foundations_sidebar
permalink: explore_family_history.html
summary: "The FHIR profiles used for the Family History Event Message Bundle"
---

## FHIR Profiles ##

The following FHIR profiles are used to form the Family History Event Message Bundle:

- [Bundle](http://hl7.org/fhir/STU3/StructureDefinition/Bundle)
- [Event-MessageHeader-1](https://fhir.nhs.uk/STU3/StructureDefinition/Event-MessageHeader-1) - where the coding and display for the event element is fixed to "​family-history-1 \| ​Family History"
- [CareConnect-Organization-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Organization-1)
- [CareConnect-HealthcareService-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-HealthcareService-1)
- [CareConnect-Patient-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Patient-1)
- [CareConnect-Encounter-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Encounter-1)
- [CareConnect-Location-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Location-1)
- [CareConnect-FamilyMemberHistory-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-FamilyMemberHistory-1)
- [CareConnect-Communication-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Communication-1)

## Bundle Structure

Specifies referencing within the Event Message Bundle.


<div style="text-align:center; margin-bottom:20px" >
	<a href="images/explore/dch-familyhistory.png" target="_blank"><img src="images/explore/dch-familyhistory.png"></a><br/>
	Family History <a href="images/explore/dch-familyhistory.png" target="_blank">(open in new TAB)</a>
</div>

## Family History Event data item mapping to FHIR profiles ##

This Mapping table defines the FHIR elements that SHALL be used to encode the Healthy Child Event Specification data items for each DCH Event Message payload.  
Some common data item mappings, such as patient, publisher or Date/Time of event information, are defined within the [Header mapping table](explore_event_header_design.html) and SHALL be considered in parallel with the payload mapping.

The Child Health Event data items are fulfilled by elements within the FHIR resources listed below:

<table>
<tr>
<th>DCH Data Item</th><th>FHIR resource element</th><th>Mandatory/<br/>Required/<br/>Optional</th><th>Notes</th>
</tr>
<tr>
<td>Date/Time</td><td>CareConnect-Encounter-1.period.start</td><td>Mandatory</td><td></td>
</tr>
<tr>
<td>ODS/ORD Site Code</td><td>CareConnect-Location-1.identifier (ODS Site Code)</td><td>Required</td><td></td>
</tr>
<tr>
<td>Family History</td><td>CareConnect-FamilyMemberHistory-1.condition.code</td><td>Mandatory</td><td></td>
</tr>
<tr>
<td>Relationship to child</td><td>CareConnect-FamilyMemberHistory-1.relationship.code</td><td>Required</td><td></td>
</tr>
<tr>
<td>Maternal Problems in Pregnancy Impacting Fetus</td><td>CareConnect-FamilyMemberHistory-1.condition.code.text</td><td>Required</td><td></td>
</tr>
<tr>
<td>Maternal or Paternal relation</td><td>CareConnect-FamilyMemberHistory-1.relationship.code</td><td>Required</td><td>CareConnect-FamilyMemberHistory-1.relationship.code shall contain 2 codes - one for the relationship type and a further code to confirm whether the relation is part of the maternal or paternal side of the family</td>
</tr>
<tr>
<td>Comment</td><td>CareConnect-Communication-1</td><td>Optional</td><td></td>
</tr>
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
| event | 1..1 | Fixed Value: "​family-history-1 \| ​Family History" |
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



### [CareConnect-FamilyMemberHistory-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-FamilyMemberHistory-1) (Family Member History)

The CareConnect-FamilyMemberHistory-1 resource included as part of the event message SHALL conform to the [CareConnect-FamilyMemberHistory-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-FamilyMemberHistory-1) constrained FHIR profile and the additional population guidance as per the table below:

| Resource Cardinality | 0..1 |

| Element | Cardinality | Additional Guidance |
| --- | --- | --- |
| patient | 1..1 | This will reference the patient resource representing the subject of this event |
| relationship | 1..1 | relationship SHALL use a value from https://fhir.nhs.uk/STU3/ValueSet/DCH-FamilyMemberHistory-PersonRelationshipType-1 |
| condition.code | 1..1 | condition.code SHALL use a value from https://fhir.nhs.uk/STU3/ValueSet/DCH-FamilyHistory-1 |

### [CareConnect-FamilyMemberHistory-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-FamilyMemberHistory-1) (Maternal Problems In Pregnancy)

The CareConnect-FamilyMemberHistory-1 resource included as part of the event message SHALL conform to the [CareConnect-FamilyMemberHistory-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-FamilyMemberHistory-1) constrained FHIR profile and the additional population guidance as per the table below:

| Resource Cardinality | 0..1 |

| Element | Cardinality | Additional Guidance |
| --- | --- | --- |
| patient | 1..1 | This will reference the patient resource representing the subject of this event |
| relationship | 1..1 | relationship SHALL use a value from http://hl7.org/fhir/ValueSet/v3-FamilyMember |
| condition.code | 1..1 | condition.code SHOULD use a value from https://fhir.nhs.uk/STU3/ValueSet/DCH-MaternalProblemsInPregnancy-FamilyHistory-1 |




### [CareConnect-Communication-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Communication-1)

The CareConnect-Communication-1 resource included as part of the event message SHALL conform to the [CareConnect-Communication-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Communication-1) constrained FHIR profile and the additional population guidance as per the table below:

| Resource Cardinality | 0..* |

| Element | Cardinality | Additional Guidance |
| --- | --- | --- |
| Communication.reasonCode | 0..1 | Communication.reasonCode SHALL use a value from https://fhir.nhs.uk/STU3/ValueSet/DCH-InformationOrAdviceGiven-1 |



## Family History Example ##

<script src="https://gist.github.com/IOPS-DEV/a279428950d8b8b89ec335e389420768.js"></script>


## Profile Change Mappings for Family History ##

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
| CareConnect-DCH-FamilyMemberHistory-1 | CareConnect-FamilyMemberHistory-1 |
| CareConnect-DCH-MaternalProblemsInPregnancy-FamilyMemberHistory-1 | CareConnect-FamilyMemberHistory-1 |
| DCH-ProfessionalComment-Communication-1 | CareConnect-Communication-1 |


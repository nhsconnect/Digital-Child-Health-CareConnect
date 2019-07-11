---
title: Problem List Event Message Bundle
keywords:  messaging, bundles
tags: [fhir,messaging]
sidebar: foundations_sidebar
permalink: explore_problem_list.html
summary: "The FHIR profiles used for the Problem List Event Message Bundle"
---

## FHIR Profiles ##

The following FHIR profiles are used to form the Problem List Event Message Bundle:

- [Bundle](http://hl7.org/fhir/STU3/StructureDefinition/Bundle)
- [Event-MessageHeader-1](https://fhir.nhs.uk/STU3/StructureDefinition/Event-MessageHeader-1) - where the coding and display elements for the ‘event’ type are fixed to '​problem-list-1 \| Problem List  '
- [CareConnect-Organization-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Organization-1)
- [CareConnect-HealthcareService-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-HealthcareService-1)
- [CareConnect-Patient-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Patient-1)
- [CareConnect-Encounter-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Encounter-1)
- [CareConnect-Location-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Location-1)
- [CareConnect-Condition-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Condition-1)
- [CareConnect-Practitioner-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Practitioner-1)
- [CareConnect-PractitionerRole-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-PractitionerRole-1)

## Bundle Structure

Specifies referencing within the Event Message Bundle.

<div style="text-align:center; margin-bottom:20px" >
	<a href="images/explore/dch-problemlist.png" target="_blank"><img src="images/explore/dch-problemlist.png"></a><br/>
	Problem List <a href="images/explore/dch-problemlist.png" target="_blank">(open in new TAB)</a>
</div>

## Problem List Event data item mapping to FHIR profiles ##

This Mapping table defines the FHIR elements that SHALL be used to encode the Healthy Child Event Specification data items for each DCH Event Message payload.  
Some common data item mappings, such as patient, publisher or Date/Time of event information, are defined within the [Header mapping table](explore_event_header_design.html) and SHALL be considered in parallel with the payload mapping.

The Child Health Event data items are fulfilled by elements within the FHIR resources listed below:

| DCH Data Item            | FHIR resource element                                 | Mandatory/Required/Optional |
|--------------------------|-------------------------------------------------------|-----------------------------|
| Date/Time               | CareConnect-Condition-1.assertedDate       | Mandatory                             | Format is YYYY-MM-DD”T”HH:MM:SS  |
| ODS/ORD Site Code       | CareConnect-Organization-1.identifier (odsSiteCode)      | Required                              |                         |
| SDS Job Role Name       | CareConnect-PractitionerRole-1.code (sdsJobRoleName) | Required                              |                         |
| Performing Professional | CareConnect-Practitioner-1.name                      | Required                              |                         |
| Condition               | CareConnect-1.code               | Mandatory                             |                         |
| Condition onset date    | CareConnect-Condition-1.onsetDateTime or onsetString | Required                    |To allow free text and date, rather than just date.  Uses the [FHIR date time format](http://hl7.org/fhir/stu3/datatypes.html#dateTime )                         |
| Condition end date      | CareConnect-Condition-1.abatementDateTime or abatementString  | Required                    |Uses the [FHIR date time format](http://hl7.org/fhir/stu3/datatypes.html#dateTime )                         |
| Fetal Diagnosis         | CareConnect-Condition-1               | Optional                              | Foetal Diagnosis to be recorded as appropriately coded Condition                     |
| Comment                 | CareConnect-Condition-1.note               | Optional                              | Free text (no maximum characters) |


## Resource Population Requirements and Guidance ##

The following requirements and resource population guidance should be followed in addition to the requirements and guidance outlined in the data item mapping above and in the [Event Header](https://developer.nhs.uk/apis/ems-beta/explore_event_header_information.html) requirements page.

#### _list profiles used (and sustituted L3 variants)_ ####

## Problem List Example ##

<script src="https://gist.github.com/IOPS-DEV/8bf9db8846e529fa3cb460981e99af4d.js"></script>


## Profile Change Mappings for Problem List ##

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
| CareConnect-DCH-Diagnosis-Condition-1 | CareConnect-Condition-1 |
| CareConnect-DCH-FetalDiagnosis-Condition-1 | CareConnect-Condition-1 |
| CareConnect-DCH-Practitioner-1 | CareConnect-Practitioner-1 |
| CareConnect-DCH-PractitionerRole-1 | CareConnect-PractitionerRole-1 |


<hr/>
<hr/>

## Old Stuff ##

#### retain until new content completed then remove ####



The following FHIR profiles are used to form the Problem List Event Message Bundle:

- [DCH-Bundle-1](https://fhir.nhs.uk/STU3/StructureDefinition/DCH-Bundle-1)
- [DCH-MessageHeader-1](https://fhir.nhs.uk/STU3/StructureDefinition/DCH-MessageHeader-1) - where the coding and display elements for the 'event' type are fixed to 'CH008 - Problem List'
- [CareConnect-Organization-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Organization-1)
- [DCH-HealthcareService-1](https://fhir.nhs.uk/STU3/StructureDefinition/DCH-HealthcareService-1)
- [CareConnect-DCH-Patient-1](https://fhir.nhs.uk/STU3/StructureDefinition/CareConnect-DCH-Patient-1)
- [CareConnect-DCH-Encounter-1](https://fhir.nhs.uk/STU3/StructureDefinition/CareConnect-DCH-Encounter-1)
- [CareConnect-Location-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Location-1)
- [CareConnect-DCH-Diagnosis-Condition-1](https://fhir.nhs.uk/STU3/StructureDefinition/CareConnect-DCH-Diagnosis-Condition-1)
- [CareConnect-DCH-FetalDiagnosis-Condition-1](https://fhir.nhs.uk/STU3/StructureDefinition/CareConnect-DCH-FetalDiagnosis-Condition-1)
- [CareConnect-DCH-Practitioner-1](https://fhir.nhs.uk/STU3/StructureDefinition/CareConnect-DCH-Practitioner-1)
- [CareConnect-DCH-PractitionerRole-1](https://fhir.nhs.uk/STU3/StructureDefinition/CareConnect-DCH-PractitionerRole-1)

### Problem List Event Event data item mapping to FHIR profiles ###

This Mapping table defines the FHIR elements that SHALL be used to encode the Healthy Child Event Specification data items for each DCH Event Message payload.  
Some common data item mappings, such as patient, publisher or Date/Time of event information, are defined within the [Header mapping table](explore_event_header_design.html) and SHALL be considered in parallel with the payload mapping.

The Child Health Event data items are fulfilled by elements within the FHIR resources listed below:

| DCH Data Item           | FHIR resource element                                    | Mandatory/<br/>Required/<br/>Optional | Note                    |
|-------------------------|----------------------------------------------------------|---------------------------------------|-------------------------|
| Date/Time               | CareConnect-DCH-Diagnosis-Condition-1.assertedDate       | Mandatory                             | Format is YYYY-MM-DD”T”HH:MM:SS  |
| ODS/ORD Site Code       | CareConnect-Organization-1.identifier (odsSiteCode)      | Required                              |                         |
| SDS Job Role Name       | CareConnect-DCH-PractitionerRole-1.code (sdsJobRoleName) | Required                              |                         |
| Performing Professional | CareConnect-DCH-Practitioner-1.name                      | Required                              |                         |
| Condition               | CareConnect-DCH-Diagnosis-Condition-1.code               | Mandatory                             |                         |
| Condition onset date    | CareConnect-DCH-Diagnosis-Condition-1.onsetDateTime or onsetString | Required                    |To allow free text and date, rather than just date.  Uses the [FHIR date time format](http://hl7.org/fhir/stu3/datatypes.html#dateTime )                         |
| Condition end date      | CareConnect-DCH-Diagnosis-Condition-1.abatementDateTime or abatementString  | Required                    |Uses the [FHIR date time format](http://hl7.org/fhir/stu3/datatypes.html#dateTime )                         |
| Fetal Diagnosis         | CareConnect-DCH-FetalDiagnosis-Condition-1               | Optional                              |                         |
| Comment                 | CareConnect-DCH-Diagnosis-Condition-1.note               | Optional                              | Free text (no maximum characters) |


### Reference Linkage Diagram ###

This Linkage diagram defines the required references that SHALL be made between resources within the DCH Event Message bundle. It includes both Header and Payload resources (but omits the DCH-Bundle-1 wrapper).

<img src="images/explore/ProblemList.png">

### Problem List Bundle XML Example ###

<script src="https://gist.github.com/IOPS-DEV/86f4c784c063366f7e90a32cc9e9c50f.js"></script>

### Problem List Bundle JSON Example ###

<script src="https://gist.github.com/IOPS-DEV/a5123084e12eef41b1cdbb0f78fe8370.js"></script>
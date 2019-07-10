---
title: Information and Advice Given Event Message Bundle
keywords:  messaging, bundles
tags: [fhir,messaging]
sidebar: foundations_sidebar
permalink: explore_information_and_advice_given.html
summary: "The FHIR profiles used for the Information and Advice Given Event Message Bundle"
---

## FHIR Profiles ##

The following FHIR profiles are used to form the Information and Advice Given Event Message Bundle:

- [Bundle](http://hl7.org/fhir/STU3/StructureDefinition/Bundle)
- [Event-MessageHeader-1](https://fhir.nhs.uk/STU3/StructureDefinition/Event-MessageHeader-1) - where the coding and display elements for the ‘event’ type are fixed to '​information-and-advice-given-1 \| Information and Advice Given  '
- [CareConnect-Organization-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Organization-1)
- [CareConnect-HealthcareService-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-HealthcareService-1)
- [CareConnect-Patient-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Patient-1)
- [CareConnect-Encounter-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Encounter-1)
- [CareConnect-Location-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Location-1)
- [CareConnect-Practitioner-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Practitioner-1)
- [CareConnect-PractitionerRole-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-PractitionerRole-1)
- [CareConnect-Communication-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Communication-1)
- [CareConnect-RelatedPerson-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-RelatedPerson-1)

## Bundle Structure

Specifies referencing within the Event Message Bundle.

<div style="text-align:center; margin-bottom:20px" >
	<a href="images/explore/dch-informationandadvice.png" target="_blank"><img src="images/explore/dch-informationandadvice.png"></a><br/>
	Information and Advice Given <a href="images/explore/dch-informationandadvice.png" target="_blank">(open in new TAB)</a>
</div>

## Information and Advice Given Event data item mapping to FHIR profiles ##

This Mapping table defines the FHIR elements that SHALL be used to encode the Healthy Child Event Specification data items for each DCH Event Message payload.  
Some common data item mappings, such as patient, publisher or Date/Time of event information, are defined within the [Header mapping table](explore_event_header_design.html) and SHALL be considered in parallel with the payload mapping.

The Child Health Event data items are fulfilled by elements within the FHIR resources listed below:

| DCH Data Item            | FHIR resource element                                 | Mandatory/Required/Optional |
|--------------------------|-------------------------------------------------------|-----------------------------|
| Date/Time                        | CareConnect-Communication-1.sent                            | Mandatory                   | Format is YYYY-MM-DD”T”HH:MM:SS                       |
| ODS/ORD Site Code              | CareConnect-Location-1.identifier (ODS Site Code)               | Required                   |                         |
| Performing Professional          | CareConnect-Practitioner-1.name                                 | Required                   |                         |
| SDS Job Role Name           | CareConnect-PractitionerRole-1.code (SDS Job Role Name) 		| Required                   |                         |
| Information Or Advice Given (coded text) | CareConnect-Communication-1.reasonCode  | Required                    |                         |
| Information Or Advice Given (free text) | CareConnect-Communication-1.payload.contentString  | Required                    |                         |
| Recipient                   | CareConnect-RelatedPerson-1.relationship                                    | Required                    |                         |


## Resource Population Requirements and Guidance ##

The following requirements and resource population guidance should be followed in addition to the requirements and guidance outlined in the data item mapping above and in the [Event Header](https://developer.nhs.uk/apis/ems-beta/explore_event_header_information.html) requirements page.

#### _list profiles used (and sustituted L3 variants)_ ####

## Information and Advice Given Example ##

#### _placeholder using additional demographics_ ####

<script src="https://gist.github.com/IOPS-DEV/646f784bcb1db6e7aa3d924aaaf423d1.js"></script>


## Profile Change Mappings for Information and Advice Given ##

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
| DCH-InformationAndAdviceGiven-Communication-1 | CareConnect-Communication-1 |
| DCH-RelatedPerson-1 | CareConnect-RelatedPerson-1 |

<hr/>
<hr/>

## Old Stuff ##

#### retain until new content completed then remove ####



The following FHIR profiles are used to form the Information and Advice Given Event Message Bundle:

- [DCH-Bundle-1](https://fhir.nhs.uk/STU3/StructureDefinition/DCH-Bundle-1)
- [DCH-MessageHeader-1](https://fhir.nhs.uk/STU3/StructureDefinition/DCH-MessageHeader-1) - where the coding and display elements for the 'event' type are fixed to 'CH017 - Information And Advice Given'
- [CareConnect-Organization-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Organization-1)
- [DCH-HealthcareService-1](https://fhir.nhs.uk/STU3/StructureDefinition/DCH-HealthcareService-1)
- [CareConnect-DCH-Patient-1](https://fhir.nhs.uk/STU3/StructureDefinition/CareConnect-DCH-Patient-1)
- [CareConnect-DCH-Encounter-1](https://fhir.nhs.uk/STU3/StructureDefinition/CareConnect-DCH-Encounter-1)
- [CareConnect-Location-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Location-1)
- [CareConnect-DCH-Practitioner-1](https://fhir.nhs.uk/STU3/StructureDefinition/CareConnect-DCH-Practitioner-1)
- [CareConnect-DCH-PractitionerRole-1](https://fhir.nhs.uk/STU3/StructureDefinition/CareConnect-DCH-PractitionerRole-1)
- [DCH-InformationAndAdviceGiven-Communication-1](https://fhir.nhs.uk/STU3/StructureDefinition/DCH-InformationAndAdviceGiven-Communication-1)
- [DCH-RelatedPerson-1](https://fhir.nhs.uk/STU3/StructureDefinition/DCH-RelatedPerson-1)


### Information and Advice Given Event data item mapping to FHIR profiles ###

This Mapping table defines the FHIR elements that SHALL be used to encode the Healthy Child Event Specification data items for each DCH Event Message payload.  
Some common data item mappings, such as patient, publisher or Date/Time of event information, are defined within the [Header mapping table](explore_event_header_design.html) and SHALL be considered in parallel with the payload mapping.

The Child Health Event data items are fulfilled by elements within the FHIR resources listed below:

| DCH Data Item               | FHIR resource element                                               | Mandatory/Required/Optional | Note                    |
|-----------------------------|---------------------------------------------------------------------|-----------------------------|-------------------------|
| Date/Time                        | DCH-InformationAndAdviceGiven-Communication-1.sent                            | Mandatory                   | Format is YYYY-MM-DD”T”HH:MM:SS                       |
| ODS/ORD Site Code              | CareConnect-Location-1.identifier (ODS Site Code)               | Required                   |                         |
| Performing Professional          | CareConnect-DCH-Practitioner-1.name                                 | Required                   |                         |
| SDS Job Role Name           | CareConnect-DCH-PractitionerRole-1.code (SDS Job Role Name) 		| Required                   |                         |
| Information Or Advice Given (coded text) | DCH-InformationAndAdviceGiven-Communication-1.reasonCode  | Required                    |                         |
| Information Or Advice Given (free text) | DCH-InformationAndAdviceGiven-Communication-1.payload.contentString  | Required                    |                         |
| Recipient                   | DCH-RelatedPerson-1.relationship                                    | Required                    |                         |

### Reference Linkage Diagram ###

This Linkage diagram defines the required references that SHALL be made between resources within the DCH Event Message bundle. It includes both Header and Payload resources (but omits the DCH-Bundle-1 wrapper).

<img src="images/explore/InformationAndAdviceGiven.png">

### Information and Advice Given Bundle XML Example ###

<script src="https://gist.github.com/IOPS-DEV/23d2e722f353f904501a853e7054b56a.js"></script>

###  Information and Advice Given Bundle JSON Example ###

<script src="https://gist.github.com/IOPS-DEV/86d31cb3975134db49f826b9fd93b2d1.js"></script>

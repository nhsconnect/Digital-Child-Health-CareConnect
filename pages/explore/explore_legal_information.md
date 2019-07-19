---
title: Legal Information Event Message Bundle
keywords:  messaging, bundles
tags: [fhir,messaging]
sidebar: foundations_sidebar
permalink: explore_legal_information.html
summary: "The FHIR profiles used for the Legal Information Event Message Bundle"
---

## FHIR Profiles ##

The following FHIR profiles are used to form the Legal Information Event Message Bundle:

- [Bundle](http://hl7.org/fhir/STU3/StructureDefinition/Bundle)
- [Event-MessageHeader-1](https://fhir.nhs.uk/STU3/StructureDefinition/Event-MessageHeader-1)
- [CareConnect-Organization-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Organization-1) - where the coding and display elements for the ‘event’ type are fixed to "​legal-information-1 | Legal Information"
- [CareConnect-HealthcareService-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-HealthcareService-1)
- [CareConnect-Patient-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Patient-1)
- [CareConnect-Encounter-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Encounter-1)
- [CareConnect-Location-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Location-1)
- [CareConnect-Observation-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Observation-1)

## Bundle Structure

Specifies referencing within the Event Message Bundle.


<div style="text-align:center; margin-bottom:20px" >
	<a href="images/explore/dch-legalinformation.png" target="_blank"><img src="images/explore/dch-legalinformation.png"></a><br/>
	Legal Information <a href="images/explore/dch-legalinformation.png" target="_blank">(open in new TAB)</a>
</div>

## Legal Information Event data item mapping to FHIR profiles ##

This Mapping table defines the FHIR elements that SHALL be used to encode the Healthy Child Event Specification data items for each DCH Event Message payload.  
Some common data item mappings, such as patient, publisher or Date/Time of event information, are defined within the [Header mapping table](explore_event_header_design.html) and SHALL be considered in parallel with the payload mapping.

The Child Health Event data items are fulfilled by elements within the FHIR resources listed below:

| DCH Data Item                                        | FHIR Resource element                                                 | Mandatory/<br/>Required/<br/>Optional | Notes           |
|------------------------------------------------------|-----------------------------------------------------------------------|---------------------------------------|-----------------|
| Date/Time                                            | CareConnect-Encounter-1.period.start                              | Mandatory                             |                 |
| Looked After Child Start Date                        | CareConnect-Observation-1.effectivePeriod.start                   | Required                              | The 'Looked After Child' Observation SHALL be SNOMED CT coded "764841000000100 \| Looked after child" |
| Looked After Child End Date                          | CareConnect-Observation-1.effectivePeriod.end                     | Required                              |                 |
| Local Authority (LAC)                                | CareConnect-Organization-1.name                                       | Required                              |                 |
| Local Authority (LAC) ODS Site Code                  | CareConnect-Organization-1.identifier (oDSOrganizationCode)           | Required                              |                 |
| Local Authority (LAC) Office Hours Telephone         | CareConnect-Organization-1.telecom                                    | Required                              |                 |
| Local Authority (LAC) Emergency Duty Team Telephone  | CareConnect-Organization-1.contact.telecom                            | Required                              | Organization.contact.purpose.text SHALL be set to “Emergency Duty Team phone number”|
| Child Protection Plan Start Date                     | CareConnect-Observation-1.effectivePeriod.start                   | Required                              |  The 'Child Protection Plan' Observation SHALL be SNOMED CT coded "1064311000000109 \| Child protection plan" |
| Child Protection Plan End Date                       | CareConnect-Observation-1.effectivePeriod.end                     | Required                              |                 |
| Local Authority (CPP)                                | CareConnect-Organization-1.name                                       | Required                              |                 |
| Local Authority (CPP) ODS Site Code                  | CareConnect-Organization-1.identifier (oDSOrganizationCode)           | Required                              |                 |
| Local Authority (CPP) Office Hours Telephone         | CareConnect-Organization-1.telecom                                    | Required                              |                 |
| Local Authority (CPP) Emergency Duty Team Telephone  | CareConnect-Organization-1.contact.telecom                            | Required                              | Organization.contact.purpose.text SHALL be set to “Emergency Duty Team phone number”|

LAC: Looked After Child  
CPP: Child Protection Plan  
ODS: Organisation Data Service  

The fact that a Child is 'Looked After' or has a 'Child Protection Plan' are recorded on separate CareConnect-DCH-Observation-1 instances. These MAY be associated with separate Local Authoritoes, modelled as CareConnect-Organization-1 instances (although usually one Local Authority only is involved).

## Resource Population Requirements and Guidance ##

The following requirements and resource population guidance should be followed in addition to the requirements and guidance outlined in the data item mapping above and in the [Event Header](https://developer.nhs.uk/apis/ems-beta/explore_event_header_information.html) requirements page.

#### _list profiles used (and sustituted L3 variants)_ ####

## Legal Information Example ##

<script src="https://gist.github.com/IOPS-DEV/8130bde1a4dd78e53d7185cc57911122.js"></script>


## Profile Change Mappings for Legal Information ##

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
| CareConnect-DCH-Observation-1 | CareConnect-Observation-1 |

<hr/>
<hr/>

## Old Stuff ##

#### retain until new content completed then remove ####



The following FHIR profiles are used to form the Legal Information Event Message Bundle:

- [DCH-Bundle-1](https://fhir.nhs.uk/STU3/StructureDefinition/DCH-Bundle-1)
- [DCH-MessageHeader-1](https://fhir.nhs.uk/STU3/StructureDefinition/DCH-MessageHeader-1) - where the coding and display elements for the 'event' type are fixed to 'CH033 - Legal Information'
- [CareConnect-Organization-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Organization-1)
- [DCH-HealthcareService-1](https://fhir.nhs.uk/STU3/StructureDefinition/DCH-HealthcareService-1)
- [CareConnect-DCH-Patient-1](https://fhir.nhs.uk/STU3/StructureDefinition/CareConnect-DCH-Patient-1)
- [CareConnect-DCH-Encounter-1](https://fhir.nhs.uk/STU3/StructureDefinition/CareConnect-DCH-Encounter-1)
- [CareConnect-Location-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Location-1)
- [CareConnect-DCH-Observation-1](https://fhir.nhs.uk/STU3/StructureDefinition/CareConnect-DCH-Observation-1)

### Legal Information Event data item mapping to FHIR profiles ###

This Mapping table defines the FHIR elements that SHALL be used to encode the Healthy Child Event Specification data items for each DCH Event Message payload.  
Some common data item mappings, such as patient, publisher or Date/Time of event information, are defined within the [Header mapping table](explore_event_header_design.html) and SHALL be considered in parallel with the payload mapping.

The Child Health Event data items are fulfilled by elements within the FHIR resources listed below:

| DCH Data Item                                        | FHIR Resource element                                                 | Mandatory/<br/>Required/<br/>Optional | Notes           |
|------------------------------------------------------|-----------------------------------------------------------------------|---------------------------------------|-----------------|
| Date/Time                                            | CareConnect-DCH-Encounter-1.period.start                              | Mandatory                             |                 |
| Looked After Child Start Date                        | CareConnect-DCH-Observation-1.effectivePeriod.start                   | Required                              | The 'Looked After Child' Observation SHALL be SNOMED CT coded "764841000000100 \| Looked after child" |
| Looked After Child End Date                          | CareConnect-DCH-Observation-1.effectivePeriod.end                     | Required                              |                 |
| Local Authority (LAC)                                | CareConnect-Organization-1.name                                       | Required                              |                 |
| Local Authority (LAC) ODS Site Code                  | CareConnect-Organization-1.identifier (oDSOrganizationCode)           | Required                              |                 |
| Local Authority (LAC) Office Hours Telephone         | CareConnect-Organization-1.telecom                                    | Required                              |                 |
| Local Authority (LAC) Emergency Duty Team Telephone  | CareConnect-Organization-1.contact.telecom                            | Required                              | Organization.contact.purpose.text SHALL be set to “Emergency Duty Team phone number”|
| Child Protection Plan Start Date                     | CareConnect-DCH-Observation-1.effectivePeriod.start                   | Required                              |  The 'Child Protection Plan' Observation SHALL be SNOMED CT coded "1064311000000109 \| Child protection plan" |
| Child Protection Plan End Date                       | CareConnect-DCH-Observation-1.effectivePeriod.end                     | Required                              |                 |
| Local Authority (CPP)                                | CareConnect-Organization-1.name                                       | Required                              |                 |
| Local Authority (CPP) ODS Site Code                  | CareConnect-Organization-1.identifier (oDSOrganizationCode)           | Required                              |                 |
| Local Authority (CPP) Office Hours Telephone         | CareConnect-Organization-1.telecom                                    | Required                              |                 |
| Local Authority (CPP) Emergency Duty Team Telephone  | CareConnect-Organization-1.contact.telecom                            | Required                              | Organization.contact.purpose.text SHALL be set to “Emergency Duty Team phone number”|

LAC: Looked After Child  
CPP: Child Protection Plan  
ODS: Organisation Data Service  

The fact that a Child is 'Looked After' or has a 'Child Protection Plan' are recorded on separate CareConnect-DCH-Observation-1 instances. These MAY be associated with separate Local Authoritoes, modelled as CareConnect-Organization-1 instances (although usually one Local Authority only is involved).

### Linkage Diagram ###

This Linkage diagram defines the required references that SHALL be made between resources within the DCH Event Message bundle. It includes both Header and Payload resources (but omits the DCH-Bundle-1 wrapper).

Note, in the diagram, below, the top CareConnect-Organization-1 is the event source, whilst the bottom CareConnect-Organization-1 is the Local Authority responsible for the child.

<img src="images/explore/LegalInformation.png">

### Legal Information XML Example ###

<script src="https://gist.github.com/IOPS-DEV/177dc20663f8d3d5e4c67b4990ff2129.js"></script>

### Legal Information JSON Example ###

<script src="https://gist.github.com/IOPS-DEV/bdecb82cb6b07a1bb987f0f9f479110c.js"></script>
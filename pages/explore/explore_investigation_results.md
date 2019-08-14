---
title: Investigation Results Event Message Bundle
keywords:  messaging, bundles
tags: [fhir,messaging]
sidebar: foundations_sidebar
permalink: explore_investigation_results.html
summary: "The FHIR profiles used for the Investigation Results Event Message Bundle"
---

## FHIR Profiles ##

The following FHIR profiles are used to form the Investigation Results Event Message Bundle:

- [Bundle](http://hl7.org/fhir/STU3/StructureDefinition/Bundle)
- [Event-MessageHeader-1](https://fhir.nhs.uk/STU3/StructureDefinition/Event-MessageHeader-1) - where the coding and display elements for the ‘event’ type are fixed to ‘​investigation-results-1 \| Investigation Results’
- [CareConnect-Organization-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Organization-1)
- [CareConnect-HealthcareService-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-HealthcareService-1)
- [CareConnect-Patient-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Patient-1)
- [CareConnect-Encounter-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Encounter-1)
- [CareConnect-Location-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Location-1)
- [CareConnect-Practitioner-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Practitioner-1)
- [CareConnect-PractitionerRole-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-PractitionerRole-1)
- [CareConnect-Observation-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Observation-1)


## Bundle Structure

Specifies referencing within the Event Message Bundle.

<div style="text-align:center; margin-bottom:20px" >
	<a href="images/explore/dch-investigationresults.png" target="_blank"><img src="images/explore/dch-investigationresults.png"></a><br/>
	Investigation Results <a href="images/explore/dch-investigationresults.png" target="_blank">(open in new TAB)</a>
</div>

## Investigation Results Event data item mapping to FHIR profiles ##

This Mapping table defines the FHIR elements that SHALL be used to encode the Healthy Child Event Specification data items for each DCH Event Message payload.  
Some common data item mappings, such as patient, publisher or Date/Time of event information, are defined within the [Header mapping table](explore_event_header_design.html) and SHALL be considered in parallel with the payload mapping.

The Child Health Event data items are fulfilled by elements within the FHIR resources listed below:

| DCH Data Item              | FHIR Resource element                                                                     | Mandatory/<br/>Required/<br/>Optional  | Note                    |
|----------------------------|-------------------------------------------------------------------------------------------|----------------------------------------|-------------------------|
| Date/Time                  | CareConnect-Encounter-1.period.start                                                  | Mandatory                              | Format is YYYY-MM-DD”T”HH:MM:SS |
| ODS/ORD Site Code          | CareConnect-Location-1.identifier (ODS Site Code)                                         | Required                               |                         |
| Performing Professional    | CareConnect-Practitioner.name                                                         | Required                               |                         |
| SDS Job Role Name          | CareConnect-PractitionerRole-1.code (SDS Job Role Name)	                             | Required                               |                         |
| Investigation              | CareConnect-Observation-1.code                                                        | Mandatory                              | The investigation should be drawn from the Procedure hierarchy of SNOMED CT (<71388002 Procedure (procedure)), but there may be an alternative SNOMED CT concept. |
| Investigation Results      | CareConnect-Observation-1.value[x]*                                                   | Required                               | CareConnect-Observation-1.value[String] for free text field to be used if no coded text available. |

*Note that the appropriate value data type should be used when reporting investigation results (for example, a measurement would use valueQuantity, and have an appropriate unit). Investigation results that are coded should use SNOMED CT, and be drawn from the Evaluation Findings Hierarchy (< 441742003 Evaluation finding (finding)), but could use other concepts from SNOMED CT. Some investigation results may have several components (for example some genetic investigations, ECG etc.), and these should use the component part of CareConnect-Observation-1 to record the investigation result.


## Resource Population Requirements and Guidance ##

The following requirements and resource population guidance should be followed in addition to the requirements and guidance outlined in the data item mapping above and in the [Event Header](https://developer.nhs.uk/apis/ems-beta/explore_event_header_information.html) requirements page.

#### _list profiles used (and sustituted L3 variants)_ ####

## Investigation Results Example ##

<script src="https://gist.github.com/IOPS-DEV/1d07ddf2c985b8adbfbee8590d5886b3.js"></script>


## Profile Change Mappings for Investigation Results ##

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
| CareConnect-DCH-Observation-1 | CareConnect-Observation-1 |


<hr/>
<hr/>

## Old Stuff ##

#### retain until new content completed then remove ####


The following FHIR profiles are used to form the Investigation Results Event Message Bundle:

- [DCH-Bundle-1](https://fhir.nhs.uk/STU3/StructureDefinition/DCH-Bundle-1)
- [DCH-MessageHeader-1](https://fhir.nhs.uk/STU3/StructureDefinition/DCH-MessageHeader-1) - where the coding and display elements for the 'event' type are fixed to 'CH037 - Investigation Results'
- [CareConnect-Organization-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Organization-1)
- [DCH-HealthcareService-1](https://fhir.nhs.uk/STU3/StructureDefinition/DCH-HealthcareService-1)
- [CareConnect-DCH-Patient-1](https://fhir.nhs.uk/STU3/StructureDefinition/CareConnect-DCH-Patient-1)
- [CareConnect-DCH-Encounter-1](https://fhir.nhs.uk/STU3/StructureDefinition/CareConnect-DCH-Encounter-1)
- [CareConnect-Location-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Location-1)
- [CareConnect-DCH-Practitioner-1](https://fhir.nhs.uk/STU3/StructureDefinition/CareConnect-DCH-Practitioner-1)
- [CareConnect-DCH-PractitionerRole-1](https://fhir.nhs.uk/STU3/StructureDefinition/CareConnect-DCH-PractitionerRole-1)
- [CareConnect-DCH-Observation-1](https://fhir.nhs.uk/STU3/StructureDefinition/CareConnect-DCH-Observation-1)
                                                                                                   
### Investigation Results Event data item mapping to FHIR profiles ###

This Mapping table defines the FHIR elements that SHALL be used to encode the Healthy Child Event Specification data items for each DCH Event Message payload.  
Some common data item mappings, such as patient, publisher or Date/Time of event information, are defined within the [Header mapping table](explore_event_header_design.html) and SHALL be considered in parallel with the payload mapping.

The Child Health Event data items are fulfilled by elements within the FHIR resources listed below:

**Investigation Results Child Health Event**

| DCH Data Item              | FHIR Resource element                                                                     | Mandatory/<br/>Required/<br/>Optional  | Note                    |
|----------------------------|-------------------------------------------------------------------------------------------|----------------------------------------|-------------------------|
| Date/Time                  | CareConnect-DCH-Encounter-1.period.start                                                  | Mandatory                              | Format is YYYY-MM-DD”T”HH:MM:SS |
| ODS/ORD Site Code          | CareConnect-Location-1.identifier (ODS Site Code)                                         | Required                               |                         |
| Performing Professional    | CareConnect-DCH-Practitioner.name                                                         | Required                               |                         |
| SDS Job Role Name          | CareConnect-DCH-PractitionerRole-1.code (SDS Job Role Name)	                             | Required                               |                         |
| Investigation              | CareConnect-DCH-Observation-1.code                                                        | Mandatory                              | The investigation should be drawn from the Procedure hierarchy of SNOMED CT (<71388002 Procedure (procedure)), but there may be an alternative SNOMED CT concept. |
| Investigation Results      | CareConnect-DCH-Observation-1.value[x]*                                                   | Required                               | CareConnect-DCH-Observation-1.value[String] for free text field to be used if no coded text available. |

*Note that the appropriate value data type should be used when reporting investigation results (for example, a measurement would use valueQuantity, and have an appropriate unit). Investigation results that are coded should use SNOMED CT, and be drawn from the Evaluation Findings Hierarchy (< 441742003 Evaluation finding (finding)), but could use other concepts from SNOMED CT. Some investigation results may have several components (for example some genetic investigations, ECG etc.), and these should use the component part of CareConnect-DCH-Observation-1 to record the investigation result.

### Reference Linkage Diagram ###

This Linkage diagram defines the required references that SHALL be made between resources within the DCH Event Message bundle. It includes both Header and Payload resources (but omits the DCH-Bundle-1 wrapper).

<img src="images/explore/InvestigationResults.png">

### Investigation Results Bundle XML Example ###

<script src="https://gist.github.com/IOPS-DEV/9f9c78430b3218effff41e6d871349c5.js"></script>

### Investigation Results Bundle JSON Example ###

<script src="https://gist.github.com/IOPS-DEV/66d7ee69d7bb1df2027cf64ec4dcb2e3.js"></script>


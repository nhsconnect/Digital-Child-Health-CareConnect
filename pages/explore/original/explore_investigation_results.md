---
title: Investigation Results Event Message Bundle
keywords:  messaging, bundles
tags: [fhir,messaging]
sidebar: foundations_sidebar
permalink: explore_investigation_results.html
summary: "The FHIR profiles used for the Investigation Results Event Message Bundle"
---

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


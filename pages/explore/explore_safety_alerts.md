---
title: Safety Alerts Event Message Bundle
keywords:  messaging, bundles
tags: [fhir,messaging]
sidebar: foundations_sidebar
permalink: explore_safety_alerts.html
summary: "The FHIR profiles used for the Safety Alerts Event Message Bundle"
---

## FHIR Profiles ##

The following FHIR profiles are used to form the Safety Alerts Event Message Bundle:

- [Bundle](http://hl7.org/fhir/STU3/StructureDefinition/Bundle)
- [Event-MessageHeader-1](https://fhir.nhs.uk/STU3/StructureDefinition/Event-MessageHeader-1) - where the coding and display for the event element is fixed to "​safety-alerts-1 \| ​Safety Alerts"
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
	<a href="images/explore/dch-safetyalerts.png" target="_blank"><img src="images/explore/dch-safetyalerts.png"></a><br/>
	Safety Alerts <a href="images/explore/dch-safetyalerts.png" target="_blank">(open in new TAB)</a>
</div>

## Safety Alerts Event data item mapping to FHIR profiles ##

This Mapping table defines the FHIR elements that SHALL be used to encode the Healthy Child Event Specification data items for each DCH Event Message payload.  
Some common data item mappings, such as patient, publisher or Date/Time of event information, are defined within the [Header mapping table](explore_event_header_design.html) and SHALL be considered in parallel with the payload mapping.

The Child Health Event data items are fulfilled by elements within the FHIR resources listed below:

| DCH Data Item     | FHIR Resource element                                       | Mandatory/<br/>Required/<br/>Optional | Note                                                                 |
|-------------------|-------------------------------------------------------------|---------------------------------------|----------------------------------------------------------------------|
| Date              | CareConnect-Encounter-1.period.start                        | Mandatory                             |                                                                      |
| ODS Site Code     | CareConnect-Location-1.identifier (ODS Site Code)           | Required                              |                                                                      |
| SDS Job Role Name | CareConnect-PractitionerRole-1.code (SDS Job Role Name)     | Required                              |                                                                      |
| Professional Name | CareConnect-Practitioner-1.name                             | Required                              |                                                                      |
| Risk Type         | CareConnect-Observation-1.code.text                         | Required                              | Risk type SHALL be represented by setting code.text to 'Risk to self', 'Risk to others' or 'Risk from others'  |
| Risk End Date     | CareConnect-Observation-1.effectivePeriod.end               | Required                              |                                                                      |
| Risk Details      | CareConnect-Observation-1.valueString                       | Required                              | The identified risk is documented in Observation.valueString as free text.          |

Multiple 'Risks' SHALL be recorded as multiple, separate Observation resources within the Safety Alerts Event Message Bundle.

## Resource Population Requirements and Guidance ##

The following requirements and resource population guidance should be followed in addition to the requirements and guidance outlined in the data item mapping above and in the [Event Header](https://developer.nhs.uk/apis/ems-beta/explore_event_header_information.html) requirements page.

#### _list profiles used (and sustituted L3 variants)_ ####

## Safety Alerts Example ##

<script src="https://gist.github.com/IOPS-DEV/8f322b8cc3a32137dc88208a577e438f.js"></script>


## Profile Change Mappings for Safety Alerts ##

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
| CareConnect-Observation-1 | CareConnect-Observation-1 |

<hr/>
<hr/>

## Old Stuff ##

#### retain until new content completed then remove ####



The following FHIR profiles are used to form the Safety Alerts Event Message Bundle:

- [DCH-Bundle-1](https://fhir.nhs.uk/STU3/StructureDefinition/DCH-Bundle-1)
- [DCH-MessageHeader-1](https://fhir.nhs.uk/STU3/StructureDefinition/DCH-MessageHeader-1) - where the coding and display for the event element is fixed to 'CH029 - Safety Alerts'
- [CareConnect-Organization-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Organization-1)
- [DCH-HealthcareService-1](https://fhir.nhs.uk/STU3/StructureDefinition/DCH-HealthcareService-1)
- [CareConnect-DCH-Patient-1](https://fhir.nhs.uk/STU3/StructureDefinition/CareConnect-DCH-Patient-1)
- [CareConnect-DCH-Encounter-1](https://fhir.nhs.uk/STU3/StructureDefinition/CareConnect-DCH-Encounter-1)
- [CareConnect-Location-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Location-1)
- [CareConnect-DCH-Practitioner-1](https://fhir.nhs.uk/STU3/StructureDefinition/CareConnect-DCH-Practitioner-1)
- [CareConnect-DCH-PractitionerRole-1](https://fhir.nhs.uk/STU3/StructureDefinition/CareConnect-DCH-PractitionerRole-1) 
- [CareConnect-Observation-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Observation-1)

### Safety Alerts Event data item mapping to FHIR profiles ###

This Mapping table defines the FHIR elements that SHALL be used to encode the Healthy Child Event Specification data items for each DCH Event Message payload.  
Some common data item mappings, such as patient, publisher or Date/Time of event information, are defined within the [Header mapping table](explore_event_header_design.html) and SHALL be considered in parallel with the payload mapping.

The Child Health Event data items are fulfilled by elements within the FHIR resources listed below:

| DCH Data Item     | FHIR Resource element                                       | Mandatory/<br/>Required/<br/>Optional | Note                                                                 |
|-------------------|-------------------------------------------------------------|---------------------------------------|----------------------------------------------------------------------|
| Date              | CareConnect-DCH-Encounter-1.period.start                    | Mandatory                             |                                                                      |
| ODS Site Code     | CareConnect-Location-1.identifier (ODS Site Code)           | Required                              |                                                                      |
| SDS Job Role Name | CareConnect-DCH-PractitionerRole-1.code (SDS Job Role Name) | Required                              |                                                                      |
| Professional Name | CareConnect-DCH-Practitioner-1.name                         | Required                              |                                                                      |
| Risk Type         | CareConnect-Observation-1.code.text                         | Required                              | Risk type SHALL be represented by setting code.text to 'Risk to self', 'Risk to others' or 'Risk from others'  |
| Risk End Date     | CareConnect-Observation-1.effectivePeriod.end               | Required                              |                                                                      |
| Risk Details      | CareConnect-Observation-1.valueString                       | Required                              | The identified risk is documented in Observation.valueString as free text.          |

Multiple 'Risks' SHALL be recorded as multiple, separate Observation resources within the Safety Alerts Event Message Bundle.

### Linkage Diagram ###

This Linkage diagram defines the required references that SHALL be made between resources within the DCH Event Message bundle. It includes both Header and Payload resources (but omits the DCH-Bundle-1 wrapper).

<img src="images/explore/SafetyAlerts.png">

### Safety Alerts XML Example ###

<script src="https://gist.github.com/IOPS-DEV/9cabbe020c71b79b32c8595c17661098.js"></script>

### Safety Alerts JSON Example ###

<script src="https://gist.github.com/IOPS-DEV/898e56846e6b7553efe70e0ce336f565.js"></script>
---
title: Discharge Details Event Message Bundle
keywords:  messaging, bundles
tags: [fhir,messaging]
sidebar: foundations_sidebar
permalink: explore_discharge_details.html
summary: "The FHIR profiles used for the Discharge Details Event Message Bundle"
---

## FHIR Profiles ##

The following FHIR profiles are used to form the Discharge Details Event Message Bundle:

- [Bundle](http://hl7.org/fhir/STU3/StructureDefinition/Bundle)
- [Event-MessageHeader-1](https://fhir.nhs.uk/STU3/StructureDefinition/Event-MessageHeader-1) - where the coding and display for the event element is fixed to ‘discharge-details-1 \| Discharge Details’
- [CareConnect-Organization-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Organization-1)
- [CareConnect-HealthcareService-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-HealthcareService-1)
- [CareConnect-Patient-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Patient-1)
- [CareConnect-Encounter-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Encounter-1)
- [CareConnect-Location-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Location-1)
- [CareConnect-Practitioner-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Practitioner-1)
- [CareConnect-PractitionerRole-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-PractitionerRole-1)

## Bundle Structure

Specifies referencing within the Event Message Bundle.


<div style="text-align:center; margin-bottom:20px" >
	<a href="images/explore/dch-dischargedetails.png" target="_blank"><img src="images/explore/dch-dischargedetails.png"></a><br/>
	Discharge Details <a href="images/explore/dch-dischargedetails.png" target="_blank">(open in new TAB)</a>
</div>

## Discharge Details Event data item mapping to FHIR profiles ##

This Mapping table defines the FHIR elements that SHALL be used to encode the Healthy Child Event Specification data items for each DCH Event Message payload.  
Some common data item mappings, such as patient, publisher or Date/Time of event information, are defined within the [Header mapping table](explore_event_header_design.html) and SHALL be considered in parallel with the payload mapping.

The Child Health Event data items are fulfilled by elements within the FHIR resources listed below:

| DCH Data Item                     | FHIR resource element                                            | Mandatory/Required/Optional | Note                                                                                  |
|-----------------------------------|------------------------------------------------------------------|-----------------------------|---------------------------------------------------------------------------------------|
| Date and Time of Discharge        | CareConnect-Encounter-1.period.end                           | Required                    |                                                                                       |
| ODS/ORD Site Code                 | CareConnect-Location-1.identifier (ODS Site Code)                | Required                    |                                                                                       |
| Discharging Clinician             | CareConnect-Practitioner-1                                   | Required                    |                                                                                       |
| Discharging Clinician Identifier  | CareConnect-Practitioner-1.identifier.value                  | Required                    |                 |
| Identifier Issuer                 | CareConnect-Practitioner-1.identifier.system                 | Required                    | *               |
| Discharging Speciality/Department | CareConnect-HealthcareService-1.specialty                                | Required                    |                                                                                       |
| Discharge method                  | CareConnect-Encounter-1.hospitalization.dischargeMethod      | Required                    |                                                                                       |
| Discharge destination             | CareConnect-Encounter-1.hospitalization.dischargeDisposition | Required                    |                                                                                       |
| Discharge address                 | CareConnect-Location-1.address                                   | Required                    | Discharge address required if it is _not_ to the usual place of residence.                                |

**\*** The Professional Registration Body identifier, e.g. the discharging Clinician's GMC number, is recorded as **Responsible Clinician Identifier** in element **CareConnect-Practitioner-1.identifier.value**.  
The identifier for the issuing Professional Registration Body is recorded as **Identifier Issuer** in element **CareConnect-Practitioner-1.identifier.system** as follows:

| Issuing Professional Registration Body         | Identifier                                |
|------------------------------------------------|-------------------------------------------|
| General Dental Council Identifier              | http://fhir.hl7.org.uk/Id/gdc-number  |
| General Medical Council Identifier             | http://fhir.hl7.org.uk/Id/gmc-number  |
| Health and Care Professions Council Identifier | http://fhir.hl7.org.uk/Id/hcpc-number |
| Nursing and Midwifery Council Identifier       | http://fhir.hl7.org.uk/Id/nmc-number  |

## Resource Population Requirements and Guidance ##

The following requirements and resource population guidance should be followed in addition to the requirements and guidance outlined in the data item mapping above and in the [Event Header](https://developer.nhs.uk/apis/ems-beta/explore_event_header_information.html) requirements page.

#### _list profiles used (and sustituted L3 variants)_ ####

## Discharge Details Example ##

#### _placeholder using additional demographics_ ####

<script src="https://gist.github.com/IOPS-DEV/646f784bcb1db6e7aa3d924aaaf423d1.js"></script>


## Profile Change Mappings for Discharge Details ##

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

<hr/>
<hr/>

## Old Stuff ##

#### retain until new content completed then remove ####



The following FHIR profiles are used to form the Discharge Details Event Message Bundle:

- [DCH-Bundle-1](https://fhir.nhs.uk/STU3/StructureDefinition/DCH-Bundle-1)
- [DCH-MessageHeader-1](https://fhir.nhs.uk/STU3/StructureDefinition/DCH-MessageHeader-1) - where the coding and display for the event element is fixed to 'CH009 - Discharge Details'
- [CareConnect-Organization-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Organization-1)
- [DCH-HealthcareService-1](https://fhir.nhs.uk/STU3/StructureDefinition/DCH-HealthcareService-1)
- [CareConnect-DCH-Patient-1](https://fhir.nhs.uk/STU3/StructureDefinition/CareConnect-DCH-Patient-1)
- [CareConnect-DCH-Encounter-1](https://fhir.nhs.uk/STU3/StructureDefinition/CareConnect-DCH-Encounter-1)
- [CareConnect-Location-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Location-1)
- [CareConnect-DCH-Practitioner-1](https://fhir.nhs.uk/STU3/StructureDefinition/CareConnect-DCH-Practitioner-1)
- [CareConnect-DCH-PractitionerRole-1](https://fhir.nhs.uk/STU3/StructureDefinition/CareConnect-DCH-PractitionerRole-1) 


### Discharge Details Event data item mapping to FHIR profiles ###

The Child Health Event data items are fulfilled by elements within the FHIR resources listed below:

| DCH Data Item                     | FHIR resource element                                            | Mandatory/Required/Optional | Note                                                                                  |
|-----------------------------------|------------------------------------------------------------------|-----------------------------|---------------------------------------------------------------------------------------|
| Date and Time of Discharge        | CareConnect-DCH-Encounter-1.period.end                           | Required                    |                                                                                       |
| ODS/ORD Site Code                 | CareConnect-Location-1.identifier (ODS Site Code)                | Required                    |                                                                                       |
| Discharging Clinician             | CareConnect-DCH-Practitioner-1                                   | Required                    |                                                                                       |
| Discharging Clinician Identifier  | CareConnect-DCH-Practitioner-1.identifier.value                  | Required                    |                 |
| Identifier Issuer                 | CareConnect-DCH-Practitioner-1.identifier.system                 | Required                    | *               |
| Discharging Speciality/Department | DCH-HealthcareService-1.specialty                                | Required                    |                                                                                       |
| Discharge method                  | CareConnect-DCH-Encounter-1.hospitalization.dischargeMethod      | Required                    |                                                                                       |
| Discharge destination             | CareConnect-DCH-Encounter-1.hospitalization.dischargeDisposition | Required                    |                                                                                       |
| Discharge address                 | CareConnect-Location-1.address                                   | Required                    | Discharge address required if it is _not_ to the usual place of residence.                                |

**\*** The Professional Registration Body identifier, e.g. the discharging Clinician's GMC number, is recorded as **Responsible Clinician Identifier** in element **CareConnect-DCH-Practitioner-1.identifier.value**.  
The identifier for the issuing Professional Registration Body is recorded as **Identifier Issuer** in element **CareConnect-DCH-Practitioner-1.identifier.system** as follows:

| Issuing Professional Registration Body         | Identifier                                |
|------------------------------------------------|-------------------------------------------|
| General Dental Council Identifier              | http://fhir.hl7.org.uk/Id/gdc-number  |
| General Medical Council Identifier             | http://fhir.hl7.org.uk/Id/gmc-number  |
| Health and Care Professions Council Identifier | http://fhir.hl7.org.uk/Id/hcpc-number |
| Nursing and Midwifery Council Identifier       | http://fhir.hl7.org.uk/Id/nmc-number  |

### Reference Linkage Diagram ###

This Linkage diagram defines the required references that SHALL be made between resources within the DCH Event Message bundle. It includes both Header and Payload resources (but omits the DCH-Bundle-1 wrapper).

<img src="images/explore/DischargeDetails.png">

### Examples ###

<script src="https://gist.github.com/IOPS-DEV/91108b7dcc8b5993b69be15cf736d688.js"></script>

<script src="https://gist.github.com/IOPS-DEV/637681930c2c97ac31d963c5f5a3f1d7.js"></script>

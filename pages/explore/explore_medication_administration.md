---
title: Medication Administration Event Message Bundle
keywords:  messaging, bundles
tags: [fhir,messaging]
sidebar: foundations_sidebar
permalink: explore_medication_administration.html
summary: "The FHIR profiles used for the Medication Administration Event Message Bundle"
---

## FHIR Profiles ##

The following FHIR profiles are used to form the Medication Administration Event Message Bundle:

- [Bundle](http://hl7.org/fhir/STU3/StructureDefinition/Bundle)
- [Event-MessageHeader-1](https://fhir.nhs.uk/STU3/StructureDefinition/Event-MessageHeader-1) - where the coding and display elements for the ‘event’ type are fixed to "​medication-administration-1 | Medication Administration"
- [CareConnect-Organization-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Organization-1)
- [CareConnect-HealthcareService-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-HealthcareService-1)
- [CareConnect-Patient-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Patient-1)
- [CareConnect-Encounter-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Encounter-1)
- [CareConnect-Location-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Location-1)
- [CareConnect-Practitioner-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Practitioner-1)
- [CareConnect-PractitionerRole-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-PractitionerRole-1)
- [CareConnect-Medication-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Medication-1)
- [CareConnect-MedicationAdministration-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-MedicationAdministration-1)

## Bundle Structure

Specifies referencing within the Event Message Bundle.


<div style="text-align:center; margin-bottom:20px" >
	<a href="images/explore/dch-medicationadministration.png" target="_blank"><img src="images/explore/dch-medicationadministration.png"></a><br/>
	Medication Administration <a href="images/explore/dch-medicationadministration.png" target="_blank">(open in new TAB)</a>
</div>

## Medication Administration Event data item mapping to FHIR profiles ##

This Mapping table defines the FHIR elements that SHALL be used to encode the Healthy Child Event Specification data items for each DCH Event Message payload.  
Some common data item mappings, such as patient, publisher or Date/Time of event information, are defined within the [Header mapping table](explore_event_header_design.html) and SHALL be considered in parallel with the payload mapping.

The Child Health Event data items are fulfilled by elements within the FHIR resources listed below:

<table>
<tr><th>DCH Data Item</th><th>FHIR Resource element</th><th>Mandatory/<br/>Required/<br/>Optional</th><th>Notes</th></tr>
<tr><td>Date/Time of Administation</td><td>CareConnect-MedicationAdministration-1.effectiveTimeDateTime</td><td>Mandatory</td><td>The date the medication administration took place. Format is YYYY-MM-DD”T”HH:MM:SS.</td></tr>
<tr><td>ODS/ORD Site Code</td><td>CareConnect--Location.identifier (ODS Site Code)</td><td>Required</td><td></td></tr>
<tr><td>Performing Professional</td><td>CareConnect-Practitioner-1.name</td><td>Required</td><td></td></tr>
<tr><td>SDS Job Role Name</td><td>CareConnect-PractitionerRole-1.code (SDS Job Role Name)</td><td>Required</td><td></td></tr>
<tr><td>Medication Name</td><td>CareConnect-Medication-1.code</td><td>Required</td><td>May be generic name or brand name (as appropriate). Free text field to be used if no coded text available.</td></tr>
<tr><td>Dose Amount Description</td><td>CareConnect-MedicationAdministration-1.dosage.text</td><td>Optional</td><td></td></tr>
<tr><td>Route</td><td>CareConnect-MedicationAdministration-1.dosage.route</td><td>Optional</td><td></td></tr>
<tr><td>Site</td><td>CareConnect-MedicationAdministration-1.dosage.site</td><td>Optional</td><td></td></tr>
<tr><td>Status</td><td>CareConnect-MedicationAdministration-1.status</td><td>Optional</td><td>The nature of any change made to the medication.  MUST be marked as COMPLETED once administered.</td></tr>
</table>

## Resource Population Requirements and Guidance ##

The following requirements and resource population guidance should be followed in addition to the requirements and guidance outlined in the data item mapping above and in the [Event Header](https://developer.nhs.uk/apis/ems-beta/explore_event_header_information.html) requirements page.

#### _list profiles used (and sustituted L3 variants)_ ####

## Medication Administration Example ##

<script src="https://gist.github.com/IOPS-DEV/1c201750216039f9a3979b48e93c832d.js"></script>


## Profile Change Mappings for Medication Administration ##

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
| CareConnect-DCH-Medication-1 | CareConnect-Medication-1 |
| DCH-MedicationAdministration-1 | CareConnect-MedicationAdministration-1 |

<hr/>
<hr/>

## Old Stuff ##

#### retain until new content completed then remove ####



The following FHIR profiles are used to form the Medication Administration Event Message Bundle:

- [DCH-Bundle-1](https://fhir.nhs.uk/STU3/StructureDefinition/DCH-Bundle-1)
- [DCH-MessageHeader-1](https://fhir.nhs.uk/STU3/StructureDefinition/DCH-MessageHeader-1) - where the coding and display elements for the 'event' type are fixed to 'CH036 - Medication Administration'
- [CareConnect-Organization-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Organization-1)
- [DCH-HealthcareService-1](https://fhir.nhs.uk/STU3/StructureDefinition/DCH-HealthcareService-1)
- [CareConnect-DCH-Patient-1](https://fhir.nhs.uk/STU3/StructureDefinition/CareConnect-DCH-Patient-1)
- [CareConnect-DCH-Encounter-1](https://fhir.nhs.uk/STU3/StructureDefinition/CareConnect-DCH-Encounter-1)
- [CareConnect-Location-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Location-1)
- [CareConnect-DCH-Practitioner-1](https://fhir.nhs.uk/STU3/StructureDefinition/CareConnect-DCH-Practitioner-1)
- [CareConnect-DCH-PractitionerRole-1](https://fhir.nhs.uk/STU3/StructureDefinition/CareConnect-DCH-PractitionerRole-1)
- [CareConnect-DCH-Medication-1](https://fhir.nhs.uk/STU3/StructureDefinition/CareConnect-DCH-Medication-1)
- [DCH-MedicationAdministration-1](https://fhir.nhs.uk/STU3/StructureDefinition/DCH-MedicationAdministration-1)


### Medication Administration Event data item mapping to FHIR profiles ###

This Mapping table defines the FHIR elements that SHALL be used to encode the Healthy Child Event Specification data items for each DCH Event Message payload.
Some common data item mappings, such as patient, publisher or Date/Time of event information, are defined within the [Header mapping table](explore_event_header_design.html) and SHALL be considered in parallel with the payload mapping.

The Child Health Event data items are fulfilled by elements within the FHIR resources listed below:

<table>
<tr><th>DCH Data Item</th><th>FHIR Resource element</th><th>Mandatory/<br/>Required/<br/>Optional</th><th>Notes</th></tr>
<tr><td>Date/Time of Administation</td><td>DCH-MedicationAdministration-1.effectiveTimeDateTime</td><td>Mandatory</td><td>The date the medication administration took place. Format is YYYY-MM-DD”T”HH:MM:SS.</td></tr>
<tr><td>ODS/ORD Site Code</td><td>CareConnect-DCH-Location.identifier (ODS Site Code)</td><td>Required</td><td></td></tr>
<tr><td>Performing Professional</td><td>CareConnect-DCH-Practitioner-1.name</td><td>Required</td><td></td></tr>
<tr><td>SDS Job Role Name</td><td>CareConnect-DCH-PractitionerRole-1.code (SDS Job Role Name)</td><td>Required</td><td></td></tr>
<tr><td>Medication Name</td><td>CareConnect-DCH-Medication-1.code</td><td>Required</td><td>May be generic name or brand name (as appropriate). Free text field to be used if no coded text available.</td></tr>
<tr><td>Dose Amount Description</td><td>DCH-MedicationAdministration-1.dosage.text</td><td>Optional</td><td></td></tr>
<tr><td>Route</td><td>DCH-MedicationAdministration-1.dosage.route</td><td>Optional</td><td></td></tr>
<tr><td>Site</td><td>DCH-MedicationAdministration-1.dosage.site</td><td>Optional</td><td></td></tr>
<tr><td>Status</td><td>DCH-MedicationAdministration-1.status</td><td>Optional</td><td>The nature of any change made to the medication.  MUST be marked as COMPLETED once administered.</td></tr>
</table>

### Reference Linkage Diagram ###

This Linkage diagram defines the required references that SHALL be made between resources within the DCH Event Message bundle. It includes both Header and Payload resources (but omits the DCH-Bundle-1 wrapper).

<img src="images/explore/MedicationAdministration.png">

### Medication Administation Event Bundle XML Example ###

<script src="https://gist.github.com/IOPS-DEV/7173c87012956dc65fa89ece00ba9c8f.js"></script>

### Medication Administation Event Bundle JSON Example ###

<script src="https://gist.github.com/IOPS-DEV/645ebb3000f77f479952dca00414a788.js"></script>


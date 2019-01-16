---
title: Vaccinations Event Message Bundle
keywords:  messaging, bundles
tags: [fhir,messaging]
sidebar: foundations_sidebar
permalink: explore_vaccination_administration.html
summary: "The FHIR profiles used for the Vaccinations Event Message Bundle"
---

The following FHIR profiles are used to form the Vaccinations Event Message Bundle:

- [DCH-Bundle-1](https://fhir.nhs.uk/STU3/StructureDefinition/DCH-Bundle-1)
- [DCH-MessageHeader-1](https://fhir.nhs.uk/STU3/StructureDefinition/DCH-MessageHeader-1) - where the coding and display for the event element is fixed to 'CH015 - Vaccinations'
- [CareConnect-Organization-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Organization-1)
- [DCH-HealthcareService-1](https://fhir.nhs.uk/STU3/StructureDefinition/DCH-HealthcareService-1)
- [CareConnect-DCH-Patient-1](https://fhir.nhs.uk/STU3/StructureDefinition/CareConnect-DCH-Patient-1)
- [CareConnect-DCH-Encounter-1](https://fhir.nhs.uk/STU3/StructureDefinition/CareConnect-DCH-Encounter-1)
- [CareConnect-Location-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Location-1)
- [CareConnect-DCH-Practitioner-1](https://fhir.nhs.uk/STU3/StructureDefinition/CareConnect-DCH-Practitioner-1)
- [CareConnect-DCH-PractitionerRole-1](https://fhir.nhs.uk/STU3/StructureDefinition/CareConnect-DCH-PractitionerRole-1)
- [CareConnect-DCH-Immunization-1](https://fhir.nhs.uk/STU3/StructureDefinition/CareConnect-DCH-Immunization-1)
<!--[CareConnect-DCH-Composition-1](https://fhir.nhs.uk/STU3/StructureDefinition/CareConnect-DCH-Composition-1)-->
<!--[CareConnect-DCH-AllergyIntolerance-1](https://fhir.nhs.uk/STU3/StructureDefinition/CareConnect-DCH-AllergyIntolerance-1)-->

### Vaccinations Event data item mapping to FHIR profiles ###

This Mapping table defines the FHIR elements that SHALL be used to encode the Healthy Child Event Specification data items for each DCH Event Message payload.
Some common data item mappings, such as patient, publisher or Date/Time of event information, are defined within the [Header mapping table](../explore_event_header_design.html) and SHALL be considered in parallel with the payload mapping.

The Child Health Event data items are fulfilled by elements within the FHIR resources listed below:

| DCH Data Item               | FHIR resource element                                               | Mandatory/<br/>/Required<br/>/Optional | Note                    |
|-----------------------------|---------------------------------------------------------------------|-----------------------------|-----------------------------|
| Date/Time                   | CareConnect-DCH-Encounter-1.period.start                            | Mandatory                   | The date on which the vaccination intervention was carried out or was meant to be administered or was reported to a health professional.  Format is YYYY-MM-DD”T”HH:MM:SS                    |
| ODS/ORD Site code           | CareConnect-Location-1.identifier (ODS Site Code)                   | Required                    |                         |
| Performing Professional     | CareConnect-DCH-Practitioner-1.name                                 | Required                    |                         |
| SDS Job Role Name           | CareConnect-DCH-PractitionerRole-1.code (SDS Job Role Name)         | Required                    |                         |
| Reported Date            	  | CareConnect-DCH-Immunization-1.date                                 | Required                    | The date or partial date that the vaccine was administered, or reported vaccination was given in the opinion of the child and/or parent carer                        | 
| Primary Source              | CareConnect-DCH-Immunization-1.primarySource                        | Mandatory                   | Boolean (FALSE (if reported)/True                        |
| Report Origin               | CareConnect-DCH-Immunization-1.reportOrigin                         | Required                    |                         |
| Vaccination Procedure       | CareConnect-DCH-Immunization-1.extension:vaccinationProcedure       | Required                    | Free text field to be used if no coded text available using vaccinationProcedure.coding.text                        |
| Vaccination Situation (Not Given Outcome)       | CareConnect-DCH-Immunization-1.explanation.reasonNotGiven | Required                    |                         |
| Not Given flag              | CareConnect-DCH-Immunization-1.notGiven                             | Mandatory                   | Boolean (FALSE (given or reported as given)/TRUE (not given)                 |
| Dose sequence               | CareConnect-DCH-Immunization-1.vaccinationProtocol.doseSequence     | Required                    | Note, if the vaccination protocol is not present, then the dose sequence is not present either.|
| Vaccine Product             | CareConnect-DCH-Immunization-1.vaccineCode.coding.code              | Required                    | DM+D [SNOMED UK drug extension](https://www.nhsbsa.nhs.uk/pharmacies-gp-practices-and-appliance-contractors/dictionary-medicines-and-devices-dmd)                         |
| Vaccine Manufacturer        | CareConnect-DCH-Immunization-1.manufacturer                         | Required                    |                         |
| Batch Number                | CareConnect-DCH-Immunization-1.lotNumber                            | Optional                    | Derived from FMD code   |
| Site of Vaccination         | CareConnect-DCH-Immunization-1.site                                 | Required                    |                         |
| Route of Vaccination        | CareConnect-DCH-Immunization-1.route                                | Required                    |                         |
| Dose Amount                 | CareConnect-DCH-Immunization-1.doseQuantity                         | Optional                    |                         |
| Indication                  | CareConnect-DCH-Immunization-1.explanation.reason                   | Optional                    | Free text field to be used if no coded text available using reason.coding.text    |


<!--| Reported                    | CareConnect-DCH-Immunization-1.primarySource                        | Required                    |                         |
| Information and Advice Given                    | CareConnect-DCH-Composition-1                   | Required                    |                         |
| Allergies and Adverse Reactions                    | CareConnect-DCH-AllergyIntolerance-1         | Required                    |                         |
| Name of Immunisation        | CareConnect-DCH-Immunization-1.vaccinationProcedure                 | Mandatory                   |                         |
| Outcome Status              | CareConnect-DCH-Immunization-1.explanation                          | Optional                    |                         |-->



### Reference Linkage Diagram ###

This Linkage diagram defines the required references that SHALL be made between resources within the DCH Event Message bundle. It includes both Header and Payload resources (but omits the DCH-Bundle-1 wrapper).

<img src="images/explore/Vaccinations.png">

### Vaccinations Event Bundle XML Example ###

<script src="https://gist.github.com/IOPS-DEV/bcd2f02a8a37ffd47d07996278dc9356.js"></script>

###  Vaccinations Event Bundle JSON Example ###

<script src="https://gist.github.com/IOPS-DEV/96e14bdaad2c7179be3ec7fcba256336.js"></script>
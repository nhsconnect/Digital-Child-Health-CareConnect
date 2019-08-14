---
title: Educational History Event Message Bundle
keywords:  messaging, bundles
tags: [fhir,messaging]
sidebar: foundations_sidebar
permalink: explore_educational_history.html
summary: "The FHIR profiles used for the Educational History Event Message Bundle"
---

## FHIR Profiles ##

The following FHIR profiles are used to form the Educational History Event Message Bundle:

- [Bundle](http://hl7.org/fhir/STU3/StructureDefinition/Bundle)
- [Event-MessageHeader-1](https://fhir.nhs.uk/STU3/StructureDefinition/Event-MessageHeader-1) - where the coding and display for the event element is fixed to ‘educational-history-1 \| Educational History’
- [CareConnect-Organization-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Organization-1)
- [CareConnect-HealthcareService-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-HealthcareService-1)
- [CareConnect-Patient-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Patient-1)
- [CareConnect-Encounter-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Encounter-1)
- [CareConnect-Location-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Location-1)
- [CareConnect-QuestionnaireResponse-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-QuestionnaireResponse-1)
- [CareConnect-Communication-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Communication-1)
- [CareConnect-Practitioner-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Practitioner-1)
or
- [CareConnect-RelatedPerson-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-RelatedPerson-1)

## Bundle Structure

Specifies referencing within the Event Message Bundle.

<div style="text-align:center; margin-bottom:20px" >
	<a href="images/explore/dch-educationalhistory.png" target="_blank"><img src="images/explore/dch-educationalhistory.png"></a><br/>
	Educational History <a href="images/explore/dch-educationalhistory.png" target="_blank">(open in new TAB)</a>
</div>

## Educational History Event data item mapping to FHIR profiles ##

This Mapping table defines the FHIR elements that SHALL be used to encode the Healthy Child Event Specification data items for each DCH Event Message payload.  
Some common data item mappings, such as patient, publisher or Date/Time of event information, are defined within the [Header mapping table](explore_event_header_design.html) and SHALL be considered in parallel with the payload mapping.

The Child Health Event data items are fulfilled by elements within the FHIR resources listed below:

| DCH Data Item                                | FHIR Resource element                                                             | Mandatory/Required/Optional |             |
|----------------------------------------------|-----------------------------------------------------------------------------------|-----------------------------|-------------|
| Date/Time                                    | CareConnect-Encounter-1.period.start                                          | Mandatory                   |             |
| Educational Establishment                    | CareConnect-QuestionnaireResponse-1.item.educationalEstablishment      | Mandatory                   |             |
| Educational Establishment Name               | CareConnect-Organization-1.name                                                   | Mandatory                   |             |
| Educational Establishment ODS/ORD Site Code  | CareConnect-Organization-1.identifier                                             | Mandatory                   |             |
| Type of Educational Establishment  | CareConnect-QuestionnaireResponse-1.item.educationalEstablishmentType            | Mandatory                   |             |
| Year From                          | CareConnect-QuestionnaireResponse-1.item.educationalEstablishmentStart           | Mandatory                   | Only the Year part of the date is required  |
| Year To                            | CareConnect-QuestionnaireResponse-1.item.educationalEstablishmentEnd             | Mandatory                   | Only the Year part of the date is required  |
| Educational Assessment             | CareConnect-QuestionnaireResponse-1.item.educationalAssessmentOutcome            | Required                    |             |
| Type of Special Educational Need   | CareConnect-QuestionnaireResponse-1.item.specialEducationalNeedType              | Required                    |             |
| Special Educational Need Comment   | CareConnect-Communication-1                                                     | Optional                    |             |

## Resource Population Requirements and Guidance ##

The following requirements and resource population guidance should be followed in addition to the requirements and guidance outlined in the data item mapping above and in the [Event Header](https://developer.nhs.uk/apis/ems-beta/explore_event_header_information.html) requirements page.

#### _list profiles used (and sustituted L3 variants)_ ####

## Educational History Example ##

<script src="https://gist.github.com/IOPS-DEV/ccd736e8932c5106393999aebdd720e4.js"></script>

## Profile Change Mappings for Educational History ##

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
| DCH-EducationalHistory-QuestionnaireResponse-1 | CareConnect-QuestionnaireResponse-1 |
| DCH-ProfessionalComment-Communication-1 | CareConnect-Communication-1 |
| CareConnect-DCH-Practitioner-1 | CareConnect-Practitioner-1 |
| DCH-RelatedPerson-1 | CareConnect-RelatedPerson-1 |

<hr/>
<hr/>

## Old Stuff ##

#### retain until new content completed then remove ####


The following FHIR profiles are used to form the Educational History Event Message Bundle:

- [DCH-Bundle-1](https://fhir.nhs.uk/STU3/StructureDefinition/DCH-Bundle-1)
- [DCH-MessageHeader-1](https://fhir.nhs.uk/STU3/StructureDefinition/DCH-MessageHeader-1) - where the coding and display for the event element is fixed to 'CH032 - Educational History'
- [CareConnect-Organization-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Organization-1)
- [DCH-HealthcareService-1](https://fhir.nhs.uk/STU3/StructureDefinition/DCH-HealthcareService-1)
- [CareConnect-DCH-Patient-1](https://fhir.nhs.uk/STU3/StructureDefinition/CareConnect-DCH-Patient-1)
- [CareConnect-DCH-Encounter-1](https://fhir.nhs.uk/STU3/StructureDefinition/CareConnect-DCH-Encounter-1)
- [CareConnect-Location-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Location-1)
- [DCH-EducationalHistory-QuestionnaireResponse-1](https://fhir.nhs.uk/STU3/StructureDefinition/DCH-EducationalHistory-QuestionnaireResponse-1)
- [DCH-ProfessionalComment-Communication-1](https://fhir.nhs.uk/STU3/StructureDefinition/DCH-ProfessionalComment-Communication-1)
- [CareConnect-DCH-Practitioner-1](https://fhir.nhs.uk/STU3/StructureDefinition/CareConnect-DCH-Practitioner-1) or  
- [DCH-RelatedPerson-1](https://fhir.nhs.uk/STU3/StructureDefinition/DCH-RelatedPerson-1)

### Educational History Event data item mapping to FHIR profiles ###

This Mapping table defines the FHIR elements that SHALL be used to encode the Healthy Child Event Specification data items for each DCH Event Message payload.  
Some common data item mappings, such as patient, publisher or Date/Time of event information, are defined within the [Header mapping table](explore_event_header_design.html) and SHALL be considered in parallel with the payload mapping.

The Child Health Event data items are fulfilled by elements within the FHIR resources listed below:

| DCH Data Item                                | FHIR Resource element                                                             | Mandatory/Required/Optional |             |
|----------------------------------------------|-----------------------------------------------------------------------------------|-----------------------------|-------------|
| Date/Time                                    | CareConnect-DCH-Encounter-1.period.start                                          | Mandatory                   |             |
| Educational Establishment                    | DCH-EducationalHistory-QuestionnaireResponse-1.item.educationalEstablishment      | Mandatory                   |             |
| Educational Establishment Name               | CareConnect-Organization-1.name                                                   | Mandatory                   |             |
| Educational Establishment ODS/ORD Site Code  | CareConnect-Organization-1.identifier                                             | Mandatory                   |             |
| Type of Educational Establishment  | DCH-EducationalHistory-QuestionnaireResponse-1.item.educationalEstablishmentType            | Mandatory                   |             |
| Year From                          | DCH-EducationalHistory-QuestionnaireResponse-1.item.educationalEstablishmentStart           | Mandatory                   | Only the Year part of the date is required  |
| Year To                            | DCH-EducationalHistory-QuestionnaireResponse-1.item.educationalEstablishmentEnd             | Mandatory                   | Only the Year part of the date is required  |
| Educational Assessment             | DCH-EducationalHistory-QuestionnaireResponse-1.item.educationalAssessmentOutcome            | Required                    |             |
| Type of Special Educational Need   | DCH-EducationalHistory-QuestionnaireResponse-1.item.specialEducationalNeedType              | Required                    |             |
| Special Educational Need Comment   | DCH-ProfessionalComment-Communication-1                                                     | Optional                    |             |


### Reference Linkage Diagram ###

This Linkage diagram defines the required references that SHALL be made between resources within the DCH Event Message bundle. It includes both Header and Payload resources (but omits the DCH-Bundle-1 wrapper).

<img src="images/explore/EducationalHistory.png">

### Examples ###

<script src="https://gist.github.com/IOPS-DEV/cbb2372807a6c68f7d82f361dd4b1c9b.js"></script>

<script src="https://gist.github.com/IOPS-DEV/66fffa8c4b5804ec8a3ad46511799528.js"></script>
---
title: Early Years Progress Event Message Bundle
keywords:  messaging, bundles
tags: [fhir,messaging]
sidebar: foundations_sidebar
permalink: explore_early_years_progress.html
summary: "The FHIR profiles used for the Early Years Progress Event Message Bundle"
---

## FHIR Profiles ##

The following FHIR profiles are used to form the Early Years Progress Event Message Bundle:

- [Bundle](http://hl7.org/fhir/STU3/StructureDefinition/Bundle)
- [Event-MessageHeader-1](https://fhir.nhs.uk/STU3/StructureDefinition/Event-MessageHeader-1) - where the coding and display for the event element is fixed to ‘early-years-progress-1 \| Early Years Progress’
- [CareConnect-Organization-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Organization-1)
- [CareConnect-HealthcareService-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-HealthcareService-1)
- [CareConnect-Patient-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Patient-1)
- [CareConnect-Encounter-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Encounter-1)
- [CareConnect-Location-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Location-1)
- [CareConnect-Practitioner-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Practitioner-1)
- [CareConnect-PractitionerRole-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-PractitionerRole-1)
- [CareConnect-QuestionnaireResponse-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-QuestionnaireResponse-1)

## Bundle Structure

Specifies referencing within the Event Message Bundle.


<div style="text-align:center; margin-bottom:20px" >
	<a href="images/explore/dch-earlyyearsprogress.png" target="_blank"><img src="images/explore/dch-earlyyearsprogress.png"></a><br/>
	Early Years Progress <a href="images/explore/dch-earlyyearsprogress.png" target="_blank">(open in new TAB)</a>
</div>

## Early Years Progress Event data item mapping to FHIR profiles ##

This Mapping table defines the FHIR elements that SHALL be used to encode the Healthy Child Event Specification data items for each DCH Event Message payload.  
Some common data item mappings, such as patient, publisher or Date/Time of event information, are defined within the [Header mapping table](explore_event_header_design.html) and SHALL be considered in parallel with the payload mapping.

The Child Health Event data items are fulfilled by elements within the FHIR resources listed below:

| DCH Data Item                              | FHIR Resource element                                               | Mandatory/Required/Optional |
|--------------------------------------------|---------------------------------------------------------------------|-----------------------------|
| Date/Time                                  | CareConnect-Encounter-1.period.start                            | Mandatory                   |
| Site Code                                  | CareConnect-Location-1.identifier                                   | Required                    |
| Performing Professional                    | CareConnect-Practitioner.name                                   | Required                    |
| Professional Type                          | CareConnect-PractitionerRole-1.code (SDS Job Role Name)         | Required                    |
| Parental Consent                           | CareConnect-QuestionnaireResponse-1.parentalConsent                        | Required                    |
| Communication and Language                 | CareConnect-QuestionnaireResponse-1.communicationAndLanguage                    | Required                    |
| Physical Development                       | CareConnect-QuestionnaireResponse-1.physicalDevelopment                    | Required                    |
| Personal, Social and Emotional Development | CareConnect-QuestionnaireResponse-1.personalSocialEmotionalDevelopment                    | Required                    |
| Any Areas of Concern                       | CareConnect-QuestionnaireResponse-1.areasOfConcern                    | Required                    |
| Type of Support Requested/Provided         | CareConnect-QuestionnaireResponse-1.supportedRequestedOrProvided                    | Required                    |

## Resource Population Requirements and Guidance ##

The following requirements and resource population guidance should be followed in addition to the requirements and guidance outlined in the data item mapping above and in the [Event Header](https://developer.nhs.uk/apis/ems-beta/explore_event_header_information.html) requirements page.

#### _list profiles used (and sustituted L3 variants)_ ####

## Early Years Progress Example ##

#### _placeholder using additional demographics_ ####

<script src="https://gist.github.com/IOPS-DEV/646f784bcb1db6e7aa3d924aaaf423d1.js"></script>


## Profile Change Mappings for Early Years Progress ##

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
| DCH-EarlyYearsProgress-QuestionnaireResponse-1 | CareConnect-QuestionnaireResponse-1 |

<hr/>
<hr/>

## Old Stuff ##

#### retain until new content completed then remove ####



The following FHIR profiles are used to form the Early Years Progress Event Message Bundle:

- [DCH-Bundle-1](https://fhir.nhs.uk/STU3/StructureDefinition/DCH-Bundle-1)
- [DCH-MessageHeader-1](https://fhir.nhs.uk/STU3/StructureDefinition/DCH-MessageHeader-1) - where the coding and display for the event element is fixed to 'CH010 - Early Years Progress'
- [CareConnect-Organization-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Organization-1)
- [DCH-HealthcareService-1](https://fhir.nhs.uk/STU3/StructureDefinition/DCH-HealthcareService-1)
- [CareConnect-DCH-Patient-1](https://fhir.nhs.uk/STU3/StructureDefinition/CareConnect-DCH-Patient-1)
- [CareConnect-DCH-Encounter-1](https://fhir.nhs.uk/STU3/StructureDefinition/CareConnect-DCH-Encounter-1)
- [CareConnect-Location-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Location-1)
- [CareConnect-DCH-Practitioner-1](https://fhir.nhs.uk/STU3/StructureDefinition/CareConnect-DCH-Practitioner-1)
- [CareConnect-DCH-PractitionerRole-1](https://fhir.nhs.uk/STU3/StructureDefinition/CareConnect-DCH-PractitionerRole-1)
- [DCH-EarlyYearsProgress-QuestionnaireResponse-1](https://fhir.nhs.uk/STU3/StructureDefinition/DCH-EarlyYearsProgress-QuestionnaireResponse-1)

### Early Years Progress Event data item mapping to FHIR profiles ###

This Mapping table defines the FHIR elements that SHALL be used to encode the Healthy Child Event Specification data items for each DCH Event Message payload.  
Some common data item mappings, such as patient, publisher or Date/Time of event information, are defined within the [Header mapping table](explore_event_header_design.html) and SHALL be considered in parallel with the payload mapping.

The Child Health Event data items are fulfilled by elements within the FHIR resources listed below:

| DCH Data Item                              | FHIR Resource element                                               | Mandatory/Required/Optional |
|--------------------------------------------|---------------------------------------------------------------------|-----------------------------|
| Date/Time                                  | CareConnect-DCH-Encounter-1.period.start                            | Mandatory                   |
| Site Code                                  | CareConnect-Location-1.identifier                                   | Required                    |
| Performing Professional                    | CareConnect-DCH-Practitioner.name                                   | Required                    |
| Professional Type                          | CareConnect-DCH-PractitionerRole-1.code (SDS Job Role Name)         | Required                    |
| Parental Consent                           | DCH-EarlyYearsProgress-QuestionnaireResponse-1.parentalConsent                        | Required                    |
| Communication and Language                 | DCH-EarlyYearsProgress-QuestionnaireResponse-1.communicationAndLanguage                    | Required                    |
| Physical Development                       | DCH-EarlyYearsProgress-QuestionnaireResponse-1.physicalDevelopment                    | Required                    |
| Personal, Social and Emotional Development | DCH-EarlyYearsProgress-QuestionnaireResponse-1.personalSocialEmotionalDevelopment                    | Required                    |
| Any Areas of Concern                       | DCH-EarlyYearsProgress-QuestionnaireResponse-1.areasOfConcern                    | Required                    |
| Type of Support Requested/Provided         | DCH-EarlyYearsProgress-QuestionnaireResponse-1.supportedRequestedOrProvided                    | Required                    |


### Reference Linkage Diagram ###

This Linkage diagram defines the required references that SHALL be made between resources within the DCH Event Message bundle. It includes both Header and Payload resources (but omits the DCH-Bundle-1 wrapper).

<img src="images/explore/EarlyYearsProgress.png">

### Examples ###

<script src="https://gist.github.com/IOPS-DEV/6ece8304c418ddb441859020cbfed5b3.js"></script>

<script src="https://gist.github.com/IOPS-DEV/747b388edfb6235eae358a9bed994dca.js"></script>